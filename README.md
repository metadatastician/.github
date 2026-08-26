<!--
SPDX-License-Identifier: CC-BY-SA-4.0
SPDX-FileCopyrightText: 2026 Jonathan D.A. Jewell <sudo@metadatastician.art>
-->

# `.github` — organisation defaults

This repository supplies **default community-health files** for every repository in
**The Metadatastician**, and the content of the organisation's public profile page.

## What each file does

| Path | Effect |
|---|---|
| `profile/README.md` | Renders on <https://github.com/metadatastician> |
| `CODE_OF_CONDUCT.md` | Default for repos without their own |
| `CONTRIBUTING.md` | ” |
| `SECURITY.md` | ” |
| `SUPPORT.md` | ” |
| `GOVERNANCE.md` | ” |
| `PULL_REQUEST_TEMPLATE.md` | ” |
| `.github/ISSUE_TEMPLATE/` | Default issue forms |
| `.github/DISCUSSION_TEMPLATE/` | Default discussion forms |

## How overriding works

- **Single files** override individually. A repo with its own `SECURITY.md` uses it and
  still inherits everything else.
- **Template folders are all-or-nothing.** A repo with any file in its own
  `.github/ISSUE_TEMPLATE/` inherits *none* of the forms here.
- This repository must stay **public** for issue and discussion templates to apply
  org-wide.

## What does NOT inherit

Worth stating plainly, because it is easy to assume otherwise:

- **`LICENSE`** — GitHub does not support a default licence. Every repository needs its own.
- **`CODEOWNERS`** — only ever governs the repository it lives in.
- **Workflows** — a workflow in this repo runs *only in this repo*. It is not propagated.
  Organisation-wide CI is done by calling a reusable workflow explicitly, not by placing
  one here. This repository deliberately ships **no workflows** to avoid implying otherwise.
- **`dependabot.yml`** — must exist per repository.

## Licensing

Prose here is `CC-BY-SA-4.0`. See [`GOVERNANCE.md`](GOVERNANCE.md) for how licence
decisions are made — in short, manually and never by automation.
