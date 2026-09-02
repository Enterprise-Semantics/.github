# Contributing to Enterprise Semantics

Thank you for your interest in contributing to Enterprise Semantics. This document describes the governance workflow the organization uses, the templates you will need, and the standards we hold contributions to.

## Governance workflow

Every change to a normative artifact flows through the same sequence:

```text
Finding   : candidate hypotheses from existing work
   ↓
ADR       : governed architectural decision (in enterprise-semantics-governance)
   ↓
CR        : change request against the implementation (in enterprise-semantics-governance)
   ↓
PR        : pull request against the target repository
   ↓
CI        : conformance + schema validation
   ↓
Release   : semantic version tag on the authority repository
```

A **Finding** captures a hypothesis from existing work. An **ADR** (Architecture Decision Record) governs an architectural decision. A **CR** (Change Request) implements that decision. A **PR** delivers the change. **CI** verifies conformance. A **Release** tags the published semantic version.

## Repository routing

| Change type | Where it lands |
|-------------|----------------|
| Concept definition, identifier, relationship assertion | `enterprise-semantics` (the authority repo) |
| Specification, conformance requirement, serialization format | `enterprise-semantics-spec` |
| ADR, CR, Finding, workflow template | `enterprise-semantics-governance` |
| Human-readable documentation | `enterprise-semantics-docs` |
| Worked enterprise model, reference application | `enterprise-semantics-examples` |
| Mapping (ES ;;; WSF, ES ;;; OpenDEA, ES ;;; DEA Catalogs) | `enterprise-semantics-mappings` |
| Diagram source (PlantUML/Mermaid/SVG) | `enterprise-semantics-visuals` |
| Conformance test, schema, validation harness | `enterprise-semantics-test-probe` |

If unsure, open a discussion on `enterprise-semantics-governance` and the maintainers will route.

## Templates

The `enterprise-semantics-governance` repository hosts the canonical templates:

- Finding template: `docs/finding/0000-template.md`
- ADR template: `docs/adr/0000-template.md`
- CR template: `docs/cr/0000-template.md`

All three templates are dash-normalized: en-dash (–) and em-dash (—) become colons (:) or semicolons (;). Original sources that predate the rule stay verbatim in the local working workspace under `00_inbox/`.

## Pull request process

1. Fork the relevant repository.
2. Create a feature branch: `git checkout -b feature/<short-description>`.
4. Commit atomically: one logical change per commit. Use the commit message format `<type>: <imperative description>` (for example `feat: add Value Stream concept record`, `fix: correct inverse relationship on Capability`).
5. Run the local conformance check before pushing (see below).
6. Push and open a pull request. The PR description should reference the Finding / ADR / CR that authorizes the change.
7. A maintainer will review. Expect at least one round of revision for any non-trivial change.

## Local conformance

The conformance harness lives in `enterprise-semantics-test-probe`. Before opening a PR, run:

```bash
python3 enterprise-semantics-test-probe/tools/validate.py \
  --source enterprise-semantics
```

The harness verifies:

- Unique concept identifiers
- Valid names and required definitions
- Valid relationship types and inverse relationships
- No broken references
- Valid lifecycle state values
- Provenance completeness
- Mapping integrity
- Schema conformance
- Generated artifact consistency

A failing harness is a blocker. Fix the source, not the harness.

## Style and language

- All normative documents use **spec tone** (no "We should..." or first-person narration in body prose).
- En-dash (–) and em-dash (–) **do not appear** in newly authored content. Use colons (:) or semicolons (;) consistently.
- Every concept carries: `id`, `canonical_name`, `definition`, `status`, `provenance`. `relationships`, `aliases`, and `classifications` where applicable.
- Every relationship carries: `id`, `subject`, `predicate`, `object`, `status`, `provenance`, `rationale`. `inverse` where applicable.

## Reporting issues

- Security issues: follow [SECURITY.md](https://github.com/Enterprise-Semantics/.github/blob/main/SECURITY.md).
- Bugs and feature requests: open an issue in the relevant repository. Use the issue template provided.
- General questions: open a discussion on `enterprise-semantics-governance`.

## License

By contributing, you agree that your contributions will be licensed under the Apache License 2.0.