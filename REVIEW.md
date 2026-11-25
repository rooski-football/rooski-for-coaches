# REVIEW.md

Rules for any AI reviewer on a pull request here. The repo follows the Rooski Build Standard (see `AGENTS.md`); the risk of the files a change touches decides how much review it gets.

## Always check

- **No secret in a PR job.** No workflow step may read a secret, token or key, and no file may contain one.
- **Nothing grades or ranks a named coach, school or player.** Run the Reputation Check on anything a coach sees.
- **Prices come only from the official price list.** Flag any dollar figure, discount or plan name that is not copied from it.
- **No version bump outside a release PR.** A change to a `version` field in `plugin.json` or the marketplace file is a release.
- **Locked paths** (`.github/**`, `.claude/**`, the plugin manifests): flag any edit that loosens a check, adds a permission or pins an action to a tag instead of a full SHA.

## Keep it quiet

- At most five comments per review.
- Security first, then correctness; skip style.
- Never repeat a finding the author already dismissed.
