# Agent Orchestration Framework - Example Project

A working template project demonstrating the agent-orchestration framework with HTTP-mode MCP server integration.

## Prerequisites

This project requires the [claude-agent-orchestrator](https://github.com/rawe/claude-agent-orchestrator) framework to be installed in a separate directory.

## Quick Start

1. **Setup MCP servers** - See [mcp/README.md](./mcp/README.md)
   ```bash
   cd mcp
   cp .env.example .env
   # Edit .env with your credentials
   docker compose up -d
   ```

2. **Explore available agents** - See [.agent-orchestrator/agents/README.md](./.agent-orchestrator/agents/README.md)

3. **Start using agents** - Create sessions and delegate tasks to specialized agents

## Project Structure

```
.agent-orchestrator/
├── agents/              Agent definitions (see agents/README.md)
└── agent-sessions/      Agent session logs (git-ignored)

mcp/                     Docker setup for MCP servers (see mcp/README.md)

research-results/        Research agent output (git-ignored)
```

## Documentation

- [MCP Server Setup](./mcp/README.md) - How to configure and start MCP servers
- [Available Agents](./.agent-orchestrator/agents/README.md) - Agent definitions and capabilities
