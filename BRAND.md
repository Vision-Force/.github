# Vision Force, organisation design system

The visual system behind this organisation profile and the twenty SVGs in `profile/assets/`. It states what the
assets do and what a new asset must do to join the set. Where this document and an asset disagree, open the asset:
the file is the artefact, this is the description of it. The studio name rendered in the SVGs is a swappable
placeholder. See "Renaming the studio".

## 1. Principles

- **Brutal, black, left aligned.** Nothing is centred except inside `mark.svg`.
- **Everything moves.** Every asset in the set carries orbiting parallax layers, and most carry twinkle, per-plus
  orbits and a breather on top.
- **A moving highlight is not part of this system.** No scan sweep, no shine, no gloss, no sheen crossing a card.
  The plus field is the only thing that reads as motion; a travelling highlight competes with it and flattens the
  depth the parallax buys.
- **Two marks are copied, never redrawn:** the plus (section 9) and the winged bolt (section 8).

## 2. Banned characters and banned content

These must not appear in any `.svg`, any `.md`, any comment, any `alt` string, or any commit message:

| Codepoint | Character | Instead use |
|---|---|---|
| U+2014 | em dash | a colon, a full stop, a comma, or restructure the sentence |
| U+2013 | en dash | a plain hyphen for numeric ranges only, never in prose |
| U+00B7 | middot / interpunct | generous space, a real `<line>` hairline, or a slash |
| U+2022 | bullet dot | a markdown list, or a drawn `<rect>` accent rule |
| U+2026 | ellipsis | end the sentence |
| U+2018 U+2019 U+201C U+201D | curly quotes | straight quotes |

Verification, from the repository root. Zero hits required:

```
grep -RPn "[\x{2014}\x{2013}\x{00B7}\x{2022}\x{2026}\x{2018}\x{2019}\x{201C}\x{201D}]" profile/
```

Banned content, not just characters: no tiny grey footer line at the end of an asset, if it must be said it gets a
heading and normal body size; no project cards, blurbs, tag chips, status chips or counters inside artwork; no fake
stars, fake download counts or badge graphics drawn inside the artwork.

## 3. Layout and geometry

**Left margin is a constant per canvas family.** 1600 wide (`hero.svg`): `x = 96`. 1200 wide (bands, strip, values,
signature, project-row): `x = 64`, and `signature.svg` sets its wordmark at 292, right of the mark. The dashed rules
inset 60 on `divider.svg` and 70 on `divider-wide.svg`. The right third is imagery, the bolt and the dot pattern and
the brightest plus layer, and type never crosses into it.

**A left accent bar** opens `hero.svg` and every band: `<rect x="0" y="0" width="{W}" height="{H}">` filled with the
accent gradient, drawn inside the clip so it inherits the corner radius. Widths: 6 on `hero.svg`, 5 on the five
bands and on `signature.svg`, `studio-strip.svg`, `values-band.svg`, 4 on `project-row.svg`. It is the one shared
structural tell across the set.

**Corners.** `hero.svg` `rx="18"`; the five bands and `project-row.svg` `rx="14"`; `signature.svg`,
`studio-strip.svg`, `values-band.svg` and the six buttons `rx="16"`; `mark.svg` `rx="28"`. Never square, never pill
except for actual pill chips. **Borders are hairline, 1px, always:** `#1b2742` normal, `#232f4a` raised, never 2px.

**Frame discipline.** Background rect first, all content inside `<g clip-path="url(#{P}Clip)">` where the clip is the
same rect, then the same rect drawn again last as `fill="none" stroke="#1b2742" stroke-width="1"`, so the hairline
sits over the clipped art.

## 4. Palette

| Ground and ink | Hex | Use |
|---|---|---|
| ground | `#050506` | page ground of every asset |
| studio surface | `#08090a` | the `mark.svg` square, raised blocks on black |
| deep panel | `#0a0e17` | inset panels |
| card base | `#0c1322` | pill chips, inner chips |
| card gradient | `#0d1a2e` to `#0a1425` | the `{P}Bg` gradient, used only inside surfaces |
| raised panel | `#111826` | rare |
| display white | `#f4f6fb` | the white half of every two tone headline |
| bright ink | `#e8eefb` | chip labels, the rarest brightest plusses |
| body | `#c3cad8` | primary body copy |
| body dim | `#a8b0c0` | secondary body copy |
| eyebrow grey | `#7d8798` | every wide tracked caps label |
| dash rule | `#4a6f96` | the divider hairline, `stroke-dasharray="1 7"`, opacity 0.55 |
| headline shadow | `#05070b` | the offset copy under every display headline |

