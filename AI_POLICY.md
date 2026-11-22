# AI policy

TrocarLab is built with the help of AI: Claude, including Claude Code in agent
mode. This file publishes the project's AI usage policy for readers and
contributors. The policy itself is defined in the specification,
[section 9.5](docs/quality/specification.md#95-usage-de-lia-agentique)
(in French). If this file and the specification differ, the specification
applies.

## Why this policy exists

AI is used as an accelerator and as a tutor. Its usage rules protect two
things:

- **the independent verification of the safety code**: AI never defines on its
  own both the safety code and what validates it;
- **the maintainer's learning**: the project must not end up working while the
  maintainer cannot explain or rewrite it (project risk
  [RJ-008](docs/quality/specification.md#104-risques-projet-rj-xxx)).

## Who writes what

| Part | Who writes it | The maintainer's role |
| --- | --- | --- |
| Tooling: CI, Dockerfile, configuration, documentation formatting | The AI | Review, understand, let the CI validate |
| ROS 2 nodes, web console, scripts, `trocarlab_safety` (except the two modules written by the maintainer, below), the rest of `trocarlab_rcm_core` | The AI, from the requirements and the maintainer's test cases | Review, understand, then explain each module in its tutorial without looking at the code |
| Panda kinematics (tool tip pose, Jacobian) | The maintainer, with the AI as a tutor (explanations, review) | Write the code and derive the formulas by hand |
| Safety test case specification (`docs/quality/test-cases.md`) | The maintainer, with the AI as a tutor | Write the cases before the code, at the start of each milestone that contains a safety requirement verified by test (J2 to J6); check that the test code matches them |
| In `trocarlab_safety`: the shaft/sphere check (EF-402) and the ready / fault / emergency stop state machine (ES-007, ES-012, ES-013) | The maintainer, with the AI as a tutor (explanations, review) | Write the code: these are the most interesting safety modules to defend in a technical interview, and they give the maintainer C++ practice beyond the kinematics |

## Rules

- **Independent verification**: for a safety requirement, the maintainer
  defines what is correct, through the maintainer's test cases (initial
  situation, action, expected result, identifier linked to the requirement).
  The AI never defines on its own both the code and what validates it.
- **No blind trust**: all code produced with AI goes through a pull request,
  the CI and the maintainer's review, like any other code.
- **Mandatory understanding**: a module is done only when the maintainer can
  explain it (specification section 9.4: "I can explain the technical choice in
  two minutes") and its tutorial is written without looking at the code.
- **Traceability**: the pull request template states whether AI was used and
  what for; the commits concerned carry a `Co-Authored-By` trailer.
- **Provenance**: no passage whose origin is not understood is reused. The same
  rule applies to PolygonMeshVirtualFixture
  ([RJ-005](docs/quality/specification.md#104-risques-projet-rj-xxx)): it has
  no licence, so its code may be read to understand the approach, but never
  copied or adapted line by line (specification section 12.3).
- **Agent safety**: the agent works on a branch, never on `main` (protected by
  the rulesets); it has no access to any secret; no irreversible action
  (publishing a release, tag, deletion) without the maintainer's approval.

## If you contribute with AI

- Fill in the **AI usage** section of the
  [pull request template](.github/PULL_REQUEST_TEMPLATE.md): whether AI was
  used and what for, what the AI wrote, and what was written or reviewed by
  hand.
- Add a `Co-Authored-By` trailer to each commit with AI-generated content.
- Do not reuse code of unclear origin.
- The Panda kinematics, the shaft/sphere check (EF-402), the state machine
  (ES-007, ES-012, ES-013) and the safety test cases are written by the
  maintainer, with the AI used only as a tutor. If your pull request touches
  them, say so in its AI usage section.

Like any other code, your pull request goes through the CI and the
maintainer's review.

## See also

- [`CLAUDE.md`](CLAUDE.md): the project context, conventions and rules given to
  the AI agent.
- [Pull request template](.github/PULL_REQUEST_TEMPLATE.md).
- [Specification, section 9.5](docs/quality/specification.md#95-usage-de-lia-agentique)
  (in French).
