# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository nature

This is not a code project: there is no build, lint, or test tooling. It is a scratch repo holding documents and MCP configuration. `Readme.md` is empty.

- `uml/Untitled Diagram.drawio`: a draw.io diagram (git-flow style branches: main, hotfix commit, etc.). Edit it as mxGraph XML or in diagrams.net; it is large, so read portions rather than the whole file.
- `papago_manual.pdf`: generated Japanese menu translation manual (Papago app, annotated screenshots). Binary output; regenerate rather than edit.
- `uml/test.md`: placeholder.

## MCP phone servers (`.mcp.json`)

`.mcp.json` registers two HTTP MCP servers that control Android phones: `phone2` (`https://phone2.flywithu.com/mcp`) and `phone` (`https://phone.flywithu.com/mcp`). Both authenticate with `Authorization: Bearer ${PHONE2_TOKEN}`, so that environment variable must be set in the session.

- MCP servers are read only at session start. After pulling a change to `.mcp.json`, start a new session; an existing session will not pick up the new server.
- Tools are exposed as `mcp__phone__*` and `mcp__phone2__*` (screenshot, screen_size, tap, swipe, input_text, key, set_gps). Take a screenshot first, and use `screen_size` for coordinates.
- Tools may disconnect after a worker restart; reload them with ToolSearch (`select:mcp__phone2__screenshot,mcp__phone2__swipe,mcp__phone2__tap`).
- Phone screens are 720x1600. Ads appear at the bottom of apps; never tap them or install anything from them.

## Git

Develop on branch `claude/test-q1s5wq` (remote `flywithu/uml`). The user also edits this branch directly (e.g. `.mcp.json`), so `git pull origin claude/test-q1s5wq` before working.