| Accent | Hex | Rank |
|---|---|---|
| violet | `#a855f7` | hero accent, the studio colour, used generously |
| violet blue | `#8b5cff` | violet's companion in the plus field |
| cyan | `#47d1ff` | secondary accent, and the Rocket Racing Reborn colour |
| pale cyan | `#9beaff` | charge rail head, rare plus highlight |
| blue | `#3b82f6` | plus field |
| deep blue | `#1273ea` | gradient end, plus field |
| steel blue | `#6ea8dc` | dim plusses |
| green | `#34d399` | sparing accent surprise |
| Reality Cross `#a02bfe`, Vaelora Velocity `#ff2e4d`, amber `#ffb83d`, shipped green `#38f0a0` | | README text only |

**Violet leads.** Measured across the 694 plus marks in the set: violet family (`#a855f7` plus `#8b5cff`) 36.0
percent, cyan 22.8, blue 13.3, steel 12.7, green 4.9, deep blue 3.0, near white 1.9, pale cyan 1.0. Hold roughly
that shape in any new asset. Two exceptions: `section-server.svg` flips to cyan lead, both in its accent bar
(`url(#svCy)`, not `url(#svVi)`) and in its `{P}Word` gradient, because it is the Rocket Racing Reborn band; and the
six `btn-*.svg` files each carry a few marks in the destination service's own colour, the only place a non-palette
hex is permitted.

## 5. Type

One stack everywhere. No web font can load inside an `<img>` embedded SVG, so a named-font gamble is a broken asset.
All 66 `<text>` elements in the set declare exactly this, and no monospace family appears anywhere:

```
font-family="Segoe UI, -apple-system, Helvetica, Arial, sans-serif"
```

| Role | Where | Size | Weight | Letter spacing | Fill |
|---|---|---|---|---|---|
| wordmark | `hero.svg` | 120 | 800 | -2.5 | two tone |
| wordmark | `signature.svg` | 56 | 800 | -2.2 | two tone |
| band headline | community, method bands | 56 | 800 | -2.4 | two tone |
| band headline | studio, work, server bands | 46 | 800 | -1.8 | two tone |
| column value | `studio-strip.svg` | 32 | 800 | -1.2 | `url(#stripWord)` |
| statement title | `values-band.svg` | 26 | 800 | -0.9 | `url(#valWord)` |
| sub | `hero.svg` | 17 | 400 | 0 | `#c3cad8` |
| button label | `btn-*.svg` | 17 | 700 | -0.2 | `#f4f6fb` |
| project name | `project-row.svg` | 17 | 700 | 1.8 | `#f4f6fb`, `text-anchor="middle"` |
| body | hero, signature, values | 15 | 400 | 0 | `#a8b0c0` |
| chip label | `hero.svg` | 13 | 600 | 0.4 | `#e8eefb` |
| eyebrow | `hero.svg` | 11 | 600 | 4.6 | `#7d8798`, uppercase |
| eyebrow | bands, strip, values, signature | 10.5 | 600 | 4.2 | `#7d8798`, uppercase |
| eyebrow | `btn-*.svg` | 9.5 | 600 | 3.6 | `#7d8798`, uppercase |

Display type is big relative to its canvas: the hero wordmark is 120px on a 480 tall canvas. Tracking is
bidirectional and extreme at both ends, with almost nothing in between. Text stays live `<text>`, never converted to
paths, so the wordmark remains swappable. Use `text-anchor="start"` for all left aligned copy, which is nearly all
of it; `project-row.svg` is the exception, anchoring its three names `middle` on fixed slot centres so the layout is
never measured from the glyphs and a longer name cannot shift it. Headings carry no trailing full stop and body
sentences do, except the `values-band.svg` statement titles, two beat lines where the period is the point.

## 6. The two tone display headline

The first word is near white `#f4f6fb`. The second is not a flat accent hex: it is filled with `url(#{P}Word)`, the
live wordmark gradient, so the accent shifts through the violet family and back. Every display headline ships as two
stacked `<text>` elements. The lower one, drawn first, is a solid `#05070b` copy sitting 2px below, which separates
the display type from the plus field without a blur or a drop shadow filter. The upper one carries the colour.

```xml
<text x="64" y="92" font-family="Segoe UI, -apple-system, Helvetica, Arial, sans-serif"
      font-size="46" font-weight="800" letter-spacing="-1.8" fill="#05070b"><tspan>The</tspan><tspan dx="13">Studio</tspan></text>
<text x="64" y="90" font-family="Segoe UI, -apple-system, Helvetica, Arial, sans-serif"
      font-size="46" font-weight="800" letter-spacing="-1.8"><tspan fill="#f4f6fb">The</tspan><tspan dx="13" fill="url(#stWord)">Studio</tspan></text>
```

The wordmarks and the five band headlines split the line into two `<tspan>` children, white then gradient.
`studio-strip.svg` and `values-band.svg` instead fill the whole string with `url(#{P}Word)` and carry no tspans,
because their lines are single values and single statements. Use `dx` for the word gap, never a trailing space
inside a tspan: XML whitespace collapsing makes a trailing space unreliable across renderers. `dx="13"` at 46px,
`dx="14"` at 56px and at 120px.

The five bands share one template in two size variants. Studio, work and server put the eyebrow at `y="44"` and the
headline at `y="92"` / `y="90"`; community and method put them at `y="40"` and `y="98"` / `y="96"` for the larger
type. Everything else is identical: `x="64"`, the same ghost mark placement, the same dashed hairline. If the five
bands do not stack as an obvious set, the template was not followed.

## 7. Renaming the studio

Wherever the studio name appears in an SVG: render it as live `<text>`, never as paths; put it inside its own
`<g id="{file}Wordmark">` containing nothing else; and put this comment line immediately above that group, exactly:

```xml
<!-- PLACEHOLDER STUDIO NAME: swap the two tspans below on rebrand -->
```

Build it from the stacked pair in section 6: the `#05070b` shadow copy, then the live copy, each with two `<tspan>`
children, the first white and the second filled `url(#{P}Word)`. Only two assets carry the name.

| File | Group | Shadow text | Live text | Size | Letter spacing | dx |
|---|---|---|---|---|---|---|
| `hero.svg` | `heroWordmark` | `x="96" y="246"` | `x="96" y="244"` | 120 | -2.5 | 14 |
| `signature.svg` | `sigWordmark` | `x="292" y="124"` | `x="292" y="122"` | 56 | -2.2 | 14 |

Each group holds exactly two `<text>` elements and nothing else, and each `<text>` holds exactly two `<tspan>`
children. So a rename touches **four tspans per file, not two**. Edit both copies, or the rebrand ships with the old
name ghosted 2px behind the new one.

The section bands say "The Studio", "The Work", "The Server", "The Community" and "The Method", and never the studio
name. `mark.svg` carries no text at all. Do not put the studio name in a ghost layer, a watermark, or an `alt`
string that would need editing in more than one place.

## 8. The winged bolt

The winged lightning bolt through an orbital ring with an eye aperture has `viewBox="0 0 500 364"`. **The path
geometry is copied verbatim.** Copy the two mask definitions and the two `<path>` elements across unchanged. Do not
redraw, simplify, round, re-fit or clean up the path data. Do not draw chevrons. Recolouring is the only change ever
permitted. Eight assets carry it: `hero.svg`, `mark.svg`, `signature.svg` and the five section bands.

1. Re-prefix both mask ids per file and update the two `mask="url(#...)"` references to match: `ringHero`/`eyeHero`,
   `ringMark`/`eyeMark`, `ringSig`/`eyeSig`, `ringStudio`/`eyeStudio`, `ringWork`/`eyeWork`,
   `ringServer`/`eyeServer`, `ringComm`/`eyeComm`, `ringInside`/`eyeInside`.
2. Place and size with `<g transform="translate(x,y) scale(s)">`. Native size is 500x364. Scales in use: `0.24` on
   `signature.svg`, `0.44` on `mark.svg`, `0.52` on the five bands, `0.80` on `hero.svg`.
3. Recolour by setting `fill` on the outer `<g>`: flat `#f4f6fb`, or `fill="url(#{P}Mark)"` for the live brand
   gradient. **The mark's colour is dynamic.** It travels the whole palette and the gradient itself rotates, so the
   bolt never sits on one hue. A fixed white to blue ramp is not used anywhere in this set.
4. The mask rects are `x="-200" y="-300" width="900" height="1000"`. Keep them. They are deliberately oversized and
   must not be trimmed to the viewBox.
5. `hero.svg` and `mark.svg` draw the mark twice: a blurred flat-colour glow copy underneath, then the real
   gradient-filled mark over it.
6. The ghost on the section bands is the same mark cropped by the band clip, at `opacity="0.06"` on studio, work and
   server and `opacity="0.09"` on community and method. The ghost is never text.

## 9. The plus motif

```
<path d="M{cx-h} {cy}H{cx+h}M{cx} {cy-h}V{cy+h}" stroke="{c}" stroke-width="{w}"
      stroke-linecap="round" opacity="{o}"/>
```

