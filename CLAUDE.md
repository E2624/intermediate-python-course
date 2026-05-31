# Design System — Coastal Modern Palette

Apply this design system whenever producing any UI, component, landing page, or visual output.

## Tokens

| Token | Hex |
|---|---|
| primary | `#7FAFB0` |
| primary-dark | `#3D7F82` |
| bg | `#F7F4F0` |
| surface | `#FFFFFF` |
| text | `#1E2B2E` |
| text-secondary | `#5E7578` |
| accent | `#C4874A` |
| border | `#DDD8D0` |

## CSS `:root`

```css
:root {
  --color-primary:        #7FAFB0;
  --color-primary-dark:   #3D7F82;
  --color-bg:             #F7F4F0;
  --color-surface:        #FFFFFF;
  --color-text:           #1E2B2E;
  --color-text-secondary: #5E7578;
  --color-accent:         #C4874A;
  --color-border:         #DDD8D0;
  --shadow-sm: 0 1px 3px rgba(30,43,46,0.08);
  --shadow-md: 0 4px 12px rgba(30,43,46,0.10);
  --shadow-lg: 0 8px 24px rgba(30,43,46,0.12);
}
```

## Tailwind

```js
colors: {
  primary: '#7FAFB0', 'primary-dark': '#3D7F82',
  bg: '#F7F4F0', surface: '#FFFFFF',
  ink: '#1E2B2E', slate: '#5E7578',
  caramel: '#C4874A', sand: '#DDD8D0',
}
```

Arbitrary classes for artifacts: `bg-[#7FAFB0]` `text-[#1E2B2E]` `border-[#DDD8D0]` `bg-[#C4874A]`

## Proportion Rule — 80 / 15 / 5

- **80 %** — `#F7F4F0` `#FFFFFF` `#DDD8D0` — backgrounds, cards, dividers
- **15 %** — `#7FAFB0` `#3D7F82` — CTAs, nav, icons, active states
- **5 %** — `#C4874A` — one accent element per viewport maximum

## WCAG Rules

- Body text: `#1E2B2E` on `#F7F4F0` → 13.2:1 ✓ always safe
- CTA button: `#3D7F82` bg + `#FFFFFF` text → 4.8:1 AA ✓
- Text on teal chip: `#1E2B2E` on `#7FAFB0` → 5.3:1 AA ✓
- Text on caramel: `#1E2B2E` on `#C4874A` → 6.8:1 AA ✓
- **Never** white text on `#7FAFB0` (ratio 2.8:1, fails)
- **Never** white body text on `#C4874A` (ratio 3.1:1, fails)

## Typography

| Role | Font | Weight | Size |
|---|---|---|---|
| Display / H1 | Playfair Display | 700 | 48–64 px |
| H2–H4 | Inter or DM Sans | 600 | 24–36 px |
| Body | Inter | 400 | 16–18 px |
| CTA | Inter | 600 | 15–16 px, ls 0.02em |

## Shapes & Shadows

- Radius: `12px` cards · `8px` inputs · `999px` pills · `4px` tooltips
- Borders: `1px solid #DDD8D0` — no black borders
- Shadows: warm tint `rgba(30,43,46,…)` only
- Icons: stroke-based (Lucide/Phosphor), 1.5 px, filled only when active

## Dark Mode

```css
@media (prefers-color-scheme: dark) {
  :root {
    --color-bg:             #121B1C;
    --color-surface:        #1C2A2C;
    --color-text:           #E8F0F0;
    --color-text-secondary: #8AABAC;
    --color-primary:        #7FAFB0;
    --color-primary-dark:   #5E9EA0;
    --color-accent:         #D4975A;
    --color-border:         #2C3E40;
  }
}
```

## System States

| State | Bg | Text | Border |
|---|---|---|---|
| Success | `#E6F4F1` | `#2A7A6A` | `#A8D8CF` |
| Warning | `#FDF3E3` | `#8A5A1A` | `#F0D4A0` |
| Error | `#FAE8E6` | `#9B3A32` | `#E8B8B4` |
| Info | `#E8F2F3` | `#3D7F82` | `#A8CFD1` |

## Data-Viz Order

1. `#3D7F82` 2. `#C4874A` 3. `#7FAFB0` 4. `#8AABAC` 5. `#E0B080` 6. `#5E7578`
