# Interface and packaging standards

| Standard | Edition | Layers | Scope | Governance |
|---|---|---|---|---|
| [MCP](https://modelcontextprotocol.io/specification/2026-07-28) | 2026-07-28 | L1 | Model Context Protocol | Linux Foundation / AAIF. Contributed by Anthropic |
| [AGENTS.md](https://agents.md) | n/a | L2 | Repository instructions for coding agents | Linux Foundation / AAIF. Contributed by OpenAI |
| [Agent Plugins](https://agent-plugins.org/specification) | 1.0.0 | L1, L2 | Portable packaging for skills and MCP servers | Independent TSC. Amazon, Cursor, Microsoft, OpenAI, Vercel |
| [Agent Skills](https://agentskills.io/specification) | unversioned | L2 | SKILL.md format; packaged by Agent Plugins | Originated at Anthropic. The Agent Skills specification defines the skill format |
| [A2A](https://a2a-protocol.org/latest/specification/) | 1.0.1 | L7 | Agent2Agent Protocol | Linux Foundation / AAIF since 2026-08-17. Contributed by Google. Over 150 organizations |

Agent Skills defines the SKILL.md format. Agent Plugins 1.0 packages skills and MCP servers, with a root plugin.json and skills/ directory. Client-specific hooks, custom agents and LSP integrations are outside its portable core.

A recorded support value points to repository evidence; it does not certify support for every feature or for the latest protocol revision. A2A 1.0.1 is a specification patch; the wire protocol uses version 1.0.

## Sources

- [https://modelcontextprotocol.io/specification/2026-07-28](https://modelcontextprotocol.io/specification/2026-07-28) (accessed 2026-10-28)
- [https://agents.md](https://agents.md) (accessed 2026-10-28)
- [https://agent-plugins.org/specification](https://agent-plugins.org/specification) (accessed 2026-10-28)
- [https://agentskills.io/specification](https://agentskills.io/specification) (accessed 2026-10-28)
- [https://a2a-protocol.org/latest/specification/](https://a2a-protocol.org/latest/specification/) (accessed 2026-10-28)
- [https://agent-plugins.org/specification#71-skills](https://agent-plugins.org/specification#71-skills) (accessed 2026-10-28)
- [https://github.com/a2aproject/A2A/releases/tag/v1.0.1](https://github.com/a2aproject/A2A/releases/tag/v1.0.1) (accessed 2026-10-28)
- [https://blog.modelcontextprotocol.io/posts/2026-07-28/](https://blog.modelcontextprotocol.io/posts/2026-07-28/) (accessed 2026-10-28)