One path element per plus. Horizontal subpath first, vertical second, same `d`. Never two paths. No fill. No `rx`.
No square caps. No `stroke-linejoin`. `stroke-linecap="round"` is mandatory. Coordinates carry one decimal place.

**Size, weight and opacity are coupled. Bigger means brighter and thicker.**

| Layer | half length h | stroke-width w | opacity o | typical colours |
|---|---|---|---|---|
| l1 (far, small, faint) | 3.0 to 3.4 | 1.6 to 1.8 | 0.23 to 0.42 | `#6ea8dc` `#3b82f6` `#8b5cff` |
| l2 (mid) | 3.5 to 4.2 | 1.9 to 2.2 | 0.40 to 0.62 | `#a855f7` `#47d1ff` `#3b82f6` `#34d399` |
| l3 (near, big, bright) | 4.3 to 5.1 | 2.4 to 2.8 | 0.60 to 0.90 | `#a855f7` `#47d1ff` `#e8eefb` |

5.1 is the ceiling, except that the two 56px section bands each carry one mark at `h` 6.0 to hold the larger
headline. A mid layer violet plus centred at (413.7, 88.2) with `h = 4.1` therefore reads:

```xml
<path d="M409.6 88.2H417.8M413.7 84.1V92.3" stroke="#a855f7" stroke-width="2.2"
      stroke-linecap="round" opacity="0.58"/>
```

**Scatter discipline.** Never a visible grid, never even spacing: cluster two or three marks, then leave a wide gap.
Density rises toward the right and toward the corners and falls to zero over the type, with 40px clear around
display glyphs, 24px around body copy and 20px around the bolt. Each layer keeps a mark in each of the canvas's four
quadrants, so the parallax is visible everywhere and not on one side only. Green `#34d399` is the surprise, roughly
one mark in twenty and never two adjacent; near white `#e8eefb` is rarer still, at most two per asset, in the near
layer, at opacity 0.82 or higher. Each large asset gets exactly one hero plus: the largest (`h` 5.0 or 5.1),
thickest (2.8) and brightest (opacity 0.87 to 0.90), on a deliberate compositional point.

## 10. Motion

### 10.1 Layer orbits

**Layers orbit. They do not drift out and back.** A `values="0 0; X Y; 0 0"` translate stops dead on the middle key
and retraces its own route in reverse, so the field pauses and rewinds twice a cycle: a twitch, not motion. Every
layer carries an `animateMotion` whose `path` starts at `0,0`, so the layer's rest position is exactly where the
plusses are authored; is built only from `C` cubic segments, because a straight run gives the eye a corner to catch
on and a corner is where a curve stops looking like drift; closes with `Z`, so travel is continuous, one way round,
forever; and carries no `calcMode` and no `keyTimes`, because a closed cubic already varies its own speed through
its control points and a spline on top reads as a stutter. These four are `hero.svg` verbatim.

```xml
<g><!-- LAYER 1: far, slowest, smallest orbit --><animateMotion dur="29s" repeatCount="indefinite" path="M0,0 C 6,-5 13,-2 14,4 C 15,10 8,14 0,12 C -7,10 -10,5 -8,1 C -6,-3 -3,-2 0,0 Z"/>
  <!-- l1 plusses go here --></g>
<g><!-- LAYER 2: mid, medium speed, opposite drift to layer 1 --><animateMotion dur="21s" repeatCount="indefinite" path="M0,0 C -9,-7 -19,-3 -20,6 C -21,15 -12,21 0,18 C 11,15 15,7 12,1 C 9,-5 4,-3 0,0 Z"/>
  <!-- l2 plusses go here --></g>
<g><!-- LAYER 3: near, fastest, largest orbit --><animateMotion dur="14s" repeatCount="indefinite" path="M0,0 C 14,-11 30,-5 32,9 C 34,23 19,32 1,28 C -17,24 -24,11 -19,2 C -14,-7 -7,-5 0,0 Z"/>
  <!-- l3 plusses go here --></g>
<g><!-- LAYER 4: counter, travels the opposite way round --><animateMotion dur="19s" repeatCount="indefinite" path="M0,0 C -12,8 -26,3 -28,-8 C -30,-19 -16,-27 -1,-24 C 14,-21 20,-10 16,-2 C 12,5 6,4 0,0 Z"/>
  <!-- l4 plusses go here --></g>
```

Layer 4 exists so the field never slides as one sheet: read the sign of its first control point against layer 3 and
you can see it goes round the other way. Give it to every canvas with the room. `mark.svg`, `signature.svg` and the
two dividers run three layers, the six buttons run two, `rail.svg` runs one.

