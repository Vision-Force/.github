# Vision Force, organisation design system

> The visual system behind this organisation profile and every SVG in `profile/assets/`.
> The studio name in the SVGs is a placeholder. See "Renaming the studio" below.

---

> # Vision Force org profile: design system v2 (CORRECTION PASS)
>
> This document is the single source of truth for the six implementing agents. It replaces the rejected
> first attempt entirely. Where this document and any earlier note disagree, this document wins.
>
> ---
>
> ## 0. The five laws (the user's own rejection, turned into rules)
>
> 1. **The plus mark is COPIED, not evolved.** One `<path>`, horizontal subpath then vertical subpath,
>    `stroke-linecap="round"`, no fill. Exact form in section 5 and in `plusRecipe`. Anyone who "improves"
>    the motif has failed the task.
> 2. **Everything moves.** Three or four orbiting parallax layers, twinkle, a per plus orbit on roughly one
>    mark in three, a few scale breathers, charge rails where the ornament calls for it. A static asset is a
>    rejected asset. **A moving highlight is not part of this system.** No scan sweep, no shine, no gloss, no
>    sheen crossing a card. It was built once, the studio owner rejected it, and it was stripped out of every
>    asset. Do not put it back.
> 3. **Brutal, black, LEFT ALIGNED.** Ground is near black `#050506`. Content starts at a hard left margin.
>    The right side carries the imagery and the density. Nothing is centred except inside the small square
>    `mark.svg`.
> 4. **Banned characters are banned everywhere.** See section 1. This is checked mechanically before hand-off.
> 5. **The logo is real.** Copy the winged bolt path data verbatim. Never draw a substitute mark.
>
> ---
>
> ## 1. BANNED CHARACTERS AND BANNED CONTENT (hard fail)
>
> These must not appear in any `.svg`, any `.md`, any comment, any `alt` string, any commit message:
>
> | Codepoint | Character | Instead use |
> |---|---|---|
> | U+2014 | em dash | a colon, a full stop, a comma, or restructure the sentence |
> | U+2013 | en dash | a plain hyphen for numeric ranges only, never in prose |
> | U+00B7 | middot / interpunct | generous space, a real `<line>` hairline, or a slash |
> | U+2022 | bullet dot | a markdown list, or a drawn `<rect>` accent rule |
> | U+2026 | ellipsis | end the sentence |
> | U+2018 U+2019 U+201C U+201D | curly quotes | straight quotes |
>
> **Verification command every implementing agent runs before hand-off:**
>
> ```
> grep -RPn "[\x{2014}\x{2013}\x{00B7}\x{2022}\x{2026}\x{2018}\x{2019}\x{201C}\x{201D}]" profile/
> ```
>
> Zero hits required. Any hit is a rejected file.
>
> **Banned content**, not just characters:
> - No tiny grey footer line at the end of an asset or at the end of the README. If it must be said, it gets
>   a heading and normal body size in its own section.
> - No project cards, no project blurbs inside artwork, no tag chips, no status chips, no "01 / 04" counters.
> - No fake stars, no fake download counts, no CI badges, no links to repos that do not exist.
> - No shields.io badges anywhere in this set. The badge look belongs to the other repo, not to the studio
>   front door.
>
> ---
>
> ## 2. LAYOUT: brutal and left aligned
>
> The single biggest reason the first attempt failed to read as the studio site is that it was centred.
> It is not centred.
>
> - **Left margin is a constant per canvas family.**
>   - 1600 wide: content starts at **x = 96**
>   - 1200 wide: content starts at **x = 72**, band content at **x = 64**
>   - 880 wide: the divider inset stays the user's own **60**
> - **Right third is imagery.** The winged bolt, the dot pattern, the brightest plus layer, the ghost mark.
>   Type never crosses into it.
> - **A left accent bar** (`<rect x="0" y="0" width="5" height="{H}">` filled with the accent gradient, drawn
>   INSIDE the clip so it inherits the corner radius) opens `hero.svg` and every section band. This is the
>   one shared structural tell across the set.
> - **Corners:** cards and bands `rx="14"` to `rx="18"`. `mark.svg` `rx="28"`. Never square, never pill except
>   for actual pill chips.
> - **Borders are hairline, 1px, always.** `#1b2742` normal, `#232f4a` raised. Never 2px.
> - **Frame discipline, copied from the UEFN set:** background rect first, all content inside
>   `<g clip-path="url(#{P}Clip)">` where the clip is the same rect, then the same rect drawn AGAIN last as
>   `fill="none" stroke="#1b2742" stroke-width="1"` so the hairline sits over the clipped art.
>
> ---
>
> ## 3. PALETTE
>
> **Ground and surface**
>
> | Token | Hex | Use |
> |---|---|---|
> | ground | `#050506` | page ground of every asset. Brutal near black. Almost no blue. |
> | studio surface | `#08090a` | `mark.svg` square, raised blocks on black |
> | deep panel | `#0a0e17` | inset panels |
> | card base | `#0c1322` | pill chips, inner chips |
> | card gradient | `#0d1a2e` to `#0a1425` | the `{P}Bg` gradient, kept from the UEFN set, used only INSIDE surfaces |
> | raised panel | `#111826` | rare |
>
> **Ink**
>
> | Token | Hex | Use |
> |---|---|---|
> | display white | `#f4f6fb` | the white half of every two tone headline |
> | bright ink | `#e8eefb` | chip labels, the rarest brightest plusses |
> | body | `#c3cad8` | primary body copy |
> | body dim | `#a8b0c0` | secondary body copy |
> | eyebrow grey | `#7d8798` | every wide tracked caps label |
> | dash rule | `#4a6f96` | the divider hairline, `stroke-dasharray="1 7"`, opacity 0.55 |
>
> **Accent, with an explicit hierarchy**
>
> | Token | Hex | Rank |
> |---|---|---|
> | **violet** | `#a855f7` | **HERO ACCENT.** The studio colour. Used generously. |
> | violet blue | `#8b5cff` | violet's companion in the plus field |
> | Reality Cross | `#a02bfe` | project accent, README text only |
> | cyan | `#47d1ff` | secondary accent, and the Meridian / server colour |
> | blue | `#3b82f6` | plus field |
> | deep blue | `#1273ea` | gradient end only |
> | steel blue | `#6ea8dc` | dim plusses |
> | green | `#34d399` | sparing accent surprise, roughly 1 plus in 20 |
> | Vaelora Velocity | `#ff2e4d` | project accent, README text only |
> | amber | `#ffb83d` | in progress marker, README text only |
> | shipped green | `#38f0a0` | shipped marker, README text only |
>
> **Rule:** violet leads. Across the whole asset set the violet family (`#a855f7` plus `#8b5cff`) should be
> roughly 40 percent of coloured marks, cyan roughly 25, blue 15, steel 10, green 5, near white 2, deep blue 3.
> The ONE exception is `section-server.svg`, which flips to cyan lead because it is the Meridian band.
>
> ---
>
> ## 4. TYPE
>
> One stack everywhere. No web fonts can load inside an `<img>` embedded SVG, so a named-font gamble is a
> broken asset:
>
> ```
> font-family="Segoe UI, -apple-system, BlinkMacSystemFont, Noto Sans, DejaVu Sans, Helvetica, Arial, sans-serif"
> ```
>
> Caps labels use the SAME stack with heavy tracking. No monospace family is declared anywhere in this set.
>
> | Role | Size | Weight | Letter spacing | Fill |
> |---|---|---|---|---|
> | display (hero) | 92 | 800 | -2 | two tone, see section 6 |
> | display (band) | 40 | 800 | -1 | two tone |
> | title (signature) | 40 | 800 | -1 | two tone |
> | column value | 26 | 700 | -0.3 | `#f4f6fb` |
> | statement title | 22 | 700 | -0.3 | `#f4f6fb` |
> | sub | 17 | 400 | 0 | `#c3cad8` |
> | body | 15 | 400 | 0 | `#a8b0c0` |
> | chip label | 13 | 600 | 0.4 | `#e8eefb` |
> | eyebrow | 10.5 to 11 | 600 | 3.4 to 4.6 | `#7d8798`, ALWAYS uppercase |
>
> - Display type is BIG relative to its canvas. Be bold. The hero wordmark is 92px on a 480 tall canvas.
> - Tracking is bidirectional and extreme at both ends: negative on display, strongly positive on eyebrows,
>   almost nothing in between.
> - Text stays live `<text>`, never converted to paths, because the wordmark must remain swappable
>   (section 7). Use `text-anchor="start"` for all left aligned copy, which is nearly all of it.
> - Headings carry no trailing full stop. Body sentences do. Statement titles in `values-band.svg` are the one
>   deliberate exception: they are two beat lines and the period is the point.
>
> ---
>
> ## 5. THE PLUS MOTIF (copied verbatim, never evolved)
>
> ```
> <path d="M{cx-h} {cy}H{cx+h}M{cx} {cy-h}V{cy+h}" stroke="{c}" stroke-width="{w}"
>       stroke-linecap="round" opacity="{o}"/>
> ```
>
> - ONE path element per plus. Horizontal first, vertical second, same `d`. Never two paths.
> - half length `h`: **3.0 to 5.1**
> - `stroke-width` `w`: **1.6 to 2.8**
> - `opacity` `o`: **0.23 to 0.90**
> - `stroke-linecap="round"` is mandatory. No fill. No `rx`. No square caps. No `stroke-linejoin`.
> - **Bigger means brighter and thicker.** Keep the coupling: `h` 3.0-3.4 pairs with `w` 1.6-1.8 and `o`
>   0.23-0.42; `h` 3.5-4.2 pairs with `w` 1.9-2.2 and `o` 0.40-0.62; `h` 4.3-5.1 pairs with `w` 2.4-2.8 and
>   `o` 0.60-0.90.
> - Coordinates carry **one decimal place**, like the user's own generated files. Never integers on every mark.
> - **Never on a grid.** Never evenly spaced. Cluster two or three, then leave a gap. Irregular by hand.
> - **Type exclusion zone:** no plus within 40px of a display glyph box, no plus within 24px of body copy.
>   The corners and the right third get busy; the type stays clean.
>
> Colours, in the weighting given in section 3: `#a855f7`, `#8b5cff`, `#47d1ff`, `#3b82f6`, `#6ea8dc`,
> `#34d399`, `#e8eefb`, `#1273ea`.
>
> Full copy-paste construction, including the three animated layer wrappers and the density table, is in
> `plusRecipe`. Follow it literally.
>
> ---
>
> ## 6. THE TWO TONE DISPLAY HEADLINE (the site's signature)
>
> Every display headline in this set is a `<text>` with TWO `<tspan>` children. The first word is near white
> `#f4f6fb`. The second word is NOT a flat accent hex: it is filled with `url(#{P}Word)`, the live wordmark
> gradient, so the accent shifts through the violet family and back. The server band is the one file whose
> `{P}Word` leads cyan, exactly as the palette hierarchy in section 3 says it should.
>
> The headline ships as TWO stacked `<text>` elements. The lower one, drawn first, is a solid `#05070b` copy
> sitting 2px below: it separates the display type from the plus field without a blur or a drop shadow filter.
> The upper one carries the colour. Both copies carry the same two tspans, so a rename is a four word edit.
>
> ```xml
> <text x="64" y="92" font-family="Segoe UI, -apple-system, Helvetica, Arial, sans-serif"
>       font-size="46" font-weight="800" letter-spacing="-1.8" fill="#05070b"><tspan>The</tspan><tspan dx="13">Studio</tspan></text>
> <text x="64" y="90" font-family="Segoe UI, -apple-system, Helvetica, Arial, sans-serif"
>       font-size="46" font-weight="800" letter-spacing="-1.8"><tspan fill="#f4f6fb">The</tspan><tspan dx="13" fill="url(#stWord)">Studio</tspan></text>
> ```
>
> Use `dx` for the word gap, never a trailing space inside a tspan: XML whitespace collapsing makes a trailing
> space unreliable across renderers. `dx="13"` at 40px, `dx="22"` at 92px.
>
> ---
>
> ## 7. WORDMARK PLACEHOLDER RULE (the studio may be renamed)
>
> Wherever the studio NAME appears in an SVG:
>
> - render it as live `<text>`, never as paths,
> - put it inside its own `<g id="{file}Wordmark">` containing **nothing else**,
> - immediately above that group, this comment line, exactly:
>
> ```xml
> <!-- PLACEHOLDER STUDIO NAME: swap the two tspans below on rebrand -->
> ```
>
> - build it from the stacked pair of section 6: the `#05070b` shadow copy, then the live copy, each with TWO
>   `<tspan>` children, the first white and the second filled `url(#{P}Word)`.
>
> That is what is really in the files. `hero.svg` holds
> `<!-- PLACEHOLDER STUDIO NAME: swap the two tspans below on rebrand -->` and then `<g id="heroWordmark">`
> containing exactly two `<text>` elements and nothing else: `x="96" y="246"` at `fill="#05070b"`, then
> `x="96" y="244"` with `<tspan fill="#f4f6fb">Vision</tspan><tspan dx="14" fill="url(#heroWord)">Force</tspan>`.
> Both are `font-size="120" font-weight="800" letter-spacing="-2.5"`. `signature.svg` is the same shape at
> `x="292" y="124"` and `y="122"`, `font-size="56"`, `letter-spacing="-2.2"`, `dx="14"`.
>
> So a rename touches FOUR tspans per file, not two: the shadow copy and the live copy each carry the pair.
> Edit both, or the rebrand ships with the old name ghosted 2px behind the new one.
>
> Only two assets carry the name: `hero.svg` (`heroWordmark`) and `signature.svg` (`sigWordmark`). The section
> bands say "The Studio", "The Work", "The Server", "The Community", "The Method" and never the studio name.
> `mark.svg` carries no text at all. **Do not put the studio name in a ghost layer, a watermark, or an `alt`
> string that would need editing in more than one place.**
>
> ---
>
> ## 8. THE REAL LOGO: embedding rule
>
> The winged lightning bolt through an orbital ring with an eye aperture is a real vector mark with a
> `viewBox="0 0 500 364"`. **The PATH GEOMETRY IS COPIED VERBATIM from the studio's own vector file.** Copy the
> two mask definitions and the two `<path>` elements across unchanged. Do not redraw, simplify, round, re-fit,
> or "clean up" the path data. Do not draw chevrons. **Recolouring is the only change ever permitted to the
> mark**, and step 3 below is the only place a colour decision is made.
>
> Embedding checklist:
>
> 1. Re-prefix both mask ids per file and update the two `mask="url(#...)"` references to match:
>    `ringHero`/`eyeHero`, `ringMark`/`eyeMark`, `ringSig`/`eyeSig`, `ringStudio`/`eyeStudio`,
>    `ringWork`/`eyeWork`, `ringServer`/`eyeServer`, `ringComm`/`eyeComm`, `ringInside`/`eyeInside`.
> 2. Place and size with `<g transform="translate(x,y) scale(s)">`. Native size 500x364, so `scale(0.16)`
>    gives an 80x58 mark, `scale(0.78)` gives 390x284.
> 3. Recolour by setting `fill` on the outer `<g>`: flat `#f4f6fb`, or `fill="url(#{P}Mark)"` for the live
>    brand gradient. **The mark's colour is dynamic.** It travels the whole palette and the gradient itself
>    rotates, so the bolt never sits on one hue. A fixed white to blue ramp is not used anywhere in this set,
>    and must not be reintroduced. The template is `{P}Mark` in the shared defs; the five section bands slow
>    it down for the ghost, everything else runs it at full rate.
> 4. The mask rects are `x="-200" y="-300" width="900" height="1000"`. Keep them. They are deliberately
>    oversized and must not be trimmed to the viewBox.
> 5. The ghost treatment on the section bands is this same mark at `opacity="0.06"`, cropped by the band clip.
>    The ghost is never text.
>
> ---
>
> ## 9. MOTION SYSTEM
>
> An asset must read as ALIVE and never busy. Paused on the first frame it must still look composed.
>
> | Technique | Where | Duration |
> |---|---|---|
> | parallax layer orbit | every asset with plusses | L1 27-31s, L2 19-22s, L3 13-15s, L4 10.5-26s |
> | per plus orbit | roughly 1 plus in 3 to 4 | 7-13s, `begin` staggered across 0s to 9s |
> | twinkle opacity | about 1 plus in 3 | 3.2-7.5s, `begin` spread 0s to 6s |
> | scale breather | `hero.svg` and the two dividers only, 2-8 marks | 5.5-7.0s |
> | slow mark roll | a few plus groups per asset, `additive="sum"` | 19-33s |
> | brand gradient colour cycle | every asset carrying the bolt | stops 15s, section bands 34s |
> | brand gradient rotation | the same assets | 23s, section bands 34-41s |
> | wordmark gradient | `hero.svg`, `signature.svg`, the bands, the strip, the values band | stops 11s, rotation 29s |
> | charge rail dashoffset | `rail.svg`, `signature.svg`, `divider-wide.svg` | 1.8-2.6s |
> | node pulse | `rail.svg`, `signature.svg`, `divider-wide.svg` | 1.8-2.4s, `keyTimes="0;0.2;1"`, staggered `begin` |
> | logo glow breath | `mark.svg`, `hero.svg` | 6-9s |
>
> Hard limits: nothing faster than 1.6s except the charge rails at 1.8s. No flashing above 3 Hz. Type never
> spins, the bolt never spins; the only full turns in the set are a gradient rotating and the slow roll a few
> plus groups carry, which is nearly invisible on a mark with four fold symmetry. No opacity animation that
> reaches 0 quickly. **Orbits carry no `calcMode`:** a closed cubic already varies its own speed through its
> control points, and a spline on top of that reads as a stutter. Scale breathers keep
> `calcMode="spline" keySplines="0.4 0 0.2 1; 0.4 0 0.2 1"`; twinkles stay linear.
>
> `prefers-reduced-motion` cannot be honoured inside an `<img>` embedded SVG. That is why the amplitudes are
> small and the durations long. Do not attempt a media query.
>
> ---
>
> ## 10. GITHUB CONSTRAINTS THAT SHAPE EVERY FILE
>
> 1. Every SVG is **100 percent self contained**. No external font, no external image, no cross file `<use>`,
>    no `data:` URI image, no `@import`. Internal `<defs>`, gradients, filters, masks, clipPaths and patterns
>    only.
> 2. **SMIL is the animation primitive.** `<animate>`, `<animateTransform>`, `<animateMotion>`, `<set>`. No JavaScript, no
>    `:hover`, no CSS `transition`. Inline `<style>` with `@keyframes` is permitted but this set does not use
>    it: SMIL only, so there is one technique to review.
> 3. **Paint your own opaque background** across the full viewBox and draw your own rounded corners. Never
>    rely on the page canvas. Never use `@media (prefers-color-scheme: ...)` inside the SVG. The two dividers
>    are the single deliberate exception: they are strokes only at mid luminance, exactly as the user's own
>    divider ships.
> 4. `viewBox` present, **no fixed pixel `width`/`height` on the `<svg>` root**. Design so it stays legible at
>    350px wide: that is why band eyebrows are 10.5px and not 9.
> 5. In the README every `<img>` gets **`width` only, never `height`**, or GitHub injects a muted grey box
>    behind the asset.
> 6. Absolute raw URLs only:
>    `https://raw.githubusercontent.com/Vision-Force/.github/main/profile/assets/<name>.svg`
> 7. Meaningful `alt` on every image, empty `alt` on the dividers and the rail.
> 8. Target 30 KB per SVG, hard stop 100 KB. This is why the dot matrix is a `<pattern>` and not 2,000 circles.
> 9. Ids must be unique per file but files never share a document, so the `{P}` prefix is for author sanity and
>    for safe future concatenation. Prefix everything anyway.
>
> ---
>
> ## 11. THE ASSET SET (13 files, no project cards)
>
> ```
> profile/assets/
>   hero.svg              1600x480
>   mark.svg               320x320
>   signature.svg         1200x200
>   divider.svg            880x26
>   divider-wide.svg      1200x30
>   rail.svg                46x72
>   section-studio.svg    1200x130
>   section-work.svg      1200x130
>   section-server.svg    1200x130
>   section-community.svg 1200x130
>   section-inside.svg    1200x130
>   studio-strip.svg      1200x170
>   values-band.svg       1200x260
> ```
>
> The five section bands share ONE template: identical eyebrow baseline, identical headline baseline,
> identical ghost mark placement, identical dashed hairline. Only the two words and the accent colour change.
> If the five bands do not stack as an obvious set, the template was not followed.
>
> **The assets are about the STUDIO.** Its mark, its name, what kind of outfit it is, what it stands for, how
> to reach it. Identity, not catalogue. Project detail lives in the README's markdown text.
>
> ---
>
> ## 12. VOICE
>
> - Short sentences, around 11 words on average. Second person where it addresses a reader.
> - Sentence case. Acronyms stay upper: UEFN, LUX3, UE5.
> - Headings take no full stop. Body copy does.
> - Never claim a shipped feature for Meridian. It is early and in development.
> - Meridian copy says: an original re-implementation of network services; players bring their own archived
>   client; no download link of any kind; not affiliated with or endorsed by Epic Games; Fortnite and Unreal
>   are trademarks of Epic Games, Inc; non commercial. That note gets a real heading and normal body size.


## Shared defs

Every asset copies this fragment, replacing {P} with a per file id prefix.

```svg
&lt;!-- SHARED DEFS: copy verbatim into every asset. Replace {P} with the per-file id prefix.
     Prefixes in use: hero, mark, sig, dv, dvw, rail, st (studio band), wk (work band),
     sv (server band), cm (community band), in (inside band), strip, val.
     Example: id="{P}Cy" becomes id="heroCy", referenced as fill="url(#heroCy)". --&gt;
&lt;defs&gt;

  &lt;!-- cy : the UEFN-Builds diagonal cyan --&gt;
  &lt;linearGradient id="{P}Cy" x1="0" y1="0" x2="1" y2="1"&gt;
    &lt;stop offset="0" stop-color="#47d1ff"/&gt;
    &lt;stop offset="1" stop-color="#1273ea"/&gt;
  &lt;/linearGradient&gt;

  &lt;!-- vi : the studio hero accent, violet --&gt;
  &lt;linearGradient id="{P}Vi" x1="0" y1="0" x2="1" y2="1"&gt;
    &lt;stop offset="0" stop-color="#a855f7"/&gt;
    &lt;stop offset="1" stop-color="#6d28d9"/&gt;
  &lt;/linearGradient&gt;

  &lt;!-- bg : the card surface gradient, near invisible tilt --&gt;
  &lt;linearGradient id="{P}Bg" x1="0" y1="0" x2="1" y2="1"&gt;
    &lt;stop offset="0" stop-color="#0d1a2e"/&gt;
    &lt;stop offset="1" stop-color="#0a1425"/&gt;
  &lt;/linearGradient&gt;

  &lt;!-- Mark : the winged bolt's LIVE fill. Every stop animates and the whole gradient rotates,
       so the mark never sits on one colour. THE RULE: every stop-color animate inside one
       gradient MUST share the same dur. Give one stop a different dur and the stops fall out
       of phase mid cycle, the ramp inverts for part of the loop, and the gradient tears.
       The rotate is exempt: it drives gradientTransform, not a stop, so it may differ.
       Rates: 15s stops with a 23s rotation everywhere, slowed to 34s stops and a 34-41s
       rotation on the five section bands so the ghost mark does not compete with the headline. --&gt;
  &lt;linearGradient id="{P}Mark" gradientUnits="objectBoundingBox" x1="0" y1="0" x2="1" y2="1"&gt;
    &lt;stop offset="0" stop-color="#f4f6fb"&gt;
      &lt;animate attributeName="stop-color" values="#f4f6fb;#e9d8ff;#d8f4ff;#ffe4f2;#f4f6fb"
               dur="15s" repeatCount="indefinite"/&gt;
    &lt;/stop&gt;
    &lt;stop offset="0.45" stop-color="#a855f7"&gt;
      &lt;animate attributeName="stop-color" values="#a855f7;#47d1ff;#ff2e4d;#8b5cff;#a855f7"
               dur="15s" repeatCount="indefinite"/&gt;
    &lt;/stop&gt;
    &lt;stop offset="1" stop-color="#6d28d9"&gt;
      &lt;animate attributeName="stop-color" values="#6d28d9;#1273ea;#a02bfe;#0ea5b7;#6d28d9"
               dur="15s" repeatCount="indefinite"/&gt;
    &lt;/stop&gt;
    &lt;animateTransform attributeName="gradientTransform" type="rotate"
      values="0 0.5 0.5; 360 0.5 0.5" dur="23s" repeatCount="indefinite"/&gt;
  &lt;/linearGradient&gt;

  &lt;!-- Word : the same idea for the accent half of a two tone headline. Same shared-dur rule:
       all three stops at 11s, rotation at 29s. First and last values entry must equal the
       stop's own stop-color or the loop jumps. Violet lead everywhere; section-server.svg is
       the ONE file that leads cyan, #47d1ff / #9beaff / #1273ea, per the palette hierarchy. --&gt;
  &lt;linearGradient id="{P}Word" x1="0" y1="0" x2="1" y2="0"&gt;
    &lt;stop offset="0" stop-color="#a855f7"&gt;
      &lt;animate attributeName="stop-color" values="#a855f7;#8b5cff;#47d1ff;#a855f7"
               dur="11s" repeatCount="indefinite"/&gt;
    &lt;/stop&gt;
    &lt;stop offset="0.5" stop-color="#c9a6ff"&gt;
      &lt;animate attributeName="stop-color" values="#c9a6ff;#7fe3ff;#c9a6ff;#c9a6ff"
               dur="11s" repeatCount="indefinite"/&gt;
    &lt;/stop&gt;
    &lt;stop offset="1" stop-color="#8b5cff"&gt;
      &lt;animate attributeName="stop-color" values="#8b5cff;#47d1ff;#a855f7;#8b5cff"
               dur="11s" repeatCount="indefinite"/&gt;
    &lt;/stop&gt;
    &lt;animateTransform attributeName="gradientTransform" type="rotate"
      values="0 0.5 0.5; 360 0.5 0.5" dur="29s" repeatCount="indefinite"/&gt;
  &lt;/linearGradient&gt;

  &lt;!-- spark : the charge-rail stroke, from rel-25-00.svg --&gt;
  &lt;linearGradient id="{P}Spark" x1="0" y1="0" x2="1" y2="1"&gt;
    &lt;stop offset="0" stop-color="#9beaff"/&gt;
    &lt;stop offset="0.55" stop-color="#47d1ff"/&gt;
    &lt;stop offset="1" stop-color="#7aa2ff"/&gt;
  &lt;/linearGradient&gt;

  &lt;!-- top : the 5 to 10 percent white radial anchored at the top edge --&gt;
  &lt;radialGradient id="{P}Top" cx="0.5" cy="0" r="1"&gt;
    &lt;stop offset="0" stop-color="#ffffff" stop-opacity="0.075"/&gt;
    &lt;stop offset="1" stop-color="#ffffff" stop-opacity="0"/&gt;
  &lt;/radialGradient&gt;

  &lt;!-- dots : the site's dot matrix, as a pattern so it costs ~120 bytes and not 70 KB --&gt;
  &lt;pattern id="{P}Dots" width="14" height="14" patternUnits="userSpaceOnUse"&gt;
    &lt;circle cx="7" cy="7" r="1.1" fill="#9aa8c4" opacity="0.13"/&gt;
  &lt;/pattern&gt;
  &lt;pattern id="{P}DotsFine" width="16" height="16" patternUnits="userSpaceOnUse"&gt;
    &lt;circle cx="4" cy="4" r="0.8" fill="#9aa8c4" opacity="0.07"/&gt;
  &lt;/pattern&gt;

  &lt;!-- MaskH / FadeR : edge fade for the dot field. objectBoundingBox units, so it is
       canvas-agnostic: apply mask="url(#{P}FadeR)" to any rect and it fades left to right. --&gt;
  &lt;linearGradient id="{P}MaskH" x1="0" y1="0" x2="1" y2="0"&gt;
    &lt;stop offset="0"    stop-color="#000000"/&gt;
    &lt;stop offset="0.34" stop-color="#3a3a3a"/&gt;
    &lt;stop offset="0.72" stop-color="#c8c8c8"/&gt;
    &lt;stop offset="1"    stop-color="#ffffff"/&gt;
  &lt;/linearGradient&gt;
  &lt;mask id="{P}FadeR" maskContentUnits="objectBoundingBox"&gt;
    &lt;rect x="0" y="0" width="1" height="1" fill="url(#{P}MaskH)"/&gt;
  &lt;/mask&gt;

  &lt;!-- soft : the blurs. Soft for the logo glow, SoftTight for accent-rule bloom. --&gt;
  &lt;filter id="{P}Soft" x="-60%" y="-60%" width="220%" height="220%"&gt;
    &lt;feGaussianBlur stdDeviation="7"/&gt;
  &lt;/filter&gt;
  &lt;filter id="{P}SoftTight" x="-60%" y="-60%" width="220%" height="220%"&gt;
    &lt;feGaussianBlur stdDeviation="2.6"/&gt;
  &lt;/filter&gt;

&lt;/defs&gt;
```

