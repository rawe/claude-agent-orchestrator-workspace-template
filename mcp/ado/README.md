# Azure DevOps MCP HTTP Wrapper

HTTP wrapper for Microsoft's official Azure DevOps MCP server, enabling remote access to work items via Streamable HTTP transport.

**Wrapped MCP Server:** [@azure-devops/mcp](https://github.com/microsoft/azure-devops-mcp)

## Prerequisites

- Docker & Docker Compose
- Azure DevOps Personal Access Token (PAT) with:
  - Work Items (Read)
  - Project and Team (Read)

## Quick Start

1. **Configure environment**
   ```bash
   cp .env.example .env
   ```

2. **Edit `.env` with your credentials**
   ```bash
   ADO_ORG=your-organization-name
   ADO_PAT=your-personal-access-token
   ```

3. **Start the server**
   ```bash
   docker-compose up -d
   ```

4. **Verify health**
   ```bash
   curl http://127.0.0.1:3000/health
   ```

## Usage

### Health Check
```bash
curl http://127.0.0.1:3000/health
```

### MCP Request Example
```bash
curl -X POST http://127.0.0.1:3000/mcp \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "method": "tools/call",
    "params": {
      "name": "list_work_items",
      "arguments": {"project": "YourProject"}
    },
    "id": 1
  }'
```

## Management

**View logs:**
```bash
docker-compose logs -f
```

**Stop server:**
```bash
docker-compose down
```

**Rebuild after changes:**
```bash
docker-compose up -d --build
```

## Architecture

- **HTTP Server:** Express.js on port 3000 (127.0.0.1 only)
- **MCP Backend:** Microsoft's @azure-devops/mcp
- **Transport:** stdio-to-HTTP bridge
- **Scope:** Work items domain only

See `docs/ado-mcp-http-wrapper-architecture.md` for details.

## Troubleshooting

**Container fails to start:**
- Check `.env` has valid ADO_ORG and ADO_PAT
- View logs: `docker-compose logs`

**Health check fails:**
- MCP process may be initializing (wait 10-30s)
- Check PAT permissions and expiration

**Authentication errors:**
- Verify PAT has required scopes
- Regenerate PAT if expired

## Security Notes

- Server binds to 127.0.0.1 (local access only)
- Never commit `.env` file
- Rotate PAT regularly (90 days recommended)
