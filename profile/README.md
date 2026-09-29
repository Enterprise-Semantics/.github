# Enterprise Semantics

> Open, governed, machine-accessible enterprise-level semantic definitions, relationships, and mappings: the controlled place where enterprise semantic knowledge matures into enterprise semantic authority.

Enterprise Semantics is an independent GitHub organization that fills the layer between **World Semantic Foundation** (foundational semantics) and **OpenDEA** (enterprise architecture metamodel). The organization holds enterprise-level semantic concepts whose definitions, relationships, lifecycles, and mappings can mature independently of any one consuming architecture.

---

## Canonical URL notice

> **Canonical organization:** https://github.com/Enterprise-Semantics
>
> An earlier organization name `Enterprise-Concepts-Model` was created and is preserved as an empty shell for historical reference. All authoritative assets, governance, decisions, and semantic artifacts live on `Enterprise-Semantics`. If you arrived from an `Enterprise-Concepts-Model` link, you are in the right place.

---

## Why the organization exists

The work undertaken across the Agentic Enterprise, Agentic Operations, Value Stream, Capability, Autonomous Operations, and related investigations has produced a growing body of enterprise concepts. Their precise meaning, specialization, composition, and relationships require continued investigation before they are suitable for incorporation into authoritative metamodels.

Putting them directly into OpenDEA would make an architectural implementation decision before semantic investigation is complete. Keeping them only in working documents makes them difficult to discover, reference, reuse, or consume programmatically. **Enterprise Semantics fills this missing layer.**

---

## Architectural outcome

```
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

```
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
| --- | --- |
| **WSF** | World / foundational semantics |
| **Enterprise Semantics** | Enterprise-level semantic definitions and relationships |
| **OpenDEA** | Enterprise architecture metamodel and architectural representation |
| **DEA Catalogs** | Cataloged instances and reusable catalog content |

The arrows in the architecture represent semantic reference, specialization, alignment, and mapping: **not ownership transfer**. WSF remains the authority for its foundational scope. Enterprise Semantics becomes the authority for its governed enterprise scope. OpenDEA remains the authority for its metamodel scope. Each catalog remains the authority for its catalog instances.

---

## Repositories

The Enterprise-Semantics organization consists of 8 core repositories that form a cohesive semantic authority system:

### Core Semantic Authority

