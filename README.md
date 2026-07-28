# Runnn agent skills

[Runnn](https://runnn.io) runs business automations built by AI coding
agents. The agent builds and maintains, Runnn runs, and the human
oversees from the dashboard.

## Install

```sh
npx skills add runnn-io/skills
```

Works with Claude Code, Codex, Cursor and every other agent the
[skills CLI](https://github.com/vercel-labs/skills) supports.

## Skills

- **runnn** — build, deploy and maintain business automations on a
  Runnn workspace. Job-first working practice, session ritual, and the
  guardrails (dry-green gate, nothing leaves without a yes). The live
  platform contract is always fetched fresh from
  [`/api/v1/docs`](https://app.runnn.io/api/v1/docs), never baked in.

## Versioning

The canonical source lives in the platform monorepo and is synced here
automatically on every change. The API index at
[`app.runnn.io/api/v1`](https://app.runnn.io/api/v1) reports the current
published version in its `skill` block; the skill checks it at session
start and asks to be reinstalled when it is stale.
