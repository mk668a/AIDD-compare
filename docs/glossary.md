# Comparison vocabulary

## layer

| Value | Definition |
|---|---|
| L1 | Environment and tools: the actions an agent can take at all. Sandboxes, shells, MCP servers, worktrees. |
| L2 | Context: what the model is shown on each inference, and what is kept out of it. |
| L3 | Memory: state that survives from one session to the next. |
| L4 | Spec: what is to be built, written down before it is built. |
| L5 | Verification: the definition of done, and the gates that hold it. |
| L6 | Loop: iteration control, and the condition that stops it. |
| L7 | Organization: division of labour across several agents. |

## residency

| Value | Definition |
|---|---|
| local-first | Runs on the operator's machine and keeps the state there. |
| self-hostable | Needs a server, but one the operator can stand up themselves. |
| service-required | Cannot run without somebody else's service. |

## lifecycle

| Value | Definition |
|---|---|
| persistent | Outlives the run that made it. |
| ephemeral | Lives only as long as the run. |
| na | Nothing is left behind, so the question does not arise. |

## addressee

| Value | Definition |
|---|---|
| human | Written to be read by a person. |
| agent | Written to be read by an agent. |
| both | Written to be read by either. |
| na | Nothing is left behind to read. |
| not-assessed | Could not be determined. Not the same as absent. |

## basis

| Value | Definition |
|---|---|
| stated | The project says so, and a quote is on record. |
| gated | An approval step forces a person to read it. |
| inferred | Read off the shape of the artifact. Not the project's claim. |
| na | Nothing is left to read, so the question does not arise. |
| not-assessed | Could not be determined. |

## status

| Value | Definition |
|---|---|
| stable | The specification is settled. |
| published | Published and in use. |
| working-draft | The next revision is still open. |

## constraint

| Value | Definition |
|---|---|
| experimental | Nothing outside the team depends on it yet. A wrong turn costs the time to take it again, and nothing else. |
| standard | Real users and real regressions, but no outside party asks how the change was made. |
| regulated | An outside party can ask how a change was decided, so the record has to outlive the work. |
| safety-critical | A failure can hurt someone. A persistent artifact is a precondition here, not a preference. |

## design_concerns

| Value | Definition |
|---|---|
| screen-flow | Which screens exist, and how a person moves between them. |
| data-model | The entities, their fields, and the relations between them. |
| api-contract | The interface between two parts, stated so both sides can be built against it. |
| architecture | How the system divides into parts, and which part depends on which. |
| behaviour | What the system does in a given situation, written as scenarios or acceptance criteria. |
| process | The order of work: which step follows which, and what has to hold before each. |
| convention | The rules the code itself must follow: naming, layout, and the choices a reviewer would otherwise argue about. |
| visual-identity | The design system: tokens, and the reasoning behind them. |
| none | The tool instructs no design artifact at all. |
| not-assessed | Not examined on this axis. Not the same as none. |

## spec_unit

| Value | Definition |
|---|---|
| capability-delta | One change to one capability. The unit is the difference, not the document. |
| phase-document | One document per lifecycle phase: requirements, then design, then tasks. |
| document-per-concern | One document per concern, held side by side rather than in sequence. |
| task | The unit is a single executable task. |
| test | The unit is a test. The specification is what has to pass. |
| convention-file | The unit is a rules file the agent reads on every run. |
| none | Nothing is cut into units; the tool has no specification stage. |
| not-assessed | Not examined on this axis. Not the same as none. |

## level

| Value | Definition |
|---|---|
| 0 not involved | The tool is not involved in the stage. |
| 1 involved, no feature | Something relevant to the stage may come out, but the tool has no feature for it. |
| 2 has a feature | The tool has a feature for the stage, but a person still does the work. |
| 3 main purpose | Doing the stage is the tool's main purpose. |

## token

| Value | Definition |
|---|---|
| frugal | Spends little: a bounded prompt and few calls. |
| moderate | Ordinary for a tool of its kind. |
| heavy | A large fixed cost, paid whether the task is small or large. |
| unbounded | No ceiling is built into the design. It can be cheap in practice, but nothing stops it being expensive. |

## format

| Value | Definition |
|---|---|
| markdown | A document a person reads and an agent follows. |
| config | A settings file a tool reads, rather than prose. |
| code | Source the project's own build consumes. |
| test-code | Executable tests. What has to pass is the artifact. |
| store | A database or an index, reached through the tool rather than by opening a file. |
| packed-text | Many files flattened into one blob shaped for a model. |
| vcs-history | Commits, branches and worktrees: the record version control already keeps. |
| trace-log | A record of what a run did, written to be read afterwards. |
| environment | A sandbox, container or machine state the tool stands up. |
| ephemeral-path | It transforms whatever passes through and keeps none of it. |
| none | Nothing is left on disk. |
| diagram | The drawing itself, kept as a file. |

## cynefin

| Value | Definition |
|---|---|
| clear | The procedure is known before you start, and applying it is the work. |
| complicated | There is a right answer, but analysis or expertise has to find it first. |
| complex | Only attempting the work reveals what it needs. Cause and effect are legible in hindsight only. |
| chaotic | Cause and effect are not stably related, so acting comes before analysing. |

## gate

| Value | Definition |
|---|---|
| blocking | When the check finds a problem, the commit or merge cannot go through. |
| non-blocking | The problem is reported, but the commit or merge still goes through. |
| none | No such check is offered. |

## control

| Value | Definition |
|---|---|
| impl | The implementation provides it. |
| part | Provided in part, or on some of the surfaces the project ships but not all. |
| doc | The documentation asks for it and nothing enforces it. |
| none | Not provided. |
| na | n/a The control cannot apply, because the tool runs no code. |

## conformance

| Value | Definition |
|---|---|
| yes | A file in the repository shows it. |
| no | The tree was read, and nothing in it shows the standard. Not a fault. |
| not-assessed | The repository was not read on this axis. A different claim from the one above. |

## hcd_activity

| Value | Definition |
|---|---|
| present | The tool carries the activity. |
| absent | It does not. |
| open-cycle | It designs and never evaluates, so the cycle never closes. |
