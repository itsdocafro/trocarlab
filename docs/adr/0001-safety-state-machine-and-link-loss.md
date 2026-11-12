# ADR-0001: Safety state machine and hold-in-position on console link loss

- **Status:** Proposed
- **Date:** 2026-11-04
- **Author:** Maxime JOBERT
- **Related requirements:** ES-005, ES-007, ES-012, ES-013, ES-014, ES-017, EF-302, EF-506
- **Related risks:** RP-005, RP-011, RP-012

## Context

The specification (v1.15, frozen) leaves several behaviours undefined. They surfaced while drawing the low-fidelity console wireframes:

1. **ES-005** stops the arm when "no command **or** no heartbeat" arrives for 500 ms, but does not say which state the system enters afterwards, nor how it leaves it.
2. **ES-005** mixes two different conditions. In the terminal, teleoperation is step by step (EF-302): receiving no command for one second is normal, not a failure.
3. **ES-007** says the emergency stop is lifted only by an explicit action, but not what happens after it is lifted.
4. **ES-017** lists four "safety states" (ready, command refused, fault, emergency stop). A refused command is an event, not a state: the arm stays ready. The console brief, in turn, asks for nine screen states that are not all safety states.
5. **ES-008 / ES-019** refuse to start on an invalid configuration, but the specification does not say what the user sees.
6. **EF-506** lists four startup steps, while ES-012 (since v1.12) has five: the straight-line insertion is missing.

## Decision drivers

- Fault is reserved for situations where the robot itself can no longer be trusted (ES-002, ES-011, ES-014). Only then is a full retraction (ES-013) justified.
- When the cause is external and the robot is healthy, the safest action is to stop and stay still: every movement, including a retraction, is a new opportunity for error.
- Nothing must ever restart on its own: a stale command must never be executed without the user's intent.
- The state machine must stay minimal, so it can be tested to 100 % branch coverage (ENF-010).

## Options considered

| Option | Behaviour on link loss | Rejected because |
| --- | --- | --- |
| A. Fault | Arm stops, fault, rearm retracts the instrument and restarts the startup sequence | Disproportionate: every network glitch forces a full retraction. Less safe: the retraction is itself a movement |
| B. Automatic resume | Arm stops, restarts by itself when the link returns | May execute a stale command without user intent |
| **C. Hold in position** | Arm stops and stays still; the user resumes explicitly after checks | **Chosen** |

## Decision

### 1. Safety states

The safety state machine has six states. Only these states change which rules apply.

| State | Meaning | Teleoperation |
| --- | --- | --- |
| `Stopped` | Initial state; also the state after a refused startup. Instrument outside the body | Disabled |
| `Startup` | Startup sequence of ES-012 in progress (also used after a rearm) | Disabled |
| `Ready` | All checks passed | Enabled |
| `Held` | Console heartbeat lost; arm held in position | Disabled |
| `Fault` | The robot itself can no longer be trusted | Disabled |
| `EmergencyStop` | Operator stop; has priority over everything (ES-007) | Disabled |

### 2. Transitions

| From | Event | To |
| --- | --- | --- |
| `Stopped` | Start requested | `Startup` |
| `Startup` | Check fails **before** insertion (configuration, MoveIt, controller switch) | `Stopped`, with the cause |
| `Startup` | Check fails **after** insertion started | `Fault` |
| `Startup` | All steps pass, RCM deviation < 1 mm | `Ready` |
| `Ready` | No heartbeat for 500 ms | `Held` |
| `Held` | Resume, with all resume conditions met (§3) | `Ready` |
| `Held` | Resume, with a check failing | `Fault` |
| `Ready`, `Held` | ES-002, ES-011 or ES-014 triggered | `Fault` |
| `Fault` | Rearm: straight-line retraction succeeds | `Startup` |
| `Fault` | Rearm: retraction impossible | `Fault` |
| any | Emergency stop | `EmergencyStop` |
| `EmergencyStop` | Release, with all resume conditions met | `Ready` |
| `EmergencyStop` | Release, with a check failing | `Fault` |

Monitoring does not pause in `Held`: ES-014 (stale arm state) still applies and leads to `Fault`.

### 3. Resume conditions (Held → Ready, EmergencyStop → Ready)

Resume is accepted only if **all** of the following hold:

1. the console connection is back (for `Held`);
2. no teleoperation key is pressed;
3. every command received before or during the interruption has been discarded;
4. the arm state is up to date (ES-014);
5. the RCM deviation is below the 1 mm target (ENF-001), not merely below the 2 mm safety threshold;
6. the whole shaft is outside the forbidden zone and its margin (EF-402).

Conditions 4 to 6 are the same as the last checks of the startup sequence.

### 4. Heartbeat versus absence of commands

- **Loss of heartbeat** (the console stops sending its liveness signal for 500 ms) leads to `Held`.
- **Absence of commands** is not a failure. It is handled by the dead-man behaviour of EF-302: motion stops, the state stays `Ready`. In the terminal, each step stops by itself.

### 5. Displayed states

The console shows display states that refine a safety state without changing its rules. They are defined once, as a single TypeScript type shared with the Figma components.

| Display state | Safety state |
| --- | --- |
| `startup`, `startupFailed` | `Startup`, `Stopped` |
| `ready`, `moving`, `approach`, `refused`, `focusLost` | `Ready` |
| `fault`, `rearming` | `Fault`, then `Startup` |
| `estop` | `EmergencyStop` |
| `connectionLost`, `connectionRestored` | `Held` |

A refused command is shown until the next accepted command or the release of the key, never with a timer: while a key is held towards the zone, a command is refused at every cycle.

## Consequences

**Positive**

- A short network loss no longer forces a full retraction.
- Nothing ever restarts without an explicit user action.
- Each state has a distinct reason to exist; the machine stays small enough to test exhaustively.

**Negative**

- One more state (`Held`) and two more transitions to test.
- The console must send a heartbeat distinct from its commands.

**Tests to add (fault injection, with a simulated clock):**

- heartbeat lost at 500 ms − ε (still `Ready`) and 500 ms + ε (`Held`);
- no command for 2 s in the terminal: no state change;
- Resume refused while a key is pressed;
- a command received during `Held` is never executed after Resume;
- Resume with a deviation above 1 mm leads to `Fault`;
- stale arm state during `Held` leads to `Fault`;
- invalid configuration value: `Stopped`, arm never moved, cause names the parameter.

## Changes to carry into the next revision of the specification

- **ES-005:** trigger on loss of heartbeat only; the arm enters `Held`.
- **New ES-022:** resume conditions (§3).
- **ES-007:** release goes through the resume conditions.
- **ES-012:** a failure before insertion leads to `Stopped` with the cause shown; a failure after insertion leads to `Fault`.
- **ES-017:** list the six safety states; a refused command is an event shown in the `Ready` state.
- **EF-506:** add the straight-line insertion step.
- **RP-005:** add `Held` and the resume conditions to its measures.
- **Section 5.6 (brief):** add the screens `startupFailed`, `rearming` and `connectionRestored`.

## Open questions

- **Emergency stop during startup or rearm:** on release, should the system go to `Fault` if the instrument is partly inserted, and to `Stopped` otherwise?
- **Retry after a refused startup:** a "Retry" button in the console (re-reading the configuration) or a restart of the containers?
- **Heartbeat period:** to be set with the 500 ms timeout in mind, for example 100 ms, after the J1 measurements.
- **Key mapping:** the proposal in the wireframes (W/A/S/D tilt, R/F insert and retract, Q/E roll, Esc emergency stop) is not part of this ADR; it can be confirmed in the teleoperation tutorial.
