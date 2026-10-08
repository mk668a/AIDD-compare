# Choose by the constraint you need to resolve

Start with the failure you observe, then compare tools in that layer. Read the prerequisites and anti-fit conditions in the linked tool records before adopting one.

| What happens | Start here |
|---|---|
| The agent cannot reach the tools or environment it needs | [L1: Environment](layers/L1.md) |
| Relevant code or instructions are missing from its input | [L2: Context](layers/L2.md) |
| Decisions are lost between sessions | [L3: Memory](layers/L3.md) |
| Implementation starts before the intended change is clear | [L4: Specification](layers/L4.md) |
| Nobody can determine whether the result is correct | [L5: Verification](layers/L5.md) |
| Iteration has no reliable stopping condition | [L6: Loop](layers/L6.md) |
| Parallel agents duplicate work or conflict | [L7: Coordination](layers/L7.md) |

## Compare the conditions of adoption

For an existing codebase, compare `fit.extend`, `fit.restructure`, `fit.rebuild`, `fit.replace` and `fit.wrap` rather than assuming all change is a rewrite. `fit.greenfield` addresses a new system.

Check whether the workflow requires tests, clear module boundaries, a reviewer, a running service or a particular host. If data must remain local, read `data_residency` and the source supporting it. If unattended execution is required, examine approval, limits, sandbox and stop controls together.

A strict cost ceiling needs an actual bound on iteration and usage. A structural token label is not evidence that a budget will hold. Assess cost and reliability with measurements for the model, task and environment you intend to use, including failed attempts.

## Inspect evidence before choosing

Compare the artifact format and persistence, lifecycle stages and workflow. Check whether a grade describes implementation, partial support or documentation. Read `unresolved` where present; an unverified value should not decide a high-consequence choice.

Use the [comparison table](comparison.md) to narrow the choices, then follow the evidence for those entries. The comparison does not establish that an entire tool is safe or suitable for every deployment.
