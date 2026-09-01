# Quality Gates

A quality gate is a decision boundary, not a suggestion.

## Gate classes

- `integrity`: factual, attribution, citation, provenance, transformation integrity.
- `structural`: required document architecture and ordering.
- `evidence`: claims have adequate supporting evidence.
- `style`: target style and readability requirements.
- `mechanical`: grammar, spelling, punctuation, formatting.
- `compliance`: target venue or submission requirements.
- `human`: explicit author/reviewer approval.

## Outcomes

`pass` continues execution. `pass_with_warnings` continues while preserving warnings. `revise` returns to a declared revision stage. `blocked` stops until a dependency or human resolves the blocker. `fail` terminates unsuccessfully when no recovery is defined.

Every gate must identify its subject, criterion, evidence, and failure route. Avoid vague criteria such as `looks good`.
