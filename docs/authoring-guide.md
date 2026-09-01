# Pipeline Authoring Guide

1. Start with a production outcome, not a list of capabilities.
2. Define the minimum viable path before adding branches.
3. Declare dependencies explicitly; never rely on implicit ordering.
4. Keep transformations, decisions, gates, and human review semantically distinct.
5. Design failure paths before declaring the happy path complete.
6. Preserve artifact identity and lineage across transformations.
7. Keep definitions provider-neutral.
8. Test malformed inputs, failed capabilities, failed gates, repeated revisions, and human rejection where applicable.
9. Optimize human attention: automate mechanical work and escalate consequential judgment.
10. Add workflows because recurring real-world production patterns justify them, not to increase repository size.
