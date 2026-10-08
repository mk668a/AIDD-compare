# Inclusion criteria

This comparison is for people using coding agents and choosing capabilities to add to their development workflow.

## Tools included

A tool must have public source under an OSI-approved license, usable documentation and an implementation beyond its README. It must have a commit within six months of assessment or an explicit maintenance-mode statement.

It must offer a documented capability to an existing coding agent: a server, skill, plugin, command, hook, convention file, or a workflow that invokes the agent. Its own development configuration, examples and test fixtures do not establish that capability. An MCP client alone does not make a project an MCP server.

At least one stage from requirements to operations must be a supported feature (level 2 or above). Specifications and design documents count as artifacts, alongside code, tests and review results.

A repository must have at least 100 stars at assessment. This is a coverage threshold, not a quality score; it can exclude new and useful tools. An absent star count is not zero. Specifications and patterns without a repository star count are assessed on their applicable source, documentation and scope requirements.

A plain coding-agent host is outside this comparison. A host is included only when it adds a specification discipline of its own, represented by `spec_unit`. General frameworks for building a new agent are outside scope unless they also ship a capability for an existing host.

## Licensing and scope

Source-available licenses are not treated as open source. Open-core products can qualify when the open-source portion works independently; their records identify that boundary. A specification must have identifiable text and version information.

Not finding a project is not evidence that it fails the criteria. Missing information remains unassessed.

## How to interpret assessments

Judge implemented behavior separately from documentation and future plans. Sources accompany claims. Prerequisites and anti-fit conditions matter as much as supported features.

`none` means examined and absent. `not-assessed` means unexamined. No total score is calculated: a single number would hide tradeoffs between different requirements.
