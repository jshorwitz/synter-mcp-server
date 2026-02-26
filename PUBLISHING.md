# Publishing Synter MCP Server

## Prerequisites

1. **npm account** with access to publish to `@synterai` organization
2. **GitHub access** to push to jshorwitz/synter-mcp-server

---

## Step 1: Publish to npm

### First-time Setup

```bash
# 1. Login to npm
npm login
# Enter your npm username, password, and email
# If you have 2FA, enter the code when prompted

# 2. Verify you're logged in
npm whoami
# Should output your npm username

# 3. Verify org access
npm org ls synterai
```

### Publish the Package

```bash
cd synter-mcp-server

# Build and publish
npm run build
npm publish --access public

# Or use the shortcut
npm run publish:npm
```

### Verify Publication

```bash
# Check the package is live
npm view @synterai/mcp-server

# Test installation
npx @synterai/mcp-server
# Should fail with "SYNTER_API_KEY not set" (expected)
```

---

## Step 2: Submit to MCP Registries

### Official MCP Registry (registry.modelcontextprotocol.io)

The `server.json` file is already formatted for the official registry. To submit:

1. Fork https://github.com/modelcontextprotocol/registry
2. Add `servers/synter-ads/server.json` (copy from this repo)
3. Open a PR with title: "Add Synter Ads MCP Server"

### Docker MCP Catalog

1. Go to https://github.com/docker/mcp-registry
2. Submit via their contribution process
3. Include the streamable-http remote URL: `https://mcp.syntermedia.ai/mcp/`

### Other Directories

| Directory | URL | Status |
|-----------|-----|--------|
| PulseMCP | https://pulsemcp.com | Submit via site |
| Smithery.ai | https://smithery.ai | Submit via site |
| MCPCatalog.io | https://mcpcatalog.io | Submit via site |
| OpenTools | https://opentools.com | Submit via site |

---

## Step 3: Post-Publication Tasks

### Update Synter Docs

Add the MCP server to:
- [ ] https://syntermedia.ai/manual (add MCP section)
- [ ] https://docs.syntermedia.ai (add setup guide)
- [ ] https://syntermedia.ai/developer (link to npm package)

### Create Demo Video

Use the `recording-demo-videos` skill to create a video showing:
1. Getting an API key from syntermedia.ai/developer
2. Adding the MCP server to Claude Desktop config
3. Asking Claude to "list my campaigns"
4. Creating a new campaign with natural language

### Announce

- [ ] Post on X/Twitter (see SOCIAL_COPY.md)
- [ ] Post on LinkedIn (see SOCIAL_COPY.md)
- [ ] Submit to Hacker News
- [ ] Add to Product Hunt (if applicable)

---

## Versioning

Use semantic versioning:
- **Patch (1.0.x)**: Bug fixes
- **Minor (1.x.0)**: New tools, features
- **Major (x.0.0)**: Breaking changes

To release a new version:

```bash
cd synter-mcp-server

# Update version
npm version patch  # or minor, major

# Publish
npm publish --access public

# Push tags
git push --tags
```

---

## Troubleshooting

### "npm ERR! 403 Forbidden"

You don't have permission to publish to @synterai. Either:
1. Check you're logged into the correct npm account
2. Or ask an admin to add you to the organization

### "npm ERR! 404 Not Found" after publish

The package takes 1-5 minutes to propagate. Wait and try again.

### Package shows old version

Clear npm cache: `npm cache clean --force`
