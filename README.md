# AuthorOps-Pipeline

Composable workflows for reliable AI-assisted production of manuscripts, papers, books, research, reports, and other serious knowledge work.

> **Skills provide capabilities. Pipelines provide execution patterns.**

AuthorOps-Pipeline is the workflow layer of the AuthorOps ecosystem. It defines how independent capabilities are ordered, gated, routed, retried, reviewed, and completed to produce a trustworthy artifact.

## Scope

This repository owns **pipeline architecture and workflow definitions**. It does not own individual writing or research capabilities, model prompts, provider integrations, or application UX.

A pipeline may reference an external skill by a stable identifier and declared contract, but it must not depend on the skill repository's internal implementation.

## Design principles

- **Artifact-first:** every pipeline exists to transform an artifact or answer a defined production objective.
- **Explicit stages:** execution order, inputs, outputs, gates, and failure behavior are inspectable.
- **Quality before completion:** a pipeline is not complete merely because every step ran; required quality gates must pass.
- **Evidence-aware:** claims, sources, citations, transformations, and verification states remain distinguishable.
- **Human-controllable:** review, approval, override, and rejection are first-class states.
- **Deterministic orchestration:** routing rules should be explicit and reproducible wherever practical.
- **Provider-agnostic:** pipelines describe work, not a particular model or vendor.
- **Composable:** a pipeline may consume another pipeline as a declared workflow unit without importing its internals.
- **Observable:** execution should produce structured events and a traceable run record.
- **Evolutionary:** real-world failures drive pipeline revisions and regression tests.

## Repository architecture

```text
AuthorOps-Pipeline/
├── pipelines/                 # Workflow definitions
│   ├── document-review/
│   ├── academic-paper/
│   ├── manuscript/
│   ├── research/
│   └── publishing/
├── contracts/                 # Stable interfaces between stages
├── schemas/                   # Machine-readable pipeline/run schemas
├── registry/                  # Discoverable pipeline metadata
├── evaluation/                # Quality gates and evaluation protocol
├── fixtures/                  # Small deterministic test artifacts
├── tests/                     # Pipeline contract/regression tests
├── docs/                      # Architecture and authoring guidance
├── AGENTS.md                  # Agent contribution/execution rules
└── LICENSE
```

## Pipeline lifecycle

```text
INTAKE → PLAN → EXECUTE → VERIFY → REVIEW → FINALIZE
                    │          │
                    └── FAIL ──┘
                         ↓
                     REVISE / RETRY
```

A pipeline definition is a **declarative workflow contract**, not an implementation of an agent runtime. Runtime systems may execute these definitions in different ways as long as they honor the contract.

## Status

The repository begins with a deliberately small set of high-value reference pipelines and a strong contract layer. New workflows should be added when a recurring production pattern has been observed and can be specified with explicit inputs, outputs, gates, and failure semantics.

## Relationship to AuthorOps-Skills

AuthorOps-Skills and AuthorOps-Pipeline are intentionally separate repositories.

- **AuthorOps-Skills:** defines reusable capabilities.
- **AuthorOps-Pipeline:** defines reusable workflows that invoke capabilities through stable contracts.

Neither repository should rely on the other's internal files or development history.

## License

MIT
