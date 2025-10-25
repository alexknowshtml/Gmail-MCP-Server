# Local Gmail MCP Server Fork

This is a local fork of [GongRzhe/Gmail-MCP-Server](https://github.com/GongRzhe/Gmail-MCP-Server) maintained for bug fixes and custom features.

## Current Status

**Installed globally via symlink:**
```bash
npm list -g @gongrzhe/server-gmail-autoauth-mcp
# → /home/alexhillman/.nvm/versions/node/v22.21.0/lib
# └── @gongrzhe/server-gmail-autoauth-mcp@1.1.11 -> ./../../../../../andy/Gmail-MCP-Server
```

**Remote setup:**
- `origin`: https://github.com/alexknowshtml/Gmail-MCP-Server.git (your fork)
- `upstream`: https://github.com/GongRzhe/Gmail-MCP-Server.git (original repo)

## Bug Fixes Applied

### Fix list_filters bug (PR #56)
**Issue:** `list_filters` always returned empty results
**Fix:** Changed `response.data.filters` to `response.data.filter` in `src/filter-manager.ts:70`
**PR:** https://github.com/GongRzhe/Gmail-MCP-Server/pull/56

## Development Workflow

### Building after changes:
```bash
cd /home/alexhillman/andy/Gmail-MCP-Server
npm run build
```

### Testing locally:
```bash
# Restart Claude Code to reload MCP server
# Or use test script:
cd /home/alexhillman/andy/scripts
node test-gmail-filters-api.js
```

### Syncing with upstream:
```bash
git fetch upstream
git merge upstream/main
npm install
npm run build
```

### Updating global install:
No action needed - global package is symlinked to this directory.
Changes take effect after `npm run build` and Claude Code restart.

## Related Files

- `/home/alexhillman/andy/scripts/test-gmail-filters-api.js` - Direct Gmail API test script
- `/home/alexhillman/andy/.claude/commands/email-filter-unified.md` - Uses list_filters functionality

## Notes

- Keep this directory for easy updates and custom patches
- Changes require rebuild + Claude Code restart to take effect
- PR submitted to upstream - may be merged or need updates