## The plus motif

```
## THE PLUS RECIPE. Follow it literally. Do not improvise.

### 1. The plus form (copied verbatim from the user's own divider)

```
<path d="M{cx-h} {cy}H{cx+h}M{cx} {cy-h}V{cy+h}" stroke="{c}" stroke-width="{w}"
      stroke-linecap="round" opacity="{o}"/>
```

ONE path. Horizontal subpath first, vertical second, same `d`. No fill. No `rx`. Round caps only.
Coordinates to ONE decimal place.

### 2. Worked example, start to finish

Wanted: a mid-layer violet plus at centre (413.7, 88.2), half length h = 4.1.

- `cx - h` = 409.6, `cx + h` = 417.8
- `cy - h` = 84.1, `cy + h` = 92.3
- h is 4.1, which sits in the MID band, so stroke-width 2.2 and opacity 0.58

```xml
<path d="M409.6 88.2H417.8M413.7 84.1V92.3" stroke="#a855f7" stroke-width="2.2"
      stroke-linecap="round" opacity="0.58"/>
```

That plus goes inside the l2 group. Nothing else needs deciding.

### 3. The size / weight / opacity coupling table (NEVER break it)

| Layer | half length h | stroke-width w | opacity o | typical colours |
|---|---|---|---|---|
| l1 (far, small, faint) | 3.0 to 3.4 | 1.6 to 1.8 | 0.23 to 0.42 | `#6ea8dc` `#3b82f6` `#8b5cff` |
| l2 (mid) | 3.5 to 4.2 | 1.9 to 2.2 | 0.40 to 0.62 | `#a855f7` `#47d1ff` `#3b82f6` `#34d399` |
| l3 (near, big, bright) | 4.3 to 5.1 | 2.4 to 2.8 | 0.60 to 0.90 | `#a855f7` `#47d1ff` `#e8eefb` |

