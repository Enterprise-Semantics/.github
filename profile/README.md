# Enterprise Semantics

> Open, governed, machine-accessible enterprise-level semantic definitions, relationships, and mappings: the controlled place where enterprise semantic knowledge matures into enterprise semantic authority.

Enterprise Semantics is an independent GitHub organization that fills the layer between **World Semantic Foundation** (foundational semantics) and **OpenDEA** (enterprise architecture metamodel). The organization holds enterprise-level semantic concepts whose definitions, relationships, lifecycles, and mappings can mature independently of any one consuming architecture.

---

## Why the organization exists

The work undertaken across the Agentic Enterprise, Agentic Operations, Value Stream, Capability, Autonomous Operations, and related investigations has produced a growing body of enterprise concepts. Their precise meaning, specialization, composition, and relationships require continued investigation before they are suitable for incorporation into authoritative metamodels.

Putting them directly into OpenDEA would make an architectural implementation decision before semantic investigation is complete. Keeping them only in working documents makes them difficult to discover, reference, reuse, or consume programmatically. **Enterprise Semantics fills this missing layer.**

---

## Architectural outcome

```text
                     WSF
                      : foundation grounding
                      v
             ENTERPRISE SEMANTICS
                      : enterprise semantic grounding
          +-----------+-----------+
          :           :           :
       Research    Concepts    Mappings
          :           :           :
          +-----------+-----------+
                      :
                 formalization
                      v
                   OpenDEA
                      :
                  instances
                      v
                DEA Catalogs
```

The semantic development loop:

```text
Existing Knowledge
       : ↓
Finding
       : ↓                       (candidate hypotheses)
ADR
       : ↓                       (governed decision)
CR
       : ↓                       (implementable change)
Implementation
       : ↓
CI
       : ↓
Published Semantic Version
       : ↓
Reference / Mapping
       : ↓
Downstream Use
       : ↓
New Finding
       : ↑
       back to the top of the loop
```

---

## Authority boundary

| Authority | Primary responsibility |
|-----------|------------------------|
| **WSF** | World / foundational semantics |
| **Enterprise Semantics** | Enterprise-level semantic definitions and relationships |
| **OpenDEA** | Enterprise architecture metamodel and architectural representation |
| **DEA Catalogs** | Cataloged instances and reusable catalog content |

The arrows in the architecture represent semantic reference, specialization, alignment, and mapping: **not ownership transfer**. WSF remains the authority for its foundational scope. Enterprise Semantics becomes the authority for its governed enterprise scope. OpenDEA remains the authority for its metamodel scope. Each catalog remains the authority for its catalog instances.

---

## Repositories

