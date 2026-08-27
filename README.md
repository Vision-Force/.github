# Vision Force / .github

The special `.github` repository for the [Vision Force](https://github.com/Vision-Force)
organisation. GitHub treats it differently from a normal repository in two ways.

1. `profile/README.md` renders as the organisation landing page. It is the first
   thing a visitor to the org sees.
2. The community health files here apply org wide. Any Vision Force repository
   without its own `CONTRIBUTING.md`, `SECURITY.md`, `CODE_OF_CONDUCT.md`,
   `SUPPORT.md`, issue templates or pull request template falls back to the copy
   in this repository. A file committed in a project repository always wins.

## Repo map

```
README.md                     this file
BRAND.md                      the design system behind the profile assets
CODE_OF_CONDUCT.md            Contributor Covenant 2.1
CONTRIBUTING.md               how to report and propose
SECURITY.md                   disclosure policy and contact
SUPPORT.md                    where to get help
FUNDING.yml                   sponsor buttons, all keys commented out
PULL_REQUEST_TEMPLATE.md      default pull request body
ISSUE_TEMPLATE/
  config.yml                  blank issues off, contact links
  bug_report.yml              issue form
  feature_request.yml         issue form
profile/
  README.md                   the org landing page
  assets/                     20 hand authored SVGs used by that page
```

Nothing here is generated. The SVGs are written by hand so they can be read,
diffed and corrected like any other source file.

## Editing the profile

`profile/README.md` is public the moment it is pushed, and a few of its failure
modes are invisible locally. [BRAND.md](BRAND.md) carries the full system; these
are the four that bite hardest.

- **The branch must stay `main`.** Every image is referenced by an absolute
  `raw.githubusercontent.com/.../main/...` URL, so on any other branch name the
  whole page renders as broken images.
- **Prefix every id per file.** Gradients, filters, clip paths and masks all
  share a namespace. Two assets using the same id means one steals the other's
  fill. The convention is a short token per file, such as `heroMark` in
  `hero.svg`.
- **SMIL only.** GitHub's sanitiser strips `<style>` blocks and scripts, and the
  image proxy blocks external references, so web fonts and remote assets never
  load. Motion is `<animate>`, `<animateTransform>` and `<animateMotion>`.
- **One font stack, no exceptions.**
  `Segoe UI, -apple-system, Helvetica, Arial, sans-serif`. Glyph widths differ
  between platforms, so never size a box to fit a string.

Two content rules apply to every file in this repository, markdown and SVG alike:
no em dash, en dash, middot or ellipsis character, and no raw URL printed as
visible text. Links are either a designed card or an inline link with real words.

## Renaming the studio

The studio name in the SVGs is live `<text>`, not paths, so it can be swapped
without redrawing anything. It appears in `hero.svg` and `signature.svg`, inside
a `<g>` whose id ends in `Wordmark`, marked with a placeholder comment.

Each of those files holds **two** `<text>` elements: a shadow copy and the live
one two pixels above it. Both carry the same two `<tspan>` children, so a rename
is four tspans per file. Editing only the live copy leaves the old name ghosted
behind the new one.