### 4. The layer wrappers, written out in full. Copy these exactly.

**Layers ORBIT. They do not drift out and back.** The rejected first version used
`animateTransform type="translate"` with a `values="0 0; X Y; 0 0"` list. That stops dead on the middle key
and then retraces its own route in reverse, so the whole field pauses and rewinds twice a cycle. It reads as a
twitch, not as motion, and it is gone. Every layer now carries an `animateMotion` whose `path`:

- starts at `0,0`, so the layer's rest position is exactly where the plusses are authored,
- is built ONLY from `C` cubic segments. No `L`, no `Q`, no `A`. A straight run gives the eye a corner to
  catch on, and a corner is where a curve stops looking like drift,
- closes with `Z`, so the end meets the start. Travel is continuous, one way round, forever. Nothing reverses,
- carries no `calcMode` and no `keyTimes`. See the easing note in section 9.

```xml
<!-- LAYER 1: far. Slowest, smallest orbit. -->
<g><animateMotion dur="29s" repeatCount="indefinite" path="M0,0 C 6,-5 13,-2 14,4 C 15,10 8,14 0,12 C -7,10 -10,5 -8,1 C -6,-3 -3,-2 0,0 Z"/>
  <!-- l1 plusses go here -->
</g>

<!-- LAYER 2: mid. Medium speed, opposite drift to layer 1. -->
<g><animateMotion dur="21s" repeatCount="indefinite" path="M0,0 C -9,-7 -19,-3 -20,6 C -21,15 -12,21 0,18 C 11,15 15,7 12,1 C 9,-5 4,-3 0,0 Z"/>
  <!-- l2 plusses go here -->
</g>

<!-- LAYER 3: near. Fastest, largest orbit. -->
<g><animateMotion dur="14s" repeatCount="indefinite" path="M0,0 C 14,-11 30,-5 32,9 C 34,23 19,32 1,28 C -17,24 -24,11 -19,2 C -14,-7 -7,-5 0,0 Z"/>
  <!-- l3 plusses go here -->
</g>

<!-- LAYER 4: counter orbit, travels the opposite way round. -->
<g><animateMotion dur="19s" repeatCount="indefinite" path="M0,0 C -12,8 -26,3 -28,-8 C -30,-19 -16,-27 -1,-24 C 14,-21 20,-10 16,-2 C 12,5 6,4 0,0 Z"/>
  <!-- l4 plusses go here -->
</g>
```

