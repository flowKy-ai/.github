<div align="center">

# FlowKy

### The sidekick for your coding agent.

Your agent forgets your codebase between sessions. It rewrites the helper you wrote last week, retries the command that just failed, and spends your tokens relearning a project it already knew yesterday.

**We give it memory, guardrails, and a map that tells you when it has gone stale.**

<br>

[![Docs and API](https://img.shields.io/badge/Docs%20%26%20API-read-F0620F?style=for-the-badge)](https://github.com/flowKy-ai/flowky/tree/main/docs/api)
[![Website starter](https://img.shields.io/badge/Website%20starter-MIT-F0620F?style=for-the-badge)](https://github.com/flowKy-ai/flowky/tree/main/starter)
[![Tips](https://img.shields.io/badge/Tips-read-F0620F?style=for-the-badge)](https://github.com/flowKy-ai/flowky/blob/main/TIPS.md)

</div>

---

## Works with the agent you already pay for

Claude Code · Cursor · Copilot · Gemini CLI · Windsurf · Cline

We do not replace them. We sit underneath and stop them repeating themselves.

<br>

|  | What it does |
|---|---|
| **Stops duplicate code** | Every function and class is indexed. When your agent starts writing one that already exists, it gets the file and the line — before the write lands. |
| **Breaks the retry loop** | Third time the same command has failed, it is interrupted and shown the error it kept skipping past. |
| **Keeps the map honest** | The project map records the commit it was built from and reports how far it has drifted. A stale map that reads as confident is worse than no map at all. |
| **Costs nothing until used** | Your tree, symbols and import graph live in a skill opened on demand. Sessions that never need them pay zero tokens for them. |
| **Your keys, your machine** | OpenAI, Anthropic, Google, or anything OpenAI-compatible. No inference request passes through us. |

---

## Open source

**[`flowky`](https://github.com/flowKy-ai/flowky)** — everything public, MIT licensed:

- **[API reference](https://github.com/flowKy-ai/flowky/tree/main/docs/api)** — endpoints, auth, rate limits, and the client mistakes worth avoiding
- **[Website starter](https://github.com/flowKy-ai/flowky/tree/main/starter)** — zero dependencies, one readable file, scaffolds a site that ships with agent config already in place
- **[Tips](https://github.com/flowKy-ai/flowky/blob/main/TIPS.md)** — short, checkable things that make a measurable difference

The extension and web application are closed source.

---

## Security

Report privately: **Security → Report a vulnerability** on any repository.

Never open a public issue for a vulnerability. First response within 3 working days, and we credit reporters unless they prefer otherwise. Good-faith research under [our policy](https://github.com/flowKy-ai/.github/blob/main/.github/SECURITY.md) will not be pursued.

FlowKy is bring-your-own-key. Provider credentials stay in the user's editor. If any part of the product appears to send a key anywhere, treat that as a vulnerability.

---

<div align="center">

### Elsewhere

[X](https://x.com/flowky_ai) · [LinkedIn](https://www.linkedin.com/company/flowky-ai/) · [Instagram](https://www.instagram.com/flowky.ai/) · [TikTok](https://www.tiktok.com/@flowky.ai)

<sub>Paris, France · <a href="https://github.com/flowKy-ai/.github/blob/main/.github/CODE_OF_CONDUCT.md">Code of conduct</a></sub>

</div>
