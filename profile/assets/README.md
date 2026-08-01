# Brand assets

Each mark exists twice: an `.svg` that is the source of truth, and a `.png`
rendered from it at exact pixel dimensions. Edit the SVG, never the PNG.

| File | Size | Where it goes |
|---|---|---|
| `avatar.png` | 512×512 | Organisation avatar, and the same file for the GitHub App if one is registered |
| `social-preview.png` | 1280×640 | Each repository's social preview — the card shown when a link is posted to Slack, X or LinkedIn |
| `banner.png` | 1280×320 | Header of the organisation profile README |

## Re-rendering

The PNGs are produced by rasterising the SVGs in headless Chrome, so text
renders with real font metrics rather than being traced to paths:

```bash
for a in avatar:512,512 banner:1280,320 social-preview:1280,640; do
  name=${a%%:*}; size=${a##*:}
  { printf '<!doctype html><meta charset="utf-8">'
    printf '<style>html,body{margin:0;padding:0;overflow:hidden}svg{display:block}</style>'
    cat "$name.svg"
  } > "/tmp/$name.html"
  chrome --headless=new --disable-gpu --hide-scrollbars \
         --force-device-scale-factor=1 \
         --screenshot="$name.png" --window-size="$size" "file:///tmp/$name.html"
done
```

The HTML wrapper is not optional. Point Chrome at an `.svg` directly and it
centres the image in the viewport with its own margins, which pads the avatar
off-centre.

## Design constraints

**The avatar has no corner radius.** GitHub applies its own rounding, and a
radius baked in here shows as a dark ring once it is masked a second time.

**The ears hang.** Upright ears on a round head read as a bear — the first
version of this file made exactly that mistake. Hanging ears in a darker tone
are what says *dog* at 32px, which is the size that actually has to work.

**The avatar drops the collar tag.** At sidebar scale it is three dark pixels
in the middle of a light shape. Detail that turns to mud costs legibility and
returns nothing.

**Text uses a system font stack, not a webfont.** GitHub will not load a font
for an image, so anything else silently falls back to something unintended.

## Uploading

None of these can be set through the API — GitHub gates all three behind the
web UI, so they are manual by necessity rather than oversight.

- **Organisation avatar** — Settings → Profile → upload `avatar.png`
- **Repository social preview** — per repo, Settings → General → Social preview → upload `social-preview.png`