Those four are `hero.svg` verbatim. Layer 4 exists so the field never slides as one sheet: read the sign of
its first control point against layer 3 and you can see it goes round the other way. Give layer 4 to every
canvas that has the room. `mark.svg` and `signature.svg` run three layers, `rail.svg` runs one.

### 4b. The per plus orbit, on top of the layer orbit

Roughly ONE PLUS IN THREE TO FOUR gets its own small closed orbit as well, so the field never moves as a rigid
constellation. The plus is drawn at the ORIGIN and its wrapper `<g>` carries the placement, exactly like the
scale breather in section 6. Same three path rules: start at `0,0`, `C` segments only, close with `Z`.

```xml
<g transform="translate(1359.3,431.9)">
  <animateMotion dur="7s" begin="0s" repeatCount="indefinite" path="M0,0 C 5.12,-3.84 10.24,0 8.96,5.12 C 7.68,10.24 1.28,11.52 -3.84,8.96 C -8.96,6.4 -7.68,1.28 0,0 Z"/>
  <path d="M-3.3 0H3.3M0 -3.3V3.3" stroke="#3b82f6" stroke-width="1.7" stroke-linecap="round" opacity="0.34"/>
</g>
```

`begin` is what keeps them from pulsing together. Stagger it across the field from the set
{0s, 0.6s, 1.2s, 2.4s, 3s, 3.6s, 4.8s, 5.4s, 6s, 7.2s, 8.4s, 9s}, and never give two adjacent marks the same
`dur` and `begin` pair.

