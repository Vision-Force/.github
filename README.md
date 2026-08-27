# Vision Force / .github

This is the special `.github` repository for the [Vision Force](https://github.com/Vision-Force)
organisation. GitHub treats it differently from a normal repository, in two ways.

1. `profile/README.md` is rendered as the organisation landing page at
   <https://github.com/Vision-Force>. It is the first thing a visitor sees.
2. Every community health file stored here applies org wide. Any Vision Force
   repository that does not carry its own `CONTRIBUTING.md`, `SECURITY.md`,
   `CODE_OF_CONDUCT.md`, `SUPPORT.md`, issue templates or pull request template
   falls back to the copy in this repository. A file committed in a project
   repository always wins over the copy here.

Vision Force Studio is a fan team of community volunteers, having a studio as a
hobby project. The studio runs a public development roadmap for Rocket Racing
Revive at <https://visionforceofficial.com>.

## Repo map

```
.github/
  README.md                     this file, for people reading the repo
  BRAND.md                      colours, type, logo rules, SVG conventions
  CODE_OF_CONDUCT.md            Contributor Covenant 2.1, org wide
  CONTRIBUTING.md               how to report and propose, org wide
  SECURITY.md                   disclosure policy and contact
  SUPPORT.md                    where to get help
  FUNDING.yml                   sponsor buttons, all keys commented out
  PULL_REQUEST_TEMPLATE.md      default PR body, org wide
  ISSUE_TEMPLATE/
    config.yml                  blank issues off, contact links
    bug_report.yml              issue form
    feature_request.yml         issue form
  profile/
    README.md                   THE ORG LANDING PAGE
  assets/                       hand authored SVGs used by profile/README.md
```

Nothing here is generated. The SVGs in `assets/` are written by hand, so they can
be read, diffed and corrected like any other source file.

## Editing the profile safely

`profile/README.md` is public the moment it is pushed. A few rules keep it from
breaking in ways that are hard to see locally.

- **Per file id prefix.** GitHub inlines several SVGs into one page. Every `id`,
  gradient, filter, clip path and mask must be prefixed with a short token unique
  to its file, for example `mer-glow` inside `meridian.svg`. Two files sharing an
  id means one silently steals the other's fill.
- **SMIL only.** CSS animation and `<style>` blocks are stripped by GitHub's
  sanitiser. Motion has to be SMIL, so `<animate>`, `<animateTransform>` and
  `<animateMotion>`. No scripts, no external references, no web fonts.
- **Safe font stack.** Use only fonts that exist on the reader's machine. The
  stack in use is a system sans stack for prose and a plain monospace stack for
  code. A font that fails to load reflows the whole SVG, so never rely on one
  family alone.
- **Banned characters.** No em dash, no en dash in prose, no middot, no ellipsis
  character. Use commas, colons, full stops or a slash. This applies to the SVG
  text nodes too, where a missing glyph shows as a box.
- **Wordmark placeholder.** The wordmark in `assets/` is a placeholder built from
  live text. When the real lettering lands, replace that one file and keep its
  `viewBox` and file name, so no other file needs editing.

Read [BRAND.md](BRAND.md) before changing any colour, accent or logo. It carries
the accents for each project and the rules for using them.

## Links

- Website: <https://visionforceofficial.com>
- Status: <https://status.visionforceofficial.com>
- Discord: <https://discord.gg/ABmyD3NRGV>
- YouTube: <https://www.youtube.com/@VaeloraVelocity>
- TikTok: <https://www.tiktok.com/@vaeloravelocity>
- Email: contact@visionforceofficial.com

Vision Force Studio is not affiliated with or endorsed by Epic Games. Fortnite
and Unreal are trademarks of Epic Games, Inc.