| Band | Present in | `dur` | orbit extent, wide canvases | orbit extent, the dividers |
|---|---|---|---|---|
| L1 far | every asset with plusses | 26-34s | 25-33 by 13-28 | 17-19 by 2.6-3.2 |
| L2 mid | all but `rail.svg` | 17-22s | 34-45 by 17-33 | 19-21 by 4.4-5.0 |
| L3 near | wide canvases and the dividers | 13-15s | 54-70 by 23-52 | 28-32 by 5.6-6.6 |
| L4 counter | hero, five bands, strip, values, project-row | 19-26s | 35-43 by 18-35 | not used |
| per plus | roughly 1 mark in 3 | 7-13s | 13-20 by 11.5-20 | 6-11 by 4-5 |

Extent is the full width by full height of the closed path's bounding box, so visible travel is that figure, not
twice it. **Near layers orbit further and faster than far layers**, the same coupling as the size, weight and
opacity table. On the two dividers the vertical component is crushed because the canvas is only 26 to 30 tall.
Jitter durations per asset so no two files loop in lockstep: L1 from {27s, 29s, 30s, 31s}, L2 from {19s, 20s, 21s,
22s}, L3 from {13s, 14s, 15s}, L4 from {24s, 25s, 26s}, varying the control points too, so the jitter does not read
as the same shape at a different speed.

### 10.2 The per plus orbit

Roughly one plus in three gets its own small closed orbit on top of the layer orbit, so the field never moves as a
rigid constellation. The plus is drawn at the origin and its wrapper `<g>` carries the placement. Same three path
rules: start at `0,0`, `C` segments only, close with `Z`.

```xml
<g transform="translate(1359.3,431.9)">
  <animateMotion dur="7s" begin="0s" repeatCount="indefinite" path="M0,0 C 5.12,-3.84 10.24,0 8.96,5.12 C 7.68,10.24 1.28,11.52 -3.84,8.96 C -8.96,6.4 -7.68,1.28 0,0 Z"/>
  <path d="M-3.3 0H3.3M0 -3.3V3.3" stroke="#3b82f6" stroke-width="1.7" stroke-linecap="round" opacity="0.34"/>
</g>
```

`begin` is what keeps them from pulsing together. Stagger it from {0s, 0.6s, 1.2s, 2.4s, 3s, 3.6s, 4.8s, 5.4s, 6s,
7.2s, 8.4s, 9s}, and never give two adjacent marks the same `dur` and `begin` pair. A few of these wrapper groups
also carry a very slow `type="rotate"` roll, `values="0;360"` at 19s to 32s, `additive="sum"` so it stacks on the
orbit; on a plus with four fold symmetry this is almost subliminal, so use it on a handful per asset, never on a
whole layer. `rail.svg` is the one exception to the layer rule: at 46x72 there is no room for three layers, so its
three plusses sit in a single group that orbits at 30s over a 6.6 by 2.4 path, and all three marks carry their own
orbit on top, biased inward so an outward loop cannot clip the edge.

### 10.3 The twinkle

Roughly one plus in three carries its own opacity animate as a child of the path. The first and last `values` entry
must equal the path's static `opacity`, so the loop is seamless.

```xml
<path d="M409.6 88.2H417.8M413.7 84.1V92.3" stroke="#a855f7" stroke-width="2.2"
      stroke-linecap="round" opacity="0.58">
  <animate attributeName="opacity" values="0.58;0.21;0.58" dur="4.6s" begin="1.3s" repeatCount="indefinite"/>
</path>
```

`dur` between 3.2s and 7.5s, from {3.2s, 3.9s, 4.6s, 5.1s, 5.8s, 6.4s, 7.5s}. `begin` spread across 0s to 6s, from
{0s, 0.4s, 0.9s, 1.3s, 1.8s, 2.4s, 3.1s, 3.7s, 4.2s, 5.0s, 5.6s}. The dim value is roughly 0.36 times the bright
value: never animate to 0, never strobe. Two adjacent plusses must not share both `dur` and `begin`. Twinkles stay
linear, with no `calcMode`.

### 10.4 The scale breather

Near layer members only, and only where the canvas is large: `hero.svg` carries 8, `divider-wide.svg` 3,
`divider.svg` 2, and no other asset uses one. The plus is drawn at the origin so the scale is centred on it, and the
group carries the placement. `additive="sum"` stacks the scale on whatever the group already does.

