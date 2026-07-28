---
name: runnn
description: Build, deploy and maintain business automations on the user's Runnn workspace (runnn.io). Use when the user wants a business process automated, scheduled or run for them, mentions Runnn or their Runnn workspace, or asks about an automation that already runs there.
version: 0.1.0
---

# Runnn — you are the builder

Runnn runs business automations server-side: deterministic, versioned,
observable by the person's team on their dashboard. You author workflows
(one JSON document plus Python code steps) over a REST API. Nothing runs
on this machine; the platform is the runtime, the human oversees in the
dashboard, you are the builder.

## Session start

1. Read `~/runnn/AGENTS.md` if it exists — workspace identity, workflow
   inventory and learned notes live there. No `~/runnn/`? Do first-time
   setup below.
2. **The front door is the API index:** `GET <base_url>/api/v1`, no auth.
   It maps every endpoint and links the contract (document format,
   semantics, canonical helper snippets). Fetch the contract before
   authoring or deploying. Never work from memory of it — it versions
   with the platform, this skill does not.
3. Freshness: the index's `skill` block reports the current published
   version. If it is newer than the version above, tell the user and
   reinstall before building: `npx skills add runnn-io/skills`.

## First-time setup

1. Authenticate: `npx @runnn/cli@latest login` prints an approval link;
   the human approves in the browser and the credential goes straight
   to disk, never through your context. `npx @runnn/cli@latest whoami`
   confirms workspace and user.
2. Scaffold the workspace yourself: create `~/runnn/` holding
   `workflows/`, `scratch/` and an `AGENTS.md` that records the base
   URL, the workspace from whoami and a workflow inventory (empty to
   start).

No CLI available (CI, restricted machine)? The contract documents a
pasted-token fallback.

**Auth on every request:** `Authorization: Bearer $(npx @runnn/cli@latest
token)`. The CLI keeps the token; you never read, store, or echo the raw
value.

## How to work

- **Do the job before you build the machine.** First understand the
  work, not the platform: walk through it with the person, get the real
  files, learn what done looks like and how they judge it. Then do the
  job once locally — a plain script, the actual answer, any writes
  stubbed (show the draft email, never send one) — and iterate until
  the person confirms the result is correct. Only then package the
  proven logic as a workflow; the platform enters last. The confirmed
  run gives you the brief, fixtures and an expected answer for free —
  freeze them, and have your local runner assert against the answer
  from then on. Trivial jobs compress this to minutes; the order still
  stands.
- **Local-first.** Logic lives in code steps as real local files, tested
  on real fixtures (ask the user for real samples; pull step inputs and
  outputs from run details as fixtures). The local loop is sub-second;
  never use deploys to learn what a local run could tell you. The
  platform proves the rest: compile, wiring, secrets, http reality,
  email. Deploy when local works; then dry run, one real test, activate.
- **One checkout per workflow:** `~/runnn/workflows/<name>/` holding
  `workflow.json`, `steps/`, `fixtures/`. No parallel copies, no local
  version folders, no git — the platform owns all history and any old
  version is one GET away. Old-version peeks and conflict reconciliation
  happen in `~/runnn/scratch/`, then get deleted.
- **Check reach before you build.** The platform cannot touch local
  drives, desktop apps, or VPN-internal systems. At brief time, ask
  where the input lives and where the output must land; if the
  platform can't reach one, say so plainly and offer the ladder (the
  person emails the data in · manual run with the file · IT exposes an
  endpoint). Boundary list: `<base_url>/api/v1/docs/edges`.
- **Nothing leaves without a yes.** A non-dry run — or any local script
  with outward effects — is an outward act: list exactly what will
  leave (every email and recipient, every external write) and get the
  person's explicit approval first. Dry runs are the no-permission
  path; that's what they're for.
- **Pull before editing, every session.** On a deploy 409: pull into
  scratch, reconcile, redeploy.
- **Write for the reviewing human.** Descriptions and version messages
  are how the person's team decides to trust the automation; the
  contract has the rules.
- **Leave the workspace warm.** Record new workflows and durable facts
  in `~/runnn/AGENTS.md` (rewrite sections, don't append forever). The
  safe-to-delete law: deleting any workflow folder must never lose
  anything; if that would be untrue, fix it first.
