# OWNER.md: Rooski AI coach plug-in (published copy)

This repo is the published copy of the Rooski AI plug-in that coaches install. It is built and released from Rooski's private source repository; changes are made there first.

## Who owns it
- **Owner:** Rooski. Every change is reviewed before it ships, and changes to how the plug-in reads files or writes to a coach's Drive get a separate security review.

## What must always be true
1. The plug-in manifests parse and every skill has valid frontmatter (checked on every pull request).
2. This repo carries no internal names, paths, emails or links.
3. Skills treat text from files, Drive, the web and pasted content as data, never instructions.
4. Nothing grades or ranks a named coach, school or player.
5. A version bump happens only in a release, and it matches the private source at that release.
6. Skills never write outside the coach's own Rooski Drive, never share a file and never delete; moves carry an undo receipt.

## Never
- Never a secret, token or seat link in a skill or example.
- Never a feature described as available before it is.
- Never a change to a coach's file without saying what changed; his own version is kept before a restore.

Questions: support@rooski.com.