```xml
<g transform="translate(742,196)">
  <path d="M-4.6 0H4.6M0 -4.6V4.6" stroke="#a855f7" stroke-width="2.6" stroke-linecap="round" opacity="0.74"/>
  <animateTransform attributeName="transform" type="scale" additive="sum"
    values="1;1.18;1" dur="6.2s" begin="0.8s" repeatCount="indefinite"
    calcMode="spline" keyTimes="0;0.5;1" keySplines="0.4 0 0.2 1; 0.4 0 0.2 1"/>
</g>
```

Put breather groups inside the near layer wrapper so they parallax too. `dur` from {5.5s, 5.9s, 6.2s, 6.7s, 7.0s},
`values` peak from {1.12, 1.15, 1.18, 1.22}.

### 10.5 The charge rail

Three strokes on the same path geometry, used in `rail.svg`, `signature.svg`, `divider.svg` and `divider-wide.svg`.

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

Wide faint under, thin bright over. Width ratio 2.75 to 1, opacity ratio 1 to 4.3. The travel of -36 equals the
dasharray sum, so the loop is seamless. Rates in use are 1.8s, 2.2s and 2.4s. Never add a blur filter: the sandwich
is the glow. Node pulses on the same assets run 1.8s to 2.4s with `keyTimes="0;0.2;1"` and staggered `begin`. The
two dividers apply the same dashoffset trick to their dashed hairline far more slowly: `1 7` gives a period of 8, so
the crawl is `to="-8"` over 4.6s or 5.2s.

### 10.6 Limits

Nothing faster than 1.6s except the charge rails at 1.8s. No flashing above 3 Hz. No opacity animation that reaches
0 quickly. Type never spins and the bolt never spins; the only full turns in the set are a gradient rotating and the
slow roll a few plus groups carry. The logo glow breathes at 7.4s on `hero.svg` and 8.2s on `mark.svg`.
`prefers-reduced-motion` cannot be honoured inside an `<img>` embedded SVG, which is why the amplitudes are small
and the durations long. Do not attempt a media query.

## 11. The asset set and its density

Twenty files live in `profile/assets/`, all referenced from `profile/README.md`. They are about the studio: its
mark, its name, what kind of outfit it is, what it stands for, how to reach it. Identity, not catalogue. Project
detail lives in the README's markdown text. Below is the plus count per file, measured off the shipped assets, where
a plus is one `<path>` whose `d` has an `H` subpath followed by a `V` subpath.

| Asset | Canvas | Total | l1 | l2 | l3 | l4 | per plus orbits | twinkles | breathers |
|---|---|---|---|---|---|---|---|---|---|
| `hero.svg` | 1600x480 | **154** | 64 | 51 | 27 | 12 | 45 | 53 | 8 |
| `values-band.svg` | 1200x260 | **62** | 24 | 19 | 9 | 10 | 19 | 19 | 0 |
| `signature.svg` | 1200x200 | **44** | 20 | 16 | 8 | - | 12 | 15 | 0 |
| `section-studio.svg` | 1200x130 | **44** | 17 | 14 | 7 | 6 | 13 | 14 | 0 |
| `section-work.svg` | 1200x130 | **44** | 17 | 14 | 7 | 6 | 13 | 14 | 0 |
| `section-server.svg` | 1200x130 | **44** | 17 | 14 | 7 | 6 | 13 | 14 | 0 |
| `section-community.svg` | 1200x130 | **43** | 17 | 14 | 7 | 5 | 13 | 16 | 0 |
| `section-inside.svg` | 1200x130 | **43** | 17 | 14 | 7 | 5 | 13 | 16 | 0 |
| `studio-strip.svg` | 1200x170 | **42** | 15 | 12 | 7 | 8 | 13 | 15 | 0 |
| `mark.svg` | 320x320 | **34** | 15 | 12 | 7 | - | 10 | 11 | 0 |
| `divider-wide.svg` | 1200x30 | **26** | 11 | 10 | 5 | - | 8 | 9 | 3 |
| `project-row.svg` | 1200x92 | **21** | 10 | 7 | - | 4 | 10 | 7 | 0 |
| `divider.svg` | 880x26 | **18** | 7 | 7 | 4 | - | 6 | 6 | 2 |
| `btn-discord.svg` | 300x84 | **12** | 6 | 6 | - | - | 4 | 7 | 0 |
| `btn-website.svg` | 300x84 | **12** | 6 | 6 | - | - | 4 | 7 | 0 |
| `btn-youtube.svg` | 300x84 | **12** | 6 | 6 | - | - | 4 | 7 | 0 |
| `btn-tiktok.svg` | 300x84 | **12** | 6 | 6 | - | - | 3 | 5 | 0 |
| `btn-status.svg` | 300x84 | **12** | 6 | 6 | - | - | 2 | 8 | 0 |
| `btn-email.svg` | 300x84 | **12** | 6 | 6 | - | - | 2 | 6 | 0 |
| `rail.svg` | 46x72 | **3** | 3 | - | - | - | 3 | 1 | 0 |

