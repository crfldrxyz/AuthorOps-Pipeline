# Run Contract

A run is an observable execution instance of a pipeline.

Required conceptual fields:

```yaml
run_id: stable-unique-id
pipeline: manuscript-review@0.1.0
status: running
started_at: timestamp
input_artifacts: []
stages: []
gates: []
artifacts: []
events: []
```

Each completed stage should record its stage id, status, timestamps, input/output artifact identifiers, attempt number, outcome, warnings/errors, and evidence references where applicable.

Allowed terminal states are `completed`, `completed_with_warnings`, `blocked`, `failed`, and `cancelled`.

A run is `completed` only when every required gate has passed and every required output exists.
