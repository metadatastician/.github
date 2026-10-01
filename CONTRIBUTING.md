<!--
SPDX-License-Identifier: CC-BY-SA-4.0
SPDX-FileCopyrightText: 2026 Jonathan D.A. Jewell <sudo@metadatastician.art>
-->

# Contributing

Default contribution guide for **The Metadatastician**. A repository with its own
`CONTRIBUTING` overrides this.

## Before a large change

Open an issue or a discussion first. This estate is maintained by one person, and a large
unsolicited pull request is more likely to sit unreviewed than a conversation is.

Small, obvious fixes — a typo, a broken link, a clearly wrong path — just send them.

## Toolchains vary by repository

There is no single build system here. This organisation spans formally-verified container
infrastructure, agent tooling, IETF-track specifications and games, and each repository
declares its own toolchain. **Read the repository's own README and `Justfile` first.**

Many repositories use [`just`](https://github.com/casey/just) as a task runner, so
`just --list` is usually a good first command.

## Commits

- **Sign your commits** (`git commit -S`). Several repositories enforce verified
  signatures at the branch ruleset, so unsigned commits will be refused outright.
- Write a subject line that says what changed and why. If the reason is interesting, put
  it in the body — future readers benefit far more than reviewers do.
- Prefer honest commit messages over flattering ones. "Fixes the symptom, cause unknown"
  is more useful than an implied fix that isn't one.

## Licensing

New files need the right SPDX header at authoring time:

- **Code, config, scripts** — `MPL-2.0`
- **Prose and documentation** — `CC-BY-SA-4.0`
- **Repositories that are AGPL** — games, and projects co-developed with family — use
  `AGPL-3.0-or-later` for code. Check the repository's own `LICENSE`; it is authoritative.

**Do not change the licence of an existing file.** Relicensing is a manual, owner-only
decision and is never done by sweep, script, or automation.

## Documentation

Prose in this estate is generally AsciiDoc (`.adoc`). The exception is the
community-health set — `README`, `SECURITY`, `CONTRIBUTING`, `CODE_OF_CONDUCT` and
friends — which must be Markdown, because GitHub does not recognise `.adoc` for those.

## Claims should match reality

If a README says a thing works, it should work. A pull request that corrects an
overstatement is as welcome as one that adds a feature.

## Signed commits

Every commit that reaches the default branch must be signed; a ruleset refuses
unsigned pushes. Estate policy:
[SIGNING-POLICY](https://github.com/hyperpolymath/standards/blob/main/docs/SIGNING-POLICY.adoc).

- **People and interactive agents** sign with an SSH key registered on GitHub
  as a *signing* key (`gpg.format=ssh`, `user.signingkey=<key>.pub`,
  `commit.gpgsign=true`). The committer email must be verified on that account.
- **Apps, bots and workflows** never `git push` local commits. They write
  through the API (`createCommitOnBranch` or the estate `signed-push` action)
  so that GitHub signs each commit.
- Merge PRs with **squash**. The ruleset checks every commit on the PR branch,
  not just the result, so one unsigned commit blocks the merge. Re-create such a
  branch with signed commits (`git cherry-pick -S`) and open a new PR.
  Rebase-merge replays commits unsigned and is disabled.
