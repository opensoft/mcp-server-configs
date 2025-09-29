# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Repository Overview

This repository contains Model Context Protocol (MCP) server configurations for Warp. MCP is an open-source standard that allows AI assistants to securely connect to data sources and tools, extending AI functionality through specialized servers.

## Architecture

The repository follows a simple, flat structure where each JSON file represents a complete MCP server configuration:

- **Individual server files**: `github.json`, `figma.json`, `puppeteer.json`, `sentry.json`, `context7.json` - Each contains a single server configuration
- **Consolidated file**: `all-servers.json` - Contains all server configurations in one file for convenience
- **Documentation**: `README.md` - Comprehensive setup instructions and server descriptions

### Server Types

1. **Docker-based servers**: GitHub server runs via Docker container
2. **NPX-based servers**: Figma, Puppeteer, Sentry, and Context7 use npx for execution
3. **Remote servers**: Sentry uses a remote MCP server via URL
4. **Authentication patterns**: 
   - Environment variables (GitHub token, Figma API key)
   - Web-based auth (Sentry)
   - No auth required (Puppeteer, Context7)

## Common Development Commands

### Adding a new MCP server configuration
```bash
# Create individual server file
cat > new-server.json << 'EOF'
{
  "new-server-name": {
    "command": "npx",
    "args": ["-y", "server-package-name"],
    "env": {
      "API_KEY": "YOUR_API_KEY_HERE"
    },
    "working_directory": null
  }
}
EOF

# Add to all-servers.json (manual edit required)
# Update README.md with server description
```

### Testing configurations
```bash
# Validate JSON syntax
jq . *.json

# Test specific server configuration in Warp
# 1. Open Warp
# 2. CMD-P (or CTRL-SHIFT-P)
# 3. Type "MCP" and press enter
# 4. Click "Add Server"
# 5. Copy JSON content from desired file
```

### Repository maintenance
```bash
# Standard git workflow
git add .
git commit -m "Add new MCP server configuration"
git push origin main
```

## Configuration Patterns

### Standard Server Structure
```json
{
  "server-name": {
    "command": "command-to-run",
    "args": ["array", "of", "arguments"],
    "env": {
      "ENV_VAR": "value"
    },
    "working_directory": null
  }
}
```

### Authentication Placeholders
- Use `YOUR_TOKEN_HERE` format for API keys/tokens
- Document required permissions in README.md
- Include setup instructions for obtaining credentials

### Naming Conventions
- Use lowercase with hyphens for server names
- Match official package names where possible
- Use descriptive names that indicate functionality

## Important Notes

- All server configurations use `"working_directory": null`
- Docker-based servers require full path to docker binary (`/opt/homebrew/bin/docker`)
- NPX servers use `-y` flag for automatic yes to prompts
- Environment variables containing secrets should use placeholder values
- The `all-servers.json` file must be manually synchronized with individual files

## Integration with Warp

These configurations extend Warp's AI capabilities by providing:
- **GitHub integration**: Repository management, issue tracking, PR operations
- **Figma integration**: Design file access, component extraction
- **Browser automation**: Web scraping, screenshots via Puppeteer
- **Error monitoring**: Sentry integration for issue analysis
- **Documentation access**: Library docs and code examples via Context7

Each server appears as an available tool in Warp's AI assistant, accessible through natural language commands.
