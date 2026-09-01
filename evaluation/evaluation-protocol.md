# Evaluation Protocol

A pipeline is evaluated as a workflow system, not as a prose document.

## Contract
- required fields exist;
- schema is valid;
- stage IDs are unique;
- dependencies reference existing stages;
- entry and terminal stages exist.

## Graph integrity
- no unintended dependency cycles;
- no unreachable required stage;
- no terminal path bypasses mandatory gates;
- every revision route is bounded.

## Behavior
Test the happy path plus missing input, malformed input, capability failure, gate failure, repeated revision failure, and human rejection where applicable.

## Traceability
A successful run must be explainable from recorded stages, gate outcomes, artifacts, and evidence references.

## Acceptance
A pipeline passes evaluation when behavior is predictable under normal and failure conditions, not merely when the happy path completes.
