# Pipeline Contract

A pipeline is a versioned, declarative workflow with explicit identity, purpose, inputs, outputs, stages, gates, failure behavior, and acceptance criteria.

## Required front matter

```yaml
id: manuscript-review
version: 0.1.0
status: experimental
purpose: Review a manuscript for structural, evidentiary, stylistic, and mechanical readiness.
inputs:
  - manuscript
outputs:
  - review_report
  - revised_manuscript
entry: intake
terminal: finalize
```

## Stage contract

```yaml
- id: structure
  kind: capability
  capability: structure-check
  depends_on: [intake]
  inputs: [manuscript]
  outputs: [structure_report]
  failure: revise
```

`capability` is an external stable identifier. It is not a path, prompt, provider, or implementation reference.

## Gate contract

```yaml
- id: evidence_gate
  kind: gate
  depends_on: [evidence_audit]
  criterion: evidence_coverage >= required
  on_fail: revise
```

## Human review

```yaml
human_review:
  required: false
  escalation:
    - gate: final_quality
      when: outcome in [revise, blocked]
```

## Versioning

Use semantic versioning for pipeline contracts. Increment MAJOR for incompatible inputs, outputs, semantics, or stage contracts; MINOR for backward-compatible stages, gates, or optional outputs; PATCH for corrections that preserve contract semantics.

## Non-goals

Do not encode model prompts, credentials, provider-specific API calls, or hidden state transitions inside pipeline definitions.
