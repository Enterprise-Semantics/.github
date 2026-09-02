# Pull Request

## What does this PR do?

<!-- One-paragraph summary of the change. -->

## Linked governance artifact

<!-- One of: Finding / ADR / CR. Provide the link and the ID. -->

- [ ] Finding: FND-ES-
- [ ] ADR: ADR-ES-
- [ ] CR: CR-ES-

If none of the above, explain why below.

## Type of change

- [ ] Concept record (new or updated)
- [ ] Relationship record (new or updated)
- [ ] Specification change
- [ ] Documentation only
- [ ] Conformance / test harness
- [ ] Mapping record
- [ ] Visual / diagram source
- [ ] Governance workflow / template

## Repositories affected

<!-- List every repository this PR touches, even tangentially. -->

- [ ] `enterprise-semantics`
- [ ] `enterprise-semantics-spec`
- [ ] `enterprise-semantics-governance`
- [ ] `enterprise-semantics-docs`
- [ ] `enterprise-semantics-examples`
- [ ] `enterprise-semantics-mappings`
- [ ] `enterprise-semantics-visuals`
- [ ] `enterprise-semantics-test-probe`
- [ ] `.github`

## Lifecycle status

If this PR changes a concept or relationship record, what is the new status?

- [ ] Candidate
- [ ] Investigating
- [ ] Proposed
- [ ] Established
- [ ] Canonical
- [ ] Mapped
- [ ] Deprecated
- [ ] Retired

## Verification performed

- [ ] Local conformance check passes (`python3 enterprise-semantics-test-probe/tools/validate.py --source enterprise-semantics`)
- [ ] All concept identifiers in the change are unique
- [ ] All references resolve (no broken cross-references)
- [ ] Lifecycle state values are in the controlled enum
- [ ] Provenance fields are populated
- [ ] Generated artifacts (Markdown, JSON, PlantUML) regenerated if affected

## Style and language

- [ ] No en-dash (–) or em-dash (—) in newly authored content (use colons / semicolons)
- [ ] Spec tone in normative documents (no "We should..." narration)

## Checklist

- [ ] Commit messages follow `<type>: <imperative description>`
- [ ] One logical change per commit
- [ ] Branch name is `feature/<description>`, `fix/<description>`, `refactor/<description>`, or `docs/<description>`
- [ ] No debug statements, secrets, or unrelated changes

## Notes for the reviewer

<!-- Anything that helps the reviewer: open questions, trade-offs, alternative approaches considered. -->