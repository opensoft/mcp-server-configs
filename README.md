# MCP Server Configurations

This repository contains Model Context Protocol (MCP) server configurations for Warp.

## What is MCP?

Model Context Protocol (MCP) is an open-source standard that allows AI assistants to securely connect to data sources and tools. Each MCP server provides specific capabilities that extend your AI assistant's functionality.

## Available MCP Servers

### 🐙 GitHub (`github.json`)
Connect to GitHub repositories, issues, pull requests, and more.
- **Requirements**: GitHub Personal Access Token
- **Capabilities**: Repository management, issue tracking, PR operations

### 🎨 Figma (`figma.json`) 
Access Figma files, components, and design data.
- **Requirements**: Figma API Key
- **Capabilities**: Design file access, component extraction, image downloads

### 🌐 Puppeteer (`puppeteer.json`)
Browser automation for web scraping and screenshots.
- **Requirements**: None (uses npx)
- **Capabilities**: Web navigation, screenshots, form filling

### 🔍 Sentry (`sentry.json`)
Error monitoring and performance tracking integration.
- **Requirements**: None (authentication handled through web interface)
- **Capabilities**: Error analysis, performance monitoring, issue management

### 📚 Context7 (`context7.json`)
Library documentation and code context provider.
- **Requirements**: None
- **Capabilities**: Library documentation, code examples, API references

## Setup Instructions

1. **Go into Warp**: https://www.warp.dev/

2. **Locate your MCP configuration file**:
   - CMD-P or CTRL-SHIFT-P
   - Type in "MCP" and press enter
   - Click "Add Server"

3. **Add server configurations**: Copy the JSON from the desired server files into your configuration file

4. **Set up API keys** (if required):
   - e.g. Replace `YOUR_GITHUB_TOKEN_HERE` with your GitHub Personal Access Token
   - e.g. Replace `YOUR_FIGMA_API_KEY_HERE` with your Figma API key
   - Other servers may require additional authentication

## Contributing

Feel free to submit additional MCP server configurations or improvements to existing ones via pull requests.

## Resources

- [MCP Official Documentation](https://modelcontextprotocol.io/)
- [MCP Server Registry](https://github.com/modelcontextprotocol/servers)

---

*This repository is maintained by [Jess](//github.com/theRubberDuckiee) for educational purposes and community sharing.*