Set total: 694 marks. The five section bands sit within one mark of each other by design; the two that run the 56px
headline give a mark back to the counter layer to keep the type clear.

## 12. Shared defs

Every asset copies the fragment it needs, replacing `{P}` with its own id prefix. No file uses all of it:
`project-row.svg` takes no card gradient, the buttons add their own plate and wash gradients, the dividers take no
clip. Ids must be unique per file, so prefix everything. Prefixes in use: `hero`, `mark`, `sig`, `dv` (divider),
`dvw` (divider-wide), `rail`, `st` (studio band), `wk` (work band), `sv` (server band), `cm` (community band), `in`
(method band), `strip`, `val`, `pr` (project-row), `vfw` (website), `vfd` (discord), `vfy` (youtube), `tkf`
(tiktok), `sts` (status), `eml` (email).

**Every `stop-color` animate inside one gradient must share the same `dur`.** Give one stop a different `dur` and the
stops fall out of phase mid cycle, the ramp inverts for part of the loop, and the gradient tears. The rotate is
exempt: it drives `gradientTransform`, not a stop, so it may differ. The first and last entry of a stop's `values`
must equal that stop's own `stop-color`, or the loop jumps. `{P}Mark` runs 15s stops with a 23s rotation, slowed to
34s and 41s on the five bands so the ghost does not compete with the headline. `{P}Word` runs 11s stops with a 29s
rotation, and `section-server.svg` is the one file whose `{P}Word` leads cyan, `#47d1ff` / `#9beaff` / `#1273ea`.

```svg
<defs>
  <!-- Mark : the winged bolt's live fill. Every stop animates and the whole gradient rotates,
       so the mark never sits on one colour. -->
  <linearGradient id="{P}Mark" gradientUnits="objectBoundingBox" x1="0" y1="0" x2="1" y2="1">
    <stop offset="0" stop-color="#f4f6fb"><animate attributeName="stop-color" dur="15s"
      repeatCount="indefinite" values="#f4f6fb;#e9d8ff;#d8f4ff;#ffe4f2;#f4f6fb"/></stop>
    <stop offset="0.45" stop-color="#a855f7"><animate attributeName="stop-color" dur="15s"
      repeatCount="indefinite" values="#a855f7;#47d1ff;#ff2e4d;#8b5cff;#a855f7"/></stop>
    <stop offset="1" stop-color="#6d28d9"><animate attributeName="stop-color" dur="15s"
      repeatCount="indefinite" values="#6d28d9;#1273ea;#a02bfe;#0ea5b7;#6d28d9"/></stop>
    <animateTransform attributeName="gradientTransform" type="rotate" dur="23s"
      repeatCount="indefinite" values="0 0.5 0.5; 360 0.5 0.5"/>
  </linearGradient>

  <!-- Word : the same idea for the accent half of a two tone headline. -->
  <linearGradient id="{P}Word" x1="0" y1="0" x2="1" y2="0">
    <stop offset="0" stop-color="#a855f7"><animate attributeName="stop-color" dur="11s"
      repeatCount="indefinite" values="#a855f7;#8b5cff;#47d1ff;#a855f7"/></stop>
    <stop offset="0.5" stop-color="#c9a6ff"><animate attributeName="stop-color" dur="11s"
      repeatCount="indefinite" values="#c9a6ff;#7fe3ff;#c9a6ff;#c9a6ff"/></stop>
    <stop offset="1" stop-color="#8b5cff"><animate attributeName="stop-color" dur="11s"
      repeatCount="indefinite" values="#8b5cff;#47d1ff;#a855f7;#8b5cff"/></stop>
    <animateTransform attributeName="gradientTransform" type="rotate" dur="29s"
      repeatCount="indefinite" values="0 0.5 0.5; 360 0.5 0.5"/>
  </linearGradient>

  <linearGradient id="{P}Cy" x1="0" y1="0" x2="1" y2="1">
    <stop offset="0" stop-color="#47d1ff"/><stop offset="1" stop-color="#1273ea"/></linearGradient>
  <linearGradient id="{P}Vi" x1="0" y1="0" x2="1" y2="1">
    <stop offset="0" stop-color="#a855f7"/><stop offset="1" stop-color="#6d28d9"/></linearGradient>
  <linearGradient id="{P}Bg" x1="0" y1="0" x2="1" y2="1">
    <stop offset="0" stop-color="#0d1a2e"/><stop offset="1" stop-color="#0a1425"/></linearGradient>
  <linearGradient id="{P}Spark" x1="0" y1="0" x2="1" y2="1">
    <stop offset="0" stop-color="#9beaff"/><stop offset="0.55" stop-color="#47d1ff"/>
    <stop offset="1" stop-color="#7aa2ff"/></linearGradient>
  <radialGradient id="{P}Top" cx="0.5" cy="0" r="1">
    <stop offset="0" stop-color="#ffffff" stop-opacity="0.075"/>
    <stop offset="1" stop-color="#ffffff" stop-opacity="0"/></radialGradient>

  <!-- Dots : the dot matrix, as a pattern so it costs about 120 bytes and not 70 KB. -->
  <pattern id="{P}Dots" width="14" height="14" patternUnits="userSpaceOnUse">
    <circle cx="7" cy="7" r="1.1" fill="#9aa8c4" opacity="0.13"/></pattern>
  <pattern id="{P}DotsFine" width="16" height="16" patternUnits="userSpaceOnUse">
    <circle cx="4" cy="4" r="0.8" fill="#9aa8c4" opacity="0.07"/></pattern>

  <!-- FadeR : edge fade for the dot field, in objectBoundingBox units, so it is canvas-agnostic:
       apply mask="url(#{P}FadeR)" to any rect and it fades left to right. -->
  <linearGradient id="{P}MaskH" x1="0" y1="0" x2="1" y2="0">
    <stop offset="0" stop-color="#000000"/><stop offset="0.34" stop-color="#3a3a3a"/>
    <stop offset="0.72" stop-color="#c8c8c8"/><stop offset="1" stop-color="#ffffff"/></linearGradient>
  <mask id="{P}FadeR" maskContentUnits="objectBoundingBox">
    <rect x="0" y="0" width="1" height="1" fill="url(#{P}MaskH)"/></mask>

  <!-- Soft : the logo glow. SoftTight : accent-rule bloom. -->
  <filter id="{P}Soft" x="-60%" y="-60%" width="220%" height="220%">
    <feGaussianBlur stdDeviation="7"/></filter>
  <filter id="{P}SoftTight" x="-60%" y="-60%" width="220%" height="220%">
    <feGaussianBlur stdDeviation="2.6"/></filter>
</defs>
```

