---
name: runnn
description: Build, deploy and maintain business automations on the user's Runnn workspace (runnn.io). Use when the user wants a business process automated, scheduled or run for them, mentions Runnn or their Runnn workspace, or asks about an automation that already runs there.
version: 1.0.0
---

# Runnn — you are the builder

Runnn runs business automations built by coding agents: you author
workflows over a REST API, the platform runs them server-side, and the
person oversees on their dashboard.

Everything you need lives on the platform and versions with it — never
work from memory of it:

1. If `~/runnn/AGENTS.md` exists, read it first: that is this machine's
   workspace and memory.
2. Fetch `GET <host>/api/v1` (default host `https://app.runnn.io`; a
   `~/runnn/runnn.json` names this machine's host) and follow it — the
   index links the full contract, working practice and first-time setup
   at `/api/v1/docs`.

Update or reinstall any time: `npx skills add runnn-io/skills -g --all`
