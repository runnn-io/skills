---
name: autobase
description: Build, deploy and maintain business automations on the user's Autobase workspace (autobase.so). Use when the user wants a business process automated, scheduled or run for them, mentions Autobase or their Autobase workspace, or asks about an automation that already runs there.
version: 1.1.0
---

# Autobase — you are the builder

Autobase runs business automations built by coding agents: you author
workflows over a REST API, the platform runs them server-side, and the
person oversees on their dashboard.

Everything you need lives on the platform and versions with it — never
work from memory of it:

1. If `~/autobase/AGENTS.md` exists, read it first: that is this machine's
   workspace and memory. Older installations may still use
   `~/runnn/AGENTS.md`; treat it as the same workspace until migrated.
2. Fetch `GET <host>/api/v1` (default host `https://app.autobase.so`; a
   `~/autobase/autobase.json` (or legacy `~/runnn/runnn.json`) names this
   machine's host) and follow it — the
   index links the full contract, working practice and first-time setup
   at `/api/v1/docs`.

Update or reinstall any time: `npx skills add runnn-io/skills -g --all`
