# Evaluation axes and data fields

One JSON file describes each tool. Missing or `not-assessed` values do not establish absence. `none` denotes examined absence. Grades are not added into a total.

## Tool records

[`data/tools/`](../data/tools/) holds one file per tool.

| Field | Meaning |
|---|---|
| `slug` | Repository or canonical project identifier |
| `n` | Display name |
| `entry_kind` | Implementation or specification |
| `l` | Primary layer, L1–L7 |
| `s2` | Secondary layers |
| `dom` | Artifact domains |
| `artifact` | Format, lifecycle, intended reader and supporting evidence |
| `lic` | Recorded license identifier; consult its source |
| `stars` | Repository attention at assessment, not a quality score |
| `push` | Recorded last-push date |
| `conf` | ok or check; read unresolved before relying on a check entry |
| `exec` | Whether the tool executes code |
| `sum` | Summary of its purpose |
| `art` | Artifact left by the workflow |
| `tok` | Structural token profile, not measured cost |
| `p` | Seven lifecycle levels: requirements, design, implementation, test, review, release, operations; 0 absent, 1 touches, 2 supports, 3 primary purpose |
| `fit` | Fit for greenfield, extend, restructure, rebuild, replace and wrap; 0–5 |
| `fit_na` | Whether the codebase-change categories do not apply |
| `quality` | Indicator grades and their evidence; see quality rubric |
| `cyn` | Interpretive fit for clear, complicated, complex and chaotic contexts; 1–5 |
| `cons` | Applicable project constraints |
| `pre` | Prerequisites |
| `anti` | Situations where the tool is a poor fit |
| `th` | Recorded threat identifiers; adoption risks, not vulnerability findings |
| `ctrl` | Implemented, partial, documented, absent or non-applicable controls |
| `gate` | Checks on output and whether they block progress |
| `gnote` | Interpretation of threats, controls and gates |
| `sources` | Source URLs and access dates |
| `i18n` | Japanese descriptions |
| `standards_conformance` | Recorded support for standards with evidence |
| `data_residency` | Where state is handled and whether operator-supplied keys are supported |
| `design_concerns` | Design subjects the tool addresses |
| `spec_unit` | Unit of specification |
| `flow` | Steps, actors, layers, gates, parallel work and return edges; basis identifies source or reconstruction |
| `verified_at` | Verification date where recorded |
| `cost_warning` | Cost-related qualification |
| `ui_ux` | Interface-design support |
| `open_core` | Open-source/commercial boundary |
| `unresolved` | Reader-facing assessment uncertainty |

Read the [quality rubric](quality-rubric.md) for indicator-specific thresholds and the [glossary](glossary.md) for enumerated values.

### Nested fields

