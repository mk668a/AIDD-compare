# Quality rubric

The tool, not the code it emits and not the product its operator is building. The security gates and the UI/UX axis judge those other objects and are kept separate for that reason.

Frame: ISO/IEC 25010:2023 product quality, applied to the tool itself. Names and sources: [quality reference](../data/quality-25010.json).

## Grades

| Grade | Meaning |
|---|---|
| impl | The property is implemented, and a file in the repository shows it |
| part | Implemented for part of the surface, or behind a non-default option |
| doc | Documented only. The project asks for it or claims it, and nothing enforces it |
| none | Absent. The files that would show it were read, and nothing implements or documents it |
| na | Not applicable to this kind of entry, with the reason recorded |
| not-assessed | Not examined. This is not the same as absent |

## How the evidence was assessed

| Method | Meaning |
|---|---|
| cited | Derived from another recorded axis. The evidence names that axis; it is not an independent reassessment. |
| tree | Decided from repository paths and CI workflow contents. Evidence identifies the deciding path. |
| read | A bounded search for specific markers in named files, not a full code review. Evidence identifies the path and matched text. Examples, fixtures and the project’s own agent configuration are excluded. |
| out-of-reach | Not assessed by this comparison. |

## Indicators

### fs.scope: Does the repository state the job it does, in a place a machine can find, rather than only in prose?

impl when a manifest, command set, skill set or spec declares the surface. doc when only the README states it. none when neither.

Evidence: The manifest or instruction file that declares the surface

Method: tree.

### fs.example: Does it ship something that exercises its primary function: an example, a fixture, a template?

impl when an example or template is shipped and referenced. part when one exists but is not referenced. none when absent.

Evidence: The example, fixture or template path

Method: tree.

### pe.budget: Can the operator put a ceiling on one run: a turn limit, a token budget, a timeout, a cost cap?

impl when a configuration key or flag sets it. doc when the README advises a limit and nothing enforces one. none when the design has no ceiling.

Evidence: The configuration key, flag or schema that sets the ceiling

Method: read.

### co.standards: Does it conform to the five neutral interface standards: MCP, AGENTS.md, Agent Plugins, Agent Skills, A2A?

Cited from standards_conformance, which is already decided from the repository tree with an evidence path. Not re-scored here.

Evidence: standards_conformance.evidence

Method: cited.

### co.coexist: Does the project state how it behaves beside another tool occupying the same slot, whether that is composition or conflict?

impl when a documented mechanism composes with another tool. doc when a conflict or a precedence rule is stated. none when the project is silent, which is not the same as no conflict.

Evidence: The file stating the relationship

Method: read.

### ic.surface: What does a person actually operate: a CLI, a TUI, an editor extension, a web interface, a library, or nothing directly?

Recorded as a value, not a grade. na when the entry has no human-facing surface by design, which is a finding rather than a gap.

Evidence: The entry point that presents the surface

Method: read.

### ic.help: Can a first-time operator find out what to run, from the tool itself rather than from the README?

impl when the surface carries built-in help or a guided first run. doc when only external documentation explains it. none when neither.

Evidence: The help text, usage output, or getting-started command

Method: read.

### ic.error: When the operator asks for something destructive or impossible, does the tool stop them, or does it proceed?

impl when a confirmation, dry run or refusal is implemented. doc when the documentation warns and nothing checks. none when neither.

Evidence: The confirmation, dry-run flag or validation path

Method: read.

### rl.tests: Does the repository ship tests that run without a person driving them: a test directory, files a test runner picks up?

impl when a test directory or test files exist. part when tests cover a fraction that the project itself describes as partial. none when absent.

Evidence: The test directory or test file

Method: tree.

### rl.ci: Does a workflow in the repository run those tests on every push or pull request?

impl when a workflow runs the suite. part when a workflow exists but runs only linting or a build. none when absent.

Evidence: The workflow file

Method: tree.

### rl.resume: After a run fails part way, can it be brought back to a known state: a checkpoint, a resume, a rollback, a transcript to replay?