A few of these wrapper groups also carry a very slow `type="rotate"` roll, `values="0;360"` at 19s to 33s,
`additive="sum"` so it stacks on the orbit. On a plus with four fold symmetry this is almost subliminal. Use
it on a handful per asset, not on a whole layer.

### 4c. The bands actually used, measured off the shipped assets

| Band | Layer count | `dur` | orbit extent, wide canvases | orbit extent, the dividers |
|---|---|---|---|---|
| L1 far | present in all | 27-31s | 25-33 by 13-28 | 17-19 by 2.6-3.2 |
| L2 mid | present in all but `rail.svg` | 19-22s | 34-45 by 17-33 | 19-21 by 4.4-5.0 |
| L3 near | present in all but `rail.svg` | 13-15s | 54-70 by 23-52 | 28-32 by 5.6-6.6 |
| L4 counter | all but `mark.svg`, `signature.svg`, `rail.svg` | 19-26s wide, 10.5-13s on the dividers | 35-43 by 18-35 | 7-11.2 by 3.8-5.2 |
| per plus | 1 mark in 3 to 4 | 7-13s | 13-20 by 11.5-20 | 6-11 by 4-5 |

Extent is the full width by full height of the closed path's bounding box, so the visible travel is that
figure, not twice it. The pattern to hold on to: **near layers orbit further and faster than far layers**,
which is the same coupling as the size, weight and opacity table above. On the two dividers the vertical
component is crushed because the canvas is only 26 to 30 tall; the horizontal band is unchanged.
`rail.svg` at 46 by 72 runs one layer at 30s over a 6.6 by 2.4 orbit, and all three of its marks carry their
own inward biased orbits, because an outward loop would clip on a canvas that small.

