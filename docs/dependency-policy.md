# Dependency Policy

AuthorOps-Pipeline is intentionally independent from implementation repositories.

## Allowed

- Stable capability identifiers.
- Declared capability contract versions.
- Pipeline-to-pipeline references through stable IDs and versions.
- Runtime adapters outside this repository.

## Forbidden

- Relative imports into another repository.
- Copying capability prompts into pipeline definitions.
- Provider/model names as execution requirements.
- Secrets, credentials, or API endpoints.
- Undocumented assumptions about another repository's internal structure.

## Compatibility

A pipeline declares the minimum capability contract it requires. Runtime resolution selects an implementation that satisfies that contract.
