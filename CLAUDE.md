# CLAUDE.md

Context and rules for AI agents working in this repository. Each rule comes from
the specification (`docs/quality/specification.md`, in French, frozen at v1.15)
or from a convention already used in this repository. Sources are in brackets.

## Project

TrocarLab is an open-source educational sandbox that simulates a laparoscopic
surgery robot: RCM control, a forbidden zone, teleoperation and a web console,
running on ROS 2 in Docker [§1.1]. It is not a medical device and must never be
used clinically [§1.2, ES-001].

## Language

- Code, identifiers, file names, commit messages and documentation are in
  English. The specification stays in French; tutorials may also get a French
  version [ENF-012].

## Git workflow

- Never work on `main`. Use one branch per issue, prefixed by its type and the
  issue number: `feat/12-rcm-command`, `fix/`, `docs/`, `test/`, `chore/`
  [§9.3, §9.5].
- Pull request titles use Conventional Commits (`feat(rcm): ...`) [§9.3].
  Commit messages use the same format [repository convention] and carry a
  `Co-Authored-By` trailer when AI was used [§9.5].
- Every change goes through a pull request that states how AI was used [§9.5]
  and contains `Closes #<issue>` [repository convention].
- Never merge a pull request (no `gh pr merge`). The maintainer reviews it and
  squash-merges it [§9.3, §9.5].
- No irreversible action (release, tag, deletion) without the maintainer's
  approval [§9.5].

## Specification and ADRs

- Never change the content of a requirement (EF, ENF, ES) or a risk (RP, RJ) in
  the specification without an accepted ADR [repository convention]. New
  decisions go in `docs/adr/`; every change to the specification is recorded in
  its version history [specification status line].
- A change that alters no requirement, such as restoring a lost diagram, goes
  through a normal pull request that says so [repository convention].
- An ADR with status Proposed is not a decision yet: do not apply it
  [repository convention].

## Who writes what [§9.5]

- The maintainer writes these parts; the agent only explains and reviews:
  - the Panda kinematics (tool pose, Jacobian);
  - in `trocarlab_safety`, the shaft/sphere check (EF-402) and the state
    machine (ES-007, ES-012, ES-013);
  - the safety test case specification (`docs/quality/test-cases.md`).
- For a safety requirement, the agent never defines both the code and what
  validates it. It implements from the maintainer's test cases.
- Never reuse code whose origin is unclear. PolygonMeshVirtualFixture has no
  licence: never copy or adapt it [§9.5, §12.3].

## Tests

- Every test declares the requirement it verifies (`RecordProperty` in gtest,
  `record_property` in pytest) [§9.2]. Safety tests are written before the code
  they verify [§9.1].

## Secrets

- Never read `~/.ssh` or any secrets file (`.env`, keys, tokens) [§9.5].

## Design

- Reuse these component names as-is in Figma and in the code: `StatusBanner`,
  `EmergencyStop`, `IndicatorPanel`, `CommandLegend`, `StartupProgress`,
  `Viewport3D`, `DisclaimerBar` [§8.1, `docs/design/README.md`].