Per-asset duration jitter so no two files loop in lockstep: pick L1 from {27s, 29s, 30s, 31s}, L2 from
{19s, 20s, 21s, 22s}, L3 from {13s, 14s, 15s}, L4 from {24s, 25s, 26s} on a tall canvas. Vary the path's
control points a little too, so the jitter does not read as the same shape at a different speed.

### 5. The twinkle, written out in full

Roughly ONE PLUS IN THREE also carries its own opacity animate, as a CHILD of the path.
The first and last `values` entry MUST equal the path's static `opacity` so the loop is seamless.

```xml
<path d="M409.6 88.2H417.8M413.7 84.1V92.3" stroke="#a855f7" stroke-width="2.2"
      stroke-linecap="round" opacity="0.58">
  <animate attributeName="opacity" values="0.58;0.21;0.58" dur="4.6s"
           begin="1.3s" repeatCount="indefinite"/>
</path>
```

Rules:
- `dur` between 3.2s and 7.5s. Pick from {3.2s, 3.9s, 4.6s, 5.1s, 5.8s, 6.4s, 7.5s}.
- `begin` spread across 0s to 6s. Pick from {0s, 0.4s, 0.9s, 1.3s, 1.8s, 2.4s, 3.1s, 3.7s, 4.2s, 5.0s, 5.6s}.
- The dim value is roughly 0.36 times the bright value. Never animate to 0. Never strobe.
- Two adjacent plusses must not share both `dur` and `begin`.