impl when a resume or rollback path exists. doc when the documentation describes recovering by hand. none when a failed run is simply lost.

Evidence: The checkpoint, session store or resume command

Method: read.

### se.residency: Does the operator's state leave their machine to make the tool work?

Cited from data_residency.mode, already decided per entry. Not re-scored here.

Evidence: data_residency

Method: cited.

### se.attest: Does the tool sign, attest or otherwise make attributable what it emits or installs?

impl when signing or attestation is implemented. doc when the project states a provenance expectation without enforcing it. none when absent.

Evidence: The signing, checksum or attestation path

Method: read.

### se.threats: Which OWASP Agentic AI threats does adoption introduce, and which controls are implemented against them?

Cited from the threat and control axis, which was authored against OWASP Agentic AI Threats v1.1. Not re-scored here, and it does not cover confidentiality or non-repudiation.

Evidence: th and ctrl

Method: cited.

### mt.units: Is the tool composed of parts a third party can take separately: published packages, a plugin interface, an extension point?

impl when separately installable units or a plugin interface exist. part when the seams exist but are undocumented. none when it is one indivisible unit.

Evidence: The package manifest set, plugin registry or extension interface

Method: tree.

### mt.process: Is there a documented way for somebody who did not write it to change it and get the change released?

impl when contribution and release are both documented. part when one of the two is. none when neither.

Evidence: The contribution guide and the release process

Method: tree.

### mt.code: Is the tool's own code split into parts a reader can analyse and test one at a time? Deciding it means reading the codebase, so it is declared out of reach and left ungraded rather than guessed.

not-assessed for every entry. The rubric says once why it cannot be decided, rather than leaving an empty column or approximating it.

Evidence: none

Method: out-of-reach.

### fx.install: How many documented ways are there to install it, and does any of them avoid a global change to the operator's machine?

impl when an isolated install path is documented. part when only a global install is. none when installation is undocumented.

Evidence: The install instruction or package definition

Method: read.

### fx.byo: Can the operator substitute the model, the provider or the backing service, or is one vendor wired in?

impl when the provider is configurable. part when a subset is. none when one vendor is required.

Evidence: The provider configuration

Method: read.

### fx.exit: If the tool is removed, is what it produced still readable by something else?

impl when the core artifact is an open format another tool already reads. part when export exists. none when the state is proprietary or in flight only.

Evidence: artifact.format, with the store or export path

Method: cited.

### sf.reach: Can the tool act outside the working tree without a person in the loop: write elsewhere on the machine, reach the network, spend money?

Recorded as a reach statement, from exec, ctrl.approval and ctrl.egress, restated rather than re-graded. Nothing here speaks to danger to life, health, property or the environment, and for this population that would be guesswork.

Evidence: exec, ctrl.approval, ctrl.egress

Method: cited.

### sf.stop: Can a run in progress be stopped, and does stopping leave the working tree in a state the operator can reason about?

impl when a stop path exists and the state after it is documented. part when it can be stopped but the resulting state is not described. none when neither.

Evidence: The stop, cancel or kill path

Method: read.

### sf.warn: Before an action the operator cannot undo, does the tool warn or ask first: a confirmation prompt, a printed warning?

impl when a warning or confirmation precedes the irreversible action. doc when the documentation warns. none when neither.

Evidence: The warning or confirmation path

Method: read.

## Assessment limits

- Functional correctness: Requires executing the tool and checking its output against a known-correct result.
- Time behaviour: Requires measuring execution time under stated model, task and environment conditions.
- Capacity: Needs a run at scale.
- Availability: A property of an operated service, and most entries here are not operated by anyone.
- Scalability: Needs measurement at more than one size.
- Analysability: Needs reading each codebase.
- Testability: Needs reading each codebase.
- User engagement: An outcome of use. ISO/IEC 25019 covers quality in use, and this catalogue does not observe operators.
- Inclusivity: Deciding it needs an accessibility evaluation of a running interface.
- Self-descriptiveness: Partly covered by ic.help. The rest needs a running interface.
