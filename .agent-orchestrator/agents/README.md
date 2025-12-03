# Available Agents

This directory contains agent definitions for the agent-orchestration framework.

## Important: HTTP-Only MCP Servers

**Agents MUST use HTTP-mode MCP servers in their `agent.mcp.json` configuration.** The stdio transport is currently not supported due to subprocess handling limitations in Claude Code when agents start their own MCP server instances.

All required MCP servers must be started externally via Docker before use. See [../../mcp/README.md](../../mcp/README.md) for setup instructions.

## Research Agents

Research agents share a common input/output schema and output their findings to the `research-results/` directory (git-ignored).

### [Confluence Researcher](./confluence-researcher/README.md)
Research Confluence content using mcp-atlassian MCP server.

### [Jira Researcher](./jira-researcher/README.md)
Research Jira issues and projects using mcp-atlassian MCP server.

### [ADO Researcher](./ado-researcher/README.md)
Research Azure DevOps work items using mcp-ado MCP server.

### [Web Researcher](./web-researcher/README.md)
Research information from the web (no MCP server required).

### [Local Codebase Researcher](./local-codebase-researcher/README.md)
Research and analyze code in local repositories (no MCP server required).

## General Agents

### [Atlassian Agent](./atlassian-agent/README.md)
General-purpose agent for interacting with Jira and Confluence using mcp-atlassian MCP server.

### [ADO Agent](./ado-agent/README.md)
General-purpose agent for Azure DevOps work items using mcp-ado MCP server.

## Utility Agents

### [Local Repo Finder](./local-repo-finder/)
Query local repository catalog (`repos/repos.json`) to find project paths for other agents.