| Field | Keys | Meaning |
|---|---|---|
| `artifact` | `format`, `lifecycle`, `addressee`, `addressee_basis`, `addressee_note`, `addressee_quote`, `format_detail` | What the workflow leaves behind, who it is written for and the basis for that reading. `format_detail` lists concrete kinds, each with an `id` and an evidence path `ev`. Values are defined under `format`, `lifecycle`, `addressee` and `basis` in the glossary. |
| `fit` | `greenfield`, `extend`, `restructure`, `rebuild`, `replace`, `wrap` | Fit from 0 to 5 for each kind of codebase change. |
| `quality` | one key per indicator, plus `evidence` | One grade per indicator identifier from the quality rubric. `evidence` holds, under the same identifier, the path or statement that the grade rests on. |
| `cyn` | `clear`, `complicated`, `complex`, `chaotic` | Interpretive fit from 1 to 5 for each context; see `cynefin` in the glossary. |
| `ctrl` | one key per control | `impl`, `part`, `doc`, `none` or `na` for each control; see `control` in the glossary. An empty object means no control was recorded. |
| `gate` | `sast`, `dep`, `secret`, `a11y` | Whether each check blocks progress; see `gate` in the glossary. |
| `sources` | `url`, `accessed` | The source consulted and the date it was read. |
| `standards_conformance` | `mcp`, `agents_md`, `agent_plugins`, `agent_skills`, `a2a`, `evidence` | `yes`, `no` or `not-assessed` for each standard; see `conformance` in the glossary. `evidence` names the file that shows conformance. |
| `data_residency` | `mode`, `byok`, `note` | Where state is handled; see `residency` in the glossary. `byok` is whether operator-supplied provider keys are supported, and `null` when the tool calls no provider itself. |
| `flow` | `basis`, `path`, `kind`, `steps`, `back` | `basis` is `repo` (a shipped procedure), `readme` (a prose description) or `derived` (an order reconstructed by this comparison). `path` locates the procedure in the repository. `kind` is `sequence` or `loop`. Each step has a name `s`, a layer `l`, an actor `who` (`human`, `model` or `tool`), an optional `gate` and optional parallel branches `par`. `back` lists return edges by step index. Rendered in [Workflows](flows.md) and supported by a [flow evidence file](#flow-evidence-files). |
| `ui_ux` | `artifact`, `hcd_activities`, `handoff`, `feedback_channel`, `a11y_standard`, `note` | Interface-design support. `hcd_activities` uses the `hcd_activity` values in the glossary. |
| `i18n.ja` | `n`, `sum`, `art`, `pre`, `anti`, `gnote`, `cost_warning`, `ui_ux_note`, `flow` | Japanese renderings of the fields with the same names. |

## Flow evidence files

[`data/flow-evidence/`](../data/flow-evidence/) holds one file per tool, with the same file name as the tool record, supporting its `flow`.

| Field | Meaning |
|---|---|
| `entry`, `slug` | The tool record this file supports. |
| `flow` | `basis`, `path` and `kind` as in the record. `cite_verified` says how `path` was verified: `content` (the file was read), `listing` (the path appeared in the repository listing) or `none`. |
| `support` | How many steps there are and how many have at least one match. |
| `steps[]` | The steps of the record, each with `i` (index), `s`, `l`, `who`, optional `gate` and `par`, and `support[]`: the matches found for that step. In a match, `kind` is the kind of evidence (`path` for a file path, `heading` for a document heading, `arrow` or `mermaid` for a diagram edge, `yaml-step` for a workflow step, `cited-document` for a passage), `source` is the file in the tool's repository and `matched` lists the words that matched. |
| `probe` | `probed_at` is the date the repository was read, `source` the GitHub surfaces used, and `branch` and `tree_sha` identify the exact repository state, so that a match can be reproduced or found to have changed. |
| `evidence[]` | The cited sources behind the matches. `kind` is as above and `value` is the path or, for `cited-document`, the lines of the file named in `source` that contain the matched words. The matches are evidence to inspect, not proof that the procedure works as described. |

## Shared data files

| File | Purpose | Main fields | Read with |
|---|---|---|---|
| [`quality-25010.json`](../data/quality-25010.json) | Names, definitions and sources for the ISO/IEC 25010:2023 characteristics that frame the quality rubric, with the Japanese renderings and the limits of the sources consulted. | `standard` (designation, edition, scope, `sources` with `url`, `accessed` and `what`), `characteristics[]` (`id`, `en`, `ja`, `asks`, `sub[]`), `source_limitations` | [Quality rubric](quality-rubric.md) |
| [`health.json`](../data/health.json) | Maintenance and distribution observations for each tool at the time of assessment. | `slug`, `pushed`, `created`, `archived`, `licence`, `stars`, `forks`, `open_issues`, `contributors`, `latest_release`, and `npm` or `pypi` with the package `name` and `month` (downloads in the trailing 30 days; `null` when no package was found) | [Project health](health.md) |
| [`metrics.json`](../data/metrics.json) | A download snapshot that puts star counts in proportion. `_meta` gives the measurement date, window and the rule that stars are never shown alone. | `downloads[]` with `package`, `registry`, `downloads_monthly`, `repo`, `stars`, `downloads_per_star` and an optional `note` | [Project health](health.md) |
| [`notations.json`](../data/notations.json) | Which diagram or specification notations the tools instruct an agent to write. A notation that appears only in a project's own documentation does not count. | `id`, `label` and `src` (the standard the notation follows); `who` lists the tools whose shipped files use the notation, `ev` gives one evidence URL per tool in the same order, `n` is their count; `self` lists tools where the notation appears only in their own documentation; `note` and `i18n.ja` carry commentary and Japanese labels | `format_detail` in each tool record |
