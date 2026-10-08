# Layers of AI-driven development

A layer describes the part of the workflow being designed. A tool may have a primary layer and additional secondary layers.

| Layer | What to compare |
|---|---|
| [L1: Environment and tools](L1.md) | Execution boundaries, tool access and the environment in which an agent can act. Compare sandbox, approval and network controls with the tools the task requires. |
| [L2: Context](L2.md) | The instructions and information available to a model on each inference. Compare what is selected, compressed or removed, and how the agent receives it. |
| [L3: Memory](L3.md) | Decisions and state that survive individual turns or sessions. Compare persistence, retrieval, provenance and who can modify the stored state. |
| [L4: Specification](L4.md) | The intended change expressed before implementation. Compare specification units, authority, lifecycle and the artifacts handed to an agent or reviewer. |
| [L5: Verification](L5.md) | The criteria and checks used to decide whether work is correct. Compare tests, evaluation methods and whether a failed check actually blocks progress. |
| [L6: Loop](L6.md) | Repeated work, feedback and stopping conditions. Compare iteration limits, external verification, recovery and the conditions that terminate a run. |
| [L7: Coordination](L7.md) | Division of work among agents. Compare coordination, handoffs, shared state, verification and the authority given to each participant. |
