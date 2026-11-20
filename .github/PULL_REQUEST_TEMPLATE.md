## Description

<!-- What changes and why. Link the specification section or ADR it implements. -->

## Requirements covered

<!--
Requirement IDs (EF-xxx, ENF-xxx, ES-xxx), e.g. "EF-202, ES-002".
Add "partly" when the requirement is not fully covered yet. Write "None" if no requirement is covered.
-->

## Risks affected

<!--
Product (RP-xxx) and project (RJ-xxx) risk IDs this change touches. A touched risk triggers a review of the risk register (specification §10.5).
Write "None" if no risk is affected.
-->

## Tests added

<!--
Each new test and the requirement it declares (`RecordProperty` in gtest, `record_property` in pytest, the equivalent annotation in Vitest and Playwright).
For a safety requirement (ES-xxx), the tests come from the maintainer's test cases (`docs/quality/test-cases.md`).
Write "None" with the reason, and say how the change was checked.
-->

## AI usage

<!--
Whether AI was used and what for: what the AI wrote, and what the maintainer wrote or reviewed.
If this change touches the Panda kinematics, the shaft/sphere check (EF-402), the state machine (ES-007, ES-012, ES-013) or the safety test cases, confirm that the maintainer wrote them, with the AI used only as a tutor (specification §9.5).
Write "None" if no AI was used.
-->

## Checklist

<!-- Only what the CI does not check. Tick each item, or strike it through and say why it does not apply. -->

- [ ] Each new test declares the requirement it verifies.
- [ ] Safety tests (ES-xxx) were written before the code they verify.
- [ ] No requirement (EF, ENF, ES) or risk (RP, RJ) in the specification changed without an accepted ADR; any specification change is recorded in its version history.
- [ ] Documentation is updated; an ADR is written if an architecture decision was made.
- [ ] No reused code of unclear origin.
- [ ] Commits with AI-generated content carry a `Co-Authored-By` trailer.
- [ ] I can explain the technical choices of this change in two minutes.

Closes #<issue>
