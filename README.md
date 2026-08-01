# .github

Organisation-wide defaults for [flowKy-ai](https://github.com/flowKy-ai).

GitHub reads this repository specially: the profile page and the community
health files here apply to every repository in the organisation that does not
define its own.

```
profile/README.md          the organisation landing page at github.com/flowKy-ai
profile/assets/            avatar, banner and social preview, SVG sources + PNGs
.github/SECURITY.md        vulnerability reporting policy — inherited org-wide
.github/CODE_OF_CONDUCT.md inherited org-wide
```

## Editing

**`profile/README.md` is the front door.** It is what someone sees before they
see any code, so it demonstrates the practices it describes rather than
describing them — the hook-versus-prompt distinction, the installed layout with
the reasoning behind each decision, and real command output rather than a
mockup.

Images are referenced by absolute `raw.githubusercontent.com` URL and point at
the **PNG**, not the SVG. Relative paths resolve inconsistently in a profile
README, and SVG through GitHub's image proxy renders unreliably — a broken
header is a poor first impression.

**Brand assets: edit the `.svg`, never the `.png`.** The PNGs are rendered from
the SVGs at exact pixel sizes; [`profile/assets/README.md`](profile/assets/README.md)
has the command and the reasoning behind each design constraint.

## What is deliberately absent

There is no `dependabot.yml`. Advisory alerts stay on at the organisation
level — those are a match against GitHub's advisory database and nothing
replaces that feed — but the pull requests come from
[FlowKy Bot](https://github.com/flowKy-ai/flowky/blob/main/.github/scripts/flowky-bot.mjs)
instead, already verified against the build. Two bots filing for one advisory is
how a security queue starts getting ignored.

No contact email is published anywhere here that has not been verified. A
security policy routing reports into a void is worse than one that only offers
the form that works.
