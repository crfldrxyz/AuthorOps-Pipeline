# Agent Operating Rules

## Mission

Build and maintain declarative workflows for high-quality knowledge production.

## Hard boundaries

1. Do not implement individual capabilities here. Reference them by stable identifiers.
2. Do not embed provider-specific prompts, credentials, or API calls in pipeline definitions.
3. Do not silently weaken or bypass quality gates to force completion.
4. Do not erase provenance when transforming artifacts.
5. Do not treat human approval as equivalent to automated confidence.
6. Do not add a workflow solely to increase catalogue size; it must represent a meaningful recurring production pattern.

## Required work sequence

Before adding or changing a pipeline:
1. Read the pipeline contract.
2. Inspect the registry conventions.
3. Identify inputs, outputs, stages, dependencies, gates, and failure routes.
4. Add or update representative fixtures.
5. Validate schema conformance.
6. Review for cycles, unreachable stages, missing outputs, and undefined failure behavior.
7. Update registry metadata.
8. Record the reason for the change.

## Quality bar

Prefer fewer, explicit, testable workflows over broad but vague orchestration. Every pipeline must have a clear terminal condition and must fail safely when required evidence or approval is unavailable.