| Repository | Purpose |
|------------|---------|
| [enterprise-semantics](https://github.com/Enterprise-Semantics/enterprise-semantics) | The semantic authority repository. Structured semantic source (YAML/JSON): concepts, relationships, identifier registry. Single source of truth. |
| [enterprise-semantics-spec](https://github.com/Enterprise-Semantics/enterprise-semantics-spec) | Normative specifications: identifier scheme, relationship vocabulary, lifecycle model, conformance requirements, serialization formats. |
| [enterprise-semantics-governance](https://github.com/Enterprise-Semantics/enterprise-semantics-governance) | ADRs, CRs, Findings, workflow templates. Where Enterprise Semantics is governed, not just described. |
| [enterprise-semantics-docs](https://github.com/Enterprise-Semantics/enterprise-semantics-docs) | Human-readable documentation; generated where possible from `enterprise-semantics`. |
| [enterprise-semantics-examples](https://github.com/Enterprise-Semantics/enterprise-semantics-examples) | Worked enterprise models and reference applications. |
| [enterprise-semantics-mappings](https://github.com/Enterprise-Semantics/enterprise-semantics-mappings) | Bi-directional mappings: ES ;;; WSF, ES ;;; OpenDEA, ES ;;; DEA Catalogs. |
| [enterprise-semantics-visuals](https://github.com/Enterprise-Semantics/enterprise-semantics-visuals) | PlantUML/Mermaid/SVG sources; reproducible architectural diagrams. |
| [enterprise-semantics-test-probe](https://github.com/Enterprise-Semantics/enterprise-semantics-test-probe) | Conformance harness: schema validation, ID uniqueness, broken-reference check, mapping integrity. |

The semantic authority lives in **`enterprise-semantics`**. The other repositories support publication, governance, mapping, examples, and presentation: not six competing sources of truth, but one authority plus its supporting repositories.

---

## Human and machine access are both first-class

### Human

A person should be able to navigate **concept ;;; definition ;;; relationships ;;; rationale ;;; sources ;;; mappings ;;; examples** without having to understand the underlying data representation.

### Machine

A machine should be able to retrieve **concept_id, canonical_name, definition, status, version, relationships, inverse_relationships, aliases, classifications, provenance, mappings** without scraping Markdown.

**Human-readable Markdown is a presentation of the semantic model, not its machine source of truth.**

---

## Semantic lifecycle

A concept moves through lifecycle states. The seed initially holds concepts at `Candidate` status, with explicit provenance. Promotion to `Investigating`, `Proposed`, `Established`, `Canonical`, `Mapped`, `Deprecated`, or `Retired` happens through the governance sequence.

```text
Candidate
   ↓
Investigating
   ↓
Proposed
   ↓
Established
   ↓
Canonical
   ↓
Mapped
   ↓
Deprecated / Retired
```

> **Seed ;;; Canonical.**
> **Published ;;; Normative.**

Authority requires the appropriate semantic lifecycle state.

---

## Contributing

The organization follows a governed workflow:

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

See [CONTRIBUTING.md](https://github.com/Enterprise-Semantics/.github/blob/main/CONTRIBUTING.md) for the full process and templates.

---

## Style and language

This organization follows one rule for punctuation in normative documentation:

> **En-dash (–) and em-dash (—) do not appear in authored content. Use colons (:) or semicolons (;) consistently.**

Original sources that predate the rule (for example the founding findings) are preserved verbatim in the working workspace; only newly authored normative documents follow the rule.

---

## Program plan

The current state of every repo, phase, and decision is tracked in [`plans/PLAN.md`](https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/plan/PLAN.md) (currently staged in the local working folder until `enterprise-semantics-governance` lands).

A persistent plan-keeper reconciles the live org state against the plan every 15 minutes and surfaces drift only when it occurs.

---

## Program ownership

Every repository in this organization has a single human owner (`@emmanuel-a-otchere`) and one persistent sub-agent that proposes and prepares changes.

**`manny-es`** is the dedicated sub-agent responsible for `Enterprise-Semantics`. It runs as a Hermes cronjob (job id `c0b35d4938af`) on the `coder` profile and posts a daily check-in to the home Discord channel. To fire an immediate check-in:

```bash
cronjob action=run job_id=c0b35d4938af
```

A sibling agent, `es-plan-keeper` (job id `434b5c9c3023`), runs every 15 minutes and detects drift between the live org state and the program plan. `manny-es` consumes the keeper's reports and decides whether to fix, flag, or escalate. The two agents cooperate, never duplicate.

| Agent | Cadence | Purpose |
|-------|---------|---------|
| `es-plan-keeper` | every 15 minutes | Drift detection only. Read-only against GitHub. |
| `manny-es` | daily + on-demand | Daily check-in, decision surfacing, change preparation. Resolves keeper drift. |

All commits are authored by `@emmanuel-a-otchere`. `manny-es` is the proposer; the human is the approver. See the [CONTRIBUTING.md](https://github.com/Enterprise-Semantics/.github/blob/main/CONTRIBUTING.md) for the full governance workflow.

## License

Apache License 2.0. See [LICENSE](https://github.com/Enterprise-Semantics/.github/blob/main/LICENSE).

## Related foundations

- [World Semantic Foundation](https://github.com/World-Semantic-Foundation) ;;; upstream foundational semantics.
- [OpenDEA](https://github.com/OpenDEAM) ;;; downstream enterprise architecture metamodel.