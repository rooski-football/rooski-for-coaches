# AGENTS.md

The Rooski plug-in for football coaches (`plugins/rooski/`). Read `README.md` for the layout and install steps.

## Build Standard

This repo follows the Rooski Build Standard.

- **Review depends on risk.** The files a change touches set how much review it gets; a file nobody listed gets the middle level. No label, comment or AI verdict lowers it.
- **Anything a coach sees gets a reputation check:** skill text, descriptions, examples and listing copy. Nothing grades or ranks a named coach, school or player; prices come only from the official price list.
- **Locked paths:** `.github/**`, `.claude/**` and the plugin manifests (`.claude-plugin/marketplace.json`, `plugins/*/.claude-plugin/plugin.json`).
- **A version bump is a release.** It reaches coaches, so it happens only in a release PR.
- **Required checks:** the leak scan and `plugin-check`.

Review rules for AI reviewers are in `REVIEW.md`.
