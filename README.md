# SpriteCook OpenCode Plugin

Generate game sprites, animations, tilesets, and textures inside [OpenCode](https://opencode.ai) with [SpriteCook](https://spritecook.ai).

This repository is the source of truth for the SpriteCook OpenCode integration. It packages:

- the hosted SpriteCook MCP connection for OpenCode
- bundled SpriteCook skills (generation, animation, tilesets, Godot export)
- an example `opencode.json` config

## Install

One command. It adds the SpriteCook MCP server to your global OpenCode config and copies the bundled skills into `~/.config/opencode/skills/`.

macOS / Linux:

```bash
curl -fsSL https://spritecook.ai/install-opencode.sh | bash
```

Windows (PowerShell):

```powershell
iwr -useb https://spritecook.ai/install-opencode.ps1 | iex
```

Then restart OpenCode and approve the SpriteCook OAuth prompt on first use.

## Manual install

Add the SpriteCook MCP server to your `opencode.json` (project-local, or global at `~/.config/opencode/opencode.json`):

```json
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "spritecook": {
      "type": "remote",
      "url": "https://api.spritecook.ai/mcp/openai",
      "enabled": true
    }
  }
}
```

Optionally copy the folders from [`skills/`](skills/) into `~/.config/opencode/skills/` (global) or `.opencode/skills/` (per project). The skills teach the agent SpriteCook's recommended workflows: style consistency with `reference_asset_id`, asset manifests, credit checks, and animation pipelines.

## Repository layout

- [`skills/`](skills/): bundled SpriteCook skills
- [`opencode.json.example`](opencode.json.example): minimal config with the SpriteCook MCP server

## Authentication

OpenCode connects to the hosted SpriteCook MCP endpoint:

- `https://api.spritecook.ai/mcp/openai`

OpenCode handles authentication through SpriteCook's OAuth flow on first protected use. No API keys in config files.

## What you can do once connected

- Generate pixel art and detailed/HD game assets from a prompt
- Keep every asset on-style by passing `reference_asset_id`
- Edit existing assets with `edit_asset_id`
- Generate autotile tilesets and use them with a dual-grid renderer
- Animate assets and export Godot-ready character packages

## Skill source of truth

The bundled skills are maintained in [SpriteCook/skills](https://github.com/SpriteCook/skills). When those change, sync the updated `SKILL.md` files into [`skills/`](skills/).

## Related

- [SpriteCook for AI agents](https://spritecook.ai/agents)
- [Codex plugin](https://github.com/spritecook/codex-plugin)
- [Claude Code plugin](https://github.com/SpriteCook/spritecook-claude-plugin)
- [Cursor plugin](https://github.com/SpriteCook/plugin)
- [`spritecook-mcp` on npm](https://www.npmjs.com/package/spritecook-mcp) for any other MCP editor