## 13. File constraints

1. Every SVG is 100 percent self contained. No external font, no external image, no cross file `<use>`, no `data:`
   URI image, no `@import`. Internal `<defs>`, gradients, filters, masks, clipPaths and patterns only.
2. SMIL is the animation primitive: `<animate>`, `<animateTransform>`, `<animateMotion>`, `<set>`. No JavaScript, no
   `:hover`, no CSS `transition`. Inline `<style>` with `@keyframes` is permitted but this set does not use it, so
   there is one technique to review.
3. Paint your own opaque background across the full viewBox and draw your own rounded corners. Never rely on the
   page canvas, and never use `@media (prefers-color-scheme: ...)` inside the SVG. The two dividers are the
   deliberate exception: they are strokes only, at mid luminance, so they read on either theme.
4. `viewBox` present, no fixed pixel `width` or `height` on the `<svg>` root. Design so it stays legible at 350px
   wide: that is why band eyebrows are 10.5px and not 9.
5. In the README every studio SVG gets `width` only, never `height`, or GitHub injects a muted grey box behind the
   asset. Absolute raw URLs only, `https://raw.githubusercontent.com/Vision-Force/.github/main/profile/assets/<name>.svg`.
6. Meaningful `alt` on every image, empty `alt` on the two dividers and the rail.
7. Keep each file under 50 KB, hard stop 100 KB. `hero.svg` is the largest at 46 KB. This is why the dot matrix is a
   `<pattern>` and not 2,000 circles.

## 14. Voice

- Short sentences, around 11 words on average. Second person where it addresses a reader.
- Sentence case. Acronyms stay upper: UEFN, LUX3, UE5. Headings take no full stop, body copy does.
- The server project is **Rocket Racing Reborn**, codename **Meridian**. Use the display name in copy; the codename
  only where the codename is the subject. Never claim a shipped feature for it: it is early and in development.
- Rocket Racing Reborn copy says: an original re-implementation of network services; players bring their own
  archived client; no download link of any kind; not affiliated with or endorsed by Epic Games; Fortnite and Unreal
  are trademarks of Epic Games, Inc; non commercial. That note gets a real heading and normal body size.