### 6. The scale breather. l3 members only, and only where the canvas is large.

`hero.svg` carries 8, `divider-wide.svg` 3, `divider.svg` 2, and no other asset uses one. The plus is drawn at
the ORIGIN so the scale is centred on it, and the group carries the placement. `additive="sum"` stacks the
scale on top of whatever the group is already doing, which is the orbit from section 4b.

```xml
<g transform="translate(742,196)">
  <path d="M-4.6 0H4.6M0 -4.6V4.6" stroke="#a855f7" stroke-width="2.6"
        stroke-linecap="round" opacity="0.74"/>
  <animateTransform attributeName="transform" type="scale" additive="sum"
    values="1;1.18;1" dur="6.2s" begin="0.8s" repeatCount="indefinite"
    calcMode="spline" keyTimes="0;0.5;1"
    keySplines="0.4 0 0.2 1; 0.4 0 0.2 1"/>
</g>
```

Put these breather groups INSIDE the l3 wrapper so they parallax too. `dur` from
{5.5s, 5.9s, 6.2s, 6.7s, 7.0s}, `values` peak from {1.12, 1.15, 1.18, 1.22}.

### 7. The charge rail. Reused verbatim from rel-25-00.svg.

Three strokes on the SAME path geometry:

```xml
<path d="{RAILPATH}" fill="none" stroke="#2a4a78" stroke-width="1.7" opacity="0.9"/>
<path d="{RAILPATH}" fill="none" stroke="url(#railSpark)" stroke-width="5.5" opacity="0.22"
      stroke-dasharray="4 32" stroke-linecap="round">
  <animate attributeName="stroke-dashoffset" from="0" to="-36" dur="1.8s" repeatCount="indefinite"/>
</path>
<path d="{RAILPATH}" fill="none" stroke="url(#railSpark)" stroke-width="2" opacity="0.95"
      stroke-dasharray="4 32" stroke-linecap="round">
  <animate attributeName="stroke-dashoffset" from="0" to="-36" dur="1.8s" repeatCount="indefinite"/>
</path>
```

Wide faint under, thin bright over. Width ratio 2.75 to 1, opacity ratio 1 to 4.3. Period 36 equals the
dasharray sum, so the loop is seamless. Never add a blur filter to this: the sandwich IS the glow.

### 8. DENSITY TABLE. This is the plus COUNT per file. Not a suggestion.

| Asset | Canvas | TOTAL | l1 | l2 | l3 | breathers (subset of l3) | twinkles (any layer) |
|---|---|---|---|---|---|---|---|
| hero.svg | 1600x480 | **142** | 64 | 51 | 27 | 8 | 47 |
| mark.svg | 320x320 | **34** | 15 | 12 | 7 | 4 | 11 |
| signature.svg | 1200x200 | **44** | 20 | 16 | 8 | 4 | 15 |
| divider.svg | 880x26 | **18** | 7 | 7 | 4 | 2 | 6 |
| divider-wide.svg | 1200x30 | **26** | 11 | 10 | 5 | 3 | 9 |
| rail.svg | 46x72 | **3** | 1 | 1 | 1 | 0 | 1 |
| section-studio.svg | 1200x130 | **38** | 17 | 14 | 7 | 4 | 13 |
| section-work.svg | 1200x130 | **38** | 17 | 14 | 7 | 4 | 13 |
| section-server.svg | 1200x130 | **38** | 17 | 14 | 7 | 4 | 13 |
| section-community.svg | 1200x130 | **38** | 17 | 14 | 7 | 4 | 13 |
| section-inside.svg | 1200x130 | **38** | 17 | 14 | 7 | 4 | 13 |
| studio-strip.svg | 1200x170 | **34** | 15 | 12 | 7 | 4 | 12 |
| values-band.svg | 1200x260 | **52** | 24 | 19 | 9 | 5 | 17 |

**rail.svg is the one exception to the layer rule:** at 46x72 there is no room for three or four layers. Its
three plusses sit in a SINGLE group. That group still orbits, 30s over a 6.6 by 2.4 path, and all three marks
carry their own orbit on top, biased inward so an outward loop cannot clip the edge. Nothing in this set is
still, not even the smallest asset.

### 9. Scatter discipline

- Never a visible grid. Never even spacing. Cluster two or three marks, then leave a wide gap.
- Density rises toward the RIGHT and toward the corners, and falls to zero over the type.
- Exclusion zones: 40px clear around display glyphs, 24px around body copy, 20px around the logo mark.
- Each layer must have at least one mark in each of the canvas's four quadrants, so the parallax is visible
  everywhere and not just on one side.
- Green `#34d399` is the surprise: roughly one mark in twenty, never two green marks adjacent.
- Near white `#e8eefb` is rarer still: at most two per asset, both in l3, both at opacity 0.82 or higher.
- Each asset gets exactly ONE hero plus: the largest (h 5.0 or 5.1), brightest (opacity 0.88 to 0.90),
  thickest (2.8), placed on a deliberate compositional point, not at random.

```
