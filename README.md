# Autobase agent skills

[Autobase](https://autobase.so) runs business automations built by AI coding
agents. The agent builds and maintains, Autobase runs, and the human
oversees from the dashboard.

## Install

```sh
npx skills add runnn-io/skills -g --all
```

Non-interactive: `-g` installs user-level, `--all` selects every skill
and every agent the [skills CLI](https://github.com/vercel-labs/skills)
detects (Claude Code, Codex, Cursor and the rest) with no prompts.

## Skills

- **autobase** — deliberately tiny: a trigger plus a pointer. It teaches
  your agent that Autobase exists and where everything true lives — the
  index at [`app.autobase.so/api/v1`](https://app.autobase.so/api/v1) and the
  contract and working practice at
  [`/api/v1/docs`](https://app.autobase.so/api/v1/docs), always fetched
  fresh, never baked in.

## Versioning

The canonical source lives in the platform monorepo and is synced here
automatically on every change. Because the skill is a pointer, it
should almost never change; all real evolution ships server-side with
the platform. The API index reports the published version in its
`skill` block.
