<div align="center">

<img src="https://raw.githubusercontent.com/flowKy-ai/.github/main/profile/assets/banner.svg" alt="FlowKy — the sidekick for your coding agent" width="100%">

<br><br>

**Your agent forgets your codebase between sessions.**

It rewrites the helper you wrote last week. It retries the command that just failed. It spends your tokens relearning a project it already knew yesterday.

We give it memory, guardrails, and a map that tells you when it has gone stale.

<br>

[![Docs and API](https://img.shields.io/badge/docs%20%26%20API-read-F0620F?style=flat-square)](https://github.com/flowKy-ai/flowky/tree/main/docs/api)
[![Starter](https://img.shields.io/badge/website%20starter-MIT-F0620F?style=flat-square)](https://github.com/flowKy-ai/flowky/tree/main/starter)
[![Tips](https://img.shields.io/badge/tips-25%20guides-F0620F?style=flat-square)](https://github.com/flowKy-ai/flowky/blob/main/TIPS.md)
[![Discussions](https://img.shields.io/badge/discussions-join-F0620F?style=flat-square)](https://github.com/flowKy-ai/flowky/discussions)

</div>

---

## See it work

Not a mockup. This is the guard catching a real duplicate, in the codebase that runs our own website:

```console
$ your agent writes safeRedirectPath()

FlowKy: this symbol already exists in this codebase.
  • safeRedirectPath — already defined in src/lib/safe-redirect.ts:14

Import and reuse the existing definition, or extend it.
```

It **asks**, it does not block. Overloads and re-exports are legitimate, and a hard block produces false positives that get the hook switched off within a week.

---

## Why a hook and not a prompt

This is the whole product in one distinction, and it is worth stating plainly because most tooling in this space gets it wrong.

|  | Instructions in a context file | A lifecycle hook |
|---|---|---|
| When it applies | While the model happens to remember | Every single time, without exception |
| Survives a long session | Degrades as the window fills | Unaffected |
| Survives compaction | Only if unscoped and at the root | Unaffected |
| Enforcement | Advisory | Actual |

Anything that **must** hold belongs in a hook. Anything contextual belongs in a rule or a skill. Writing "never recreate an existing function" in a config file and expecting compliance is the mistake this product exists to fix.

---

## What we install

```
your-project/
├── CLAUDE.md                     # gotchas only, hard-capped under 200 lines
├── .claude/
│   ├── rules/
│   │   ├── conventions.md        # unscoped: survives compaction
│   │   └── api.md                # paths-scoped: loads on matching files only
│   ├── skills/project-map/       # tree, symbols, imports — opened on demand
│   └── settings.json             # hook wiring
└── .flowky/
    ├── index/symbols.tsv         # what the write guard queries
    └── hooks/flowky-guard.mjs    # Node, so macOS, Linux and Windows alike
```

Three decisions in that layout, each one deliberate:

**The directory tree is not in `CLAUDE.md`.** Claude Code's own `/doctor` strips directory layouts from context files, because the model can derive them and a written-down tree goes stale on the next refactor. It lives in a skill, where it costs nothing until something opens it.

**Absolute rules are unscoped.** Path-scoped rules are dropped on compaction and only return when a matching file is read. A "never commit secrets" rule in a scoped file stops applying halfway through a session — silently.

**The hooks are Node, not shell.** A `.sh` is dead on Windows without Git Bash; a `.ps1` is dead everywhere else. One runtime, three platforms, no second-class citizen.

---

## Works with what you already pay for

Claude Code · Cursor · Copilot · Gemini CLI · Windsurf · Cline

We do not replace them. We sit underneath and stop them repeating themselves.

|  |  |
|---|---|
| **Stops duplicate code** | Every function and class indexed. The agent gets the file and line before the write lands. |
| **Breaks the retry loop** | Third identical failure, interrupted, shown the error it kept skipping past. |
| **Keeps the map honest** | Records the commit it was built from and reports the drift. A stale map that reads as confident is worse than no map. |
| **Costs nothing until used** | Sessions that never open the map pay zero tokens for it. |
| **Your keys, your machine** | OpenAI, Anthropic, Google, or anything OpenAI-compatible. No inference request passes through us. |

---

## Open source

Everything in **[`flowky`](https://github.com/flowKy-ai/flowky)** is MIT.

| | |
|---|---|
| **[API reference](https://github.com/flowKy-ai/flowky/tree/main/docs/api)** | Endpoints, auth, rate limits — and the client mistakes worth avoiding, including the one that silently downgrades a paying user to the free tier |
| **[Website starter](https://github.com/flowKy-ai/flowky/tree/main/starter)** | Zero dependencies, one readable file. Scaffolds a site that ships with agent config already in place, because config written on day one is short and true, and config written on day ninety is archaeology |
| **[Tips](https://github.com/flowKy-ai/flowky/blob/main/TIPS.md)** | Short and checkable. "Put your build command in CLAUDE.md" beats "maintain good documentation" |

The extension and web application are closed source.

---

## How this organisation is run

Stated because it is checkable, and because a policy nobody can verify is decoration.

- **Every repository requires a review** before merging to the default branch, including the private ones. No force-pushes, no branch deletion, linear history.
- **`GITHUB_TOKEN` is read-only by default** in every repository, and workflows cannot approve their own pull requests. The historical default was write-all, which is the mechanism behind most Actions supply-chain incidents.
- **Secret scanning with push protection** on public repositories — it blocks a credential before it enters history, where removing it means a rewrite and a rotation.
- **Superseded repositories are archived, not deleted.** They are read-only, so nobody mistakes one for live, and the history stays recoverable.
- **No contact address is published that we have not verified.** A security policy routing reports into a void is worse than one that only offers the form that works.

---

## Security

Report privately: **Security → Report a vulnerability** on any repository here. Never open a public issue for a vulnerability.

First response within 3 working days. We credit reporters unless they prefer otherwise, and good-faith research under [our policy](https://github.com/flowKy-ai/.github/blob/main/.github/SECURITY.md) will not be pursued.

FlowKy is bring-your-own-key: provider credentials stay in the user's editor. If any part of the product appears to send a key anywhere, treat that as a vulnerability.

---

<div align="center">

[X](https://x.com/flowky_ai) · [LinkedIn](https://www.linkedin.com/company/flowky-ai/) · [Instagram](https://www.instagram.com/flowky.ai/) · [TikTok](https://www.tiktok.com/@flowky.ai)

<sub>Paris, France · <a href="https://github.com/flowKy-ai/.github/blob/main/.github/CODE_OF_CONDUCT.md">Code of conduct</a> · <a href="https://github.com/flowKy-ai/flowky/blob/main/CONTRIBUTING.md">Contributing</a></sub>

</div>
