# Pipeline Test Matrix

| Pipeline | Happy path | Gate failure | Revision | Human review |
|---|---|---|---|---|
| document-review | required | yes | bounded | required |
| academic-paper | required | yes | bounded | required |
| manuscript-development | required | yes | bounded | required |
| literature-review | required | yes | bounded | required |
| submission-readiness | required | yes | bounded | required |

## Contract assertions

Every reference pipeline must declare a unique ID and semantic version, inputs and outputs, entry and terminal stages, explicit dependencies, stable capability identifiers, failure behavior for substantive stages, gate acceptance criteria, bounded revision behavior, and a final human approval point for high-stakes artifacts.
