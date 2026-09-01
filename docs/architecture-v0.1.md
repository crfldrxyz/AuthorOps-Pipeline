# Pipeline Architecture v0.1

## Purpose

AuthorOps-Pipeline is a declarative workflow layer for serious knowledge production. It specifies how work moves through stages and quality gates without prescribing a particular agent runtime, model provider, UI, or implementation language.

## Boundary

A pipeline owns stage ordering and dependencies, routing, inputs and outputs, quality gates, retry/revision semantics, human review points, and provenance requirements.

A pipeline does not own capability implementation, model/provider selection, application UI, credentials, source databases, or hidden prompt chains.

## Execution model

```text
Artifact + Objective → INTAKE → PLAN → EXECUTE → VERIFY → REVIEW → FINALIZE
                                      │         │
                                      └─ FAIL ←─┘
                                           ↓
                                      REVISE / RETRY
```

A runtime may execute stages serially or concurrently where dependencies permit, but observable semantics must remain equivalent.

## Stage model

Each stage declares `id`, `kind`, `inputs`, `outputs`, `depends_on`, failure behavior, quality criteria, and human-review semantics.

Stage kinds are `transform`, `capability`, `decision`, `gate`, `human_review`, and `terminal`.

## Gates

A gate is a decision boundary. It must state a criterion and a failure route. Outcomes are `pass`, `pass_with_warnings`, `revise`, `blocked`, or `fail`.

## Revision loops

Revision is bounded. Each loop declares what can change, where execution re-enters, the maximum attempts, preserved evidence, and the escalation point.

## Independence

Cross-repository dependencies are identifier-level dependencies. A pipeline may reference a stable capability contract but must not import another repository's files or assume undocumented implementation behavior.

## Evolution

Production readiness requires an explicit contract, defined failure modes, testable gates, and representative fixtures. Observed failures should drive revisions and regression tests.
