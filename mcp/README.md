# MCP Server Setup

This directory contains Docker configurations for running MCP (Model Context Protocol) servers in HTTP mode.

## Why HTTP Mode?

**Important:** Agents in this project MUST use HTTP-mode MCP servers. The stdio transport is currently not supported due to subprocess handling limitations in Claude Code when agents start their own MCP server instances.

## Setup

### 1. Configure Environment

Copy the example environment file and fill in your credentials:

```bash
cp .env.example .env
```

Edit `.env` with your Atlassian credentials:
- `CONFLUENCE_URL` - Your Confluence instance URL
- `CONFLUENCE_USERNAME` - Your email
- `CONFLUENCE_API_TOKEN` - API token from atlassian.com
- `JIRA_URL` - Your Jira instance URL
- `JIRA_USERNAME` - Your email
- `JIRA_API_TOKEN` - API token from atlassian.com

### 2. Start MCP Servers

```bash
docker compose up -d
```

### 3. Verify

Check that the MCP server is running:

```bash
docker compose ps
```

The mcp-atlassian server should be accessible at `http://localhost:9000`.

## Managing Servers

Stop servers:
```bash
docker compose down
```

View logs:
```bash
docker compose logs -f
```

## Available MCP Servers

- **mcp-atlassian** (port 9000) - Confluence and Jira integration via [sooperset/mcp-atlassian](https://github.com/sooperset/mcp-atlassian)