| Repository | Purpose | Status |
| --- | --- | --- |
| **[enterprise-semantics](https://github.com/Enterprise-Semantics/enterprise-semantics)** | The semantic authority repository. Structured semantic source (YAML/JSON): concepts, relationships, identifier registry. Single source of truth. | Active; 64 commits; v0.1.0-seed released; 16 concept records (Candidate + Established mix); 33 governed predicates; conformance harness implemented |
| **[enterprise-semantics-spec](https://github.com/Enterprise-Semantics/enterprise-semantics-spec)** | Normative specifications: identifier scheme, relationship vocabulary, lifecycle model, conformance requirements, serialization formats. | Skeleton (v0.0.1); specifications land after ADR-ES-001 in Phase 3 |
| **[enterprise-semantics-governance](https://github.com/Enterprise-Semantics/enterprise-semantics-governance)** | ADRs, CRs, Findings, workflow templates. Where Enterprise Semantics is governed, not just described. | Active; 104 commits; PLAN.md at v3.0.0; multiple ADRs and CRs filed and accepted |

### Supporting Repositories

| Repository | Purpose | Status |
| --- | --- | --- |
| **[enterprise-semantics-docs](https://github.com/Enterprise-Semantics/enterprise-semantics-docs)** | Human-readable documentation; generated where possible from `enterprise-semantics`. | Active; 34 commits; 5 content tranches landed; conceptual guides, architecture docs, relationship docs |
| **[enterprise-semantics-examples](https://github.com/Enterprise-Semantics/enterprise-semantics-examples)** | Worked enterprise models and reference applications. | Active; 24 commits; 3 example tranches; canonical enterprise model, Agentic Value Stream examples |
| **[enterprise-semantics-mappings](https://github.com/Enterprise-Semantics/enterprise-semantics-mappings)** | Bi-directional mappings: ES ↔ WSF, ES ↔ OpenDEA, ES ↔ DEA Catalogs. | Active; 28 commits; 2 mapping tranches; WSF and OpenDEA mappings established |
| **[enterprise-semantics-visuals](https://github.com/Enterprise-Semantics/enterprise-semantics-visuals)** | PlantUML/Mermaid/SVG sources; reproducible architectural diagrams. | Active; 25 commits; 6 content tranches; 7 architectural diagrams from FND-ES-000 |
| **[enterprise-semantics-test-probe](https://github.com/Enterprise-Semantics/enterprise-semantics-test-probe)** | Conformance harness: schema validation, ID uniqueness, broken-reference check, mapping integrity. | Active; 35 commits; CI gate implemented; 5/5 schema tests passing; per-concept test kits |

The semantic authority lives in **`enterprise-semantics`**. The other repositories support publication, governance, mapping, examples, and presentation: not six competing sources of truth, but one authority plus its supporting repositories.

---

## Human and machine access are both first-class

### Human

A person should be able to navigate **concept → definition → relationships → rationale → sources → mappings → examples** without having to understand the underlying data representation.

### Machine

A machine should be able to retrieve **concept_id, canonical_name, definition, status, version, relationships, inverse_relationships, aliases, classifications, provenance, mappings** without scraping Markdown.

**Human-readable Markdown is a presentation of the semantic model, not its machine source of truth.**

---

## Semantic lifecycle

A concept moves through lifecycle states. The seed initially holds concepts at `Candidate` status, with explicit provenance. Promotion to `Investigating`, `Proposed`, `Established`, `Canonical`, `Mapped`, `Deprecated`, or `Retired` happens through the governance sequence.

```
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

> **Seed → Canonical.** **Published → Normative.**

Authority requires the appropriate semantic lifecycle state.

---

## Governance workflow

The organization follows a governed workflow:

```
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

### Governance artifacts

| Artifact | Location | Purpose |
| --- | --- | --- |
| **Finding** | `enterprise-semantics-governance/docs/finding/` | Captures a hypothesis or investigation result from existing work. Lives verbatim. |
| **ADR** | `enterprise-semantics-governance/docs/adr/` | Governs an architectural decision. Once merged, ADRs are immutable; supersession requires a new ADR. |
| **CR** | `enterprise-semantics-governance/docs/cr/` | Implements an ADR or an independent scope change. Carries a status field. |

See CONTRIBUTING.md for the full process and templates.

---

## Style and language

This organization follows one rule for punctuation in normative documentation:

> **En-dash (–) and em-dash (—) do not appear in authored content. Use colons (:) or semicolons (;) consistently.**

Original sources that predate the rule (for example the founding findings) are preserved verbatim in the working workspace; only newly authored normative documents follow the rule.

Commit messages follow `<type>: <imperative description>`.

---

## Program plan

The current state of every repo, phase, and decision is tracked in `docs/plan/PLAN.md` in the `enterprise-semantics-governance` repository.

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
| --- | --- | --- |
| `es-plan-keeper` | every 15 minutes | Drift detection only. Read-only against GitHub. |
| `manny-es` | daily + on-demand | Daily check-in, decision surfacing, change preparation. Resolves keeper drift. |

All commits are authored by `@emmanuel-a-otchere`. `manny-es` is the proposer; the human is the approver. See the CONTRIBUTING.md for the full governance workflow.

---

## Key features

### Structured semantic source

The `enterprise-semantics` repository maintains structured YAML/JSON records that capture:
- Concept definitions with stable identifiers
- Relationships with governed predicate vocabulary
- Lifecycle status tracking
- Provenance registries (sources, findings, decisions)
- Version pointers for semantic releases

### Conformance validation

The `enterprise-semantics-test-probe` validates:
- Unique concept identifiers across the seed
- Valid names and required definitions
- Valid relationship types and inverse relationships
- No broken references
- Valid lifecycle state values
- Provenance completeness
- Mapping integrity
- Schema conformance (YAML/JSON records conform to published schemas)
- Version consistency
- Generated artifact consistency

### Bi-directional mappings

The `enterprise-semantics-mappings` repository maintains governed assertions (not copies) between:
- **WSF** (upstream): grounded-by, aligned-with, specializes, references
- **OpenDEA** (downstream): maps-to, represented-by, specializes, profile-of
- **DEA Catalogs** (instances): instance-level mappings

Each mapping carries source/target identifiers, direction, predicate, status, and provenance.

### Reproducible visuals

The `enterprise-semantics-visuals` repository holds PlantUML/Mermaid/SVG sources for:
- Architecture diagrams
- Lifecycle flows
- Semantic maps
- Comparative scenarios
- Application examples

Renders (PNG/SVG) are generated from sources; never hand-edit renders.

---

## Current state (as of September 2026)

### Released versions
- **v0.1.0-seed**: First Enterprise-Semantics seed release (September 3, 2026)

### Active semantic domains
- **Value Stream**: 13 governed predicates (v0.2.0)
- **Capability**: 9 governed predicates (v0.1.0)
- **Agentic**: 11 governed predicates (v0.3.0)
- **Total**: 33 governed predicates (v0.4.0)

### Concept inventory
- 16 concept records in various lifecycle states (Candidate + Established mix)
- Profile families for disposition handling (AI Agent, Agentic AI, AIOps, MLOps, etc.)
- Stable identifier scheme: `ES:<KIND>:<NAME>`

### Governance maturity
- Multiple ADRs filed and accepted (ADR-ES-001 through ADR-ES-010+)
- Change Requests implemented across multiple tranches
- Program plan at v3.0.0 with Phase 5 completed

---

## License

Apache License 2.0. See LICENSE.

---

## Related foundations

- [World Semantic Foundation](https://github.com/World-Semantic-Foundation): upstream foundational semantics
- [OpenDEA](https://github.com/OpenDEA): downstream enterprise architecture metamodel

---

## Contributing

Contributions follow the governed workflow outlined above. See each repository's CONTRIBUTING.md for specific guidelines. All governance documents follow the dash-normalization rule (colons/semicolons only, no en-dash or em-dash).

Key principles:
- **Source of truth**: Structured semantic source (YAML/JSON) is authoritative, not Markdown
- **Stable identity**: Every concept carries a stable identifier independent of filename or display name
- **Governed change**: All semantic changes require ADR + CR approval
- **Conformance first**: All contributions must pass the test-probe validation

---

## Getting started

### For humans
1. Browse [enterprise-semantics-docs](https://github.com/Enterprise-Semantics/enterprise-semantics-docs) for conceptual guides
2. Explore [enterprise-semantics-examples](https://github.com/Enterprise-Semantics/enterprise-semantics-examples) for worked examples
3. Review [enterprise-semantics-governance](https://github.com/Enterprise-Semantics/enterprise-semantics-governance) for decision history

### For machines
1. Clone [enterprise-semantics](https://github.com/Enterprise-Semantics/enterprise-semantics) for structured semantic source
2. Validate against schemas in `schema/` directory
3. Run conformance checks via [enterprise-semantics-test-probe](https://github.com/Enterprise-Semantics/enterprise-semantics-test-probe)
4. Query mappings from [enterprise-semantics-mappings](https://github.com/Enterprise-Semantics/enterprise-semantics-mappings)

---

*Last updated: September 29, 2026*
