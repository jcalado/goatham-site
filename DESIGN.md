# DESIGN.md

Visual system for the GoatHam promotional site. Colours are sampled from
`design/brand/app_icon.png` in the app repository, not chosen beside it.

## Theme

**Light, on cream.** The scene that forces it: a licensed operator at the
kitchen table on a Thursday evening, laptop open, planning Saturday's summit.
Daylight thinking, aspirational, unhurried. A dark surface would put the page in
the CRT lane the brand exists to avoid, and would fight an icon whose largest
single colour is cream sky.

## Colour

Strategy: **full palette**, four named roles, each with one job. Cream holds the
ground, navy holds the ink and the drenched bands, the sun is the only signal
colour, slate supplies atmospheric depth.

| Token | OKLCH | Hex | Role |
|---|---|---|---|
| `--cream` | `oklch(0.975 0.020 84.6)` | `#fdf6e8` | Page ground. Sampled from the icon's sky. |
| `--cream-shade` | `oklch(0.945 0.024 82)` | | Paper shade, section alternation |
| `--navy` | `oklch(0.247 0.031 262.6)` | `#192130` | Ink, silhouettes, drenched sections |
| `--navy-soft` | `oklch(0.42 0.028 260)` | | Secondary text on cream |
| `--sun` | `oklch(0.698 0.163 44.3)` | `#ee773e` | The one signal: actions, the sun, live marks |
| `--slate` | `oklch(0.593 0.032 250)` | `#708091` | Mid ridge, borders, tertiary text |
| `--slate-pale` | `oklch(0.756 0.016 248)` | `#a8b1ba` | Far ridge, hairlines |

Rules:

- The sun is never a background for body text and never a second accent. It
  marks the primary action, the live dot, and the sun in the artwork.
- Band colours from the app (`core/util/band.dart`) appear only inside device
  frames. They carry meaning in the product and would be noise as site chrome.
- No pure black or white anywhere. Every neutral is tinted toward the navy hue.

## Typography

Selection followed the brand register's procedure. Voice words: printed,
weathered, deliberate. Reflex picks (Inter, Space Grotesk, DM Sans) were
rejected as training-data defaults.

- **Display: Anton.** One weight, ultra-heavy condensed grotesque. It is the
  voice of a screenprinted poster headline, set enormous and tight
  (`letter-spacing: -0.02em`), always in sentence or upper case, never italic.
- **Body and labels: Archivo.** A grotesque drawn for print with enough
  mechanical texture to sit under Anton without looking like app UI.

Scale is fluid `clamp()`, ratio 1.33 between steps. Body copy caps at 68ch.

## Texture

A single SVG `feTurbulence` grain at 3.5% opacity over the whole page,
`mix-blend-mode: multiply`. It stands in for screenprint tooth. It is fixed, not
animated, and it is the only decorative effect on the page. No blur, no glass,
no gradient text.

## Layout

Asymmetric. A 12-column grid on wide viewports with deliberate breaks: the hero
type sits left of centre, the artwork runs full bleed edge to edge beneath it,
and the three feature acts alternate sides rather than repeating a card row.

Spacing varies for rhythm: `clamp(5rem, 12vh, 9rem)` between sections,
tight groupings inside them.

## Components

- **Device frame.** Navy bezel, 2.2rem radius, a real screenshot inside. The
  frame is what separates the app's green interface from the site's palette.
- **Ridge rule.** A flat SVG mountain silhouette used as a section divider in
  place of a horizontal line, in slate or navy.
- **Action.** Solid sun fill, navy label, no radius above 4px. The secondary
  action is a navy hairline outline, never a second filled colour.

## Motion

One orchestrated page load: the hero type and artwork rise 12px and fade over
700ms with `cubic-bezier(0.22, 1, 0.36, 1)`, staggered 60ms. Sections reveal on
scroll with the same curve. Nothing bounces, nothing loops, and everything is
disabled under `prefers-reduced-motion`.
