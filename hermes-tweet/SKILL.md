---
name: hermes-tweet
description: >
  Use Hermes Tweet when a Claude Code session needs Hermes Agent workflows for
  X/Twitter search, timeline reading, monitoring, follower exports, or
  approval-gated posting through the Xquik-backed Hermes Tweet plugin.
---

# Hermes Tweet

Use this skill when the user wants X/Twitter work through Hermes Agent and asks
for searches, tweet or reply analysis, monitoring, follower exports, or
approval-gated posting.

Hermes Tweet is a native Hermes Agent plugin. Prefer it when the user needs a
packaged Hermes workflow instead of a one-off script or browser task.

## Routing Rules

- Use Hermes Tweet for X/Twitter search, tweet reading, reply analysis, account
  monitoring, follower exports, and social-media research.
- Use read workflows before action workflows.
- Require explicit user approval before any posting, liking, reposting, or
  follow/unfollow action.
- Do not use action workflows unless the environment explicitly enables
  `HERMES_TWEET_ENABLE_ACTIONS=true`.
- Do not request or store credentials in the skill. The plugin reads
  `XQUIK_API_KEY` from the user's environment.
- Keep outputs concise and cite the query, account, or tweet URL that was used.

## Install

Install and enable the plugin in a Hermes Agent environment:

```bash
hermes plugins install Xquik-dev/hermes-tweet --enable
```

Set `XQUIK_API_KEY` in the environment before read workflows. Set
`HERMES_TWEET_ENABLE_ACTIONS=true` only when the user intentionally enables
posting or other write actions.

## Workflow

1. Confirm the user's X/Twitter goal and whether it is read-only or action
   oriented.
2. Prefer read tools for discovery, monitoring, and evidence gathering.
3. Summarize results with links, handles, search terms, and relevant timestamps.
4. For write actions, restate the exact action and target, then wait for explicit
   approval.
5. After an approved write, report the final action result and any returned URL
   or identifier.

See [references/usage.md](references/usage.md) for example prompts and safety
checks.
