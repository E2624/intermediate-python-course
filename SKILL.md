# Skill: coastal-modern-palette

## Metadata

```yaml
name: coastal-modern-palette
version: 1.0.0
description: >
  Apply when the user mentions "ma palette", "coastal", "soft modern", "design
  épuré", asks to build a landing/UI/component, or requests a color recommendation.
  Encodes the full Coastal Modern design system: tokens, snippets, hierarchy rules,
  WCAG contrasts, dark mode, system states, and data-viz order.
```

---

## 1. Raw Palette

| Role | Name | Hex | HSL |
|---|---|---|---|
| Primary teal | Seafoam | `#7FAFB0` | 181 26% 60% |
| Primary dark | Deep teal | `#3D7F82` | 182 34% 37% |
| Background | Warm white | `#F7F4F0` | 33 24% 96% |
| Surface | Pure white | `#FFFFFF` | — |
| Text primary | Ink | `#1E2B2E` | 189 22% 15% |
| Text secondary | Slate | `#5E7578` | 185 13% 41% |
| Accent | Caramel | `#C4874A` | 30 52% 53% |
| Border | Sand | `#DDD8D0` | 33 16% 84% |

---

## 2. UI Design Tokens

```
--color-primary:          #7FAFB0;
--color-primary-dark:     #3D7F82;
--color-bg:               #F7F4F0;
--color-surface:          #FFFFFF;
--color-text:             #1E2B2E;
--color-text-secondary:   #5E7578;
--color-accent:           #C4874A;
--color-border:           #DDD8D0;
```

---

## 3. CSS Variables Snippet

```css
:root {
  --color-primary:          #7FAFB0;
  --color-primary-dark:     #3D7F82;
  --color-bg:               #F7F4F0;
  --color-surface:          #FFFFFF;
  --color-text:             #1E2B2E;
  --color-text-secondary:   #5E7578;
  --color-accent:           #C4874A;
  --color-border:           #DDD8D0;

  /* Semantic aliases */
  --color-cta-bg:           var(--color-primary);
  --color-cta-bg-hover:     var(--color-primary-dark);
  --color-cta-text:         #FFFFFF;
  --color-link:             var(--color-primary-dark);
  --color-divider:          var(--color-border);
}
```

---

## 4. Tailwind Config

```js
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      colors: {
        primary:    '#7FAFB0',
        'primary-dark': '#3D7F82',
        bg:         '#F7F4F0',
        surface:    '#FFFFFF',
        ink:        '#1E2B2E',
        slate:      '#5E7578',
        caramel:    '#C4874A',
        sand:       '#DDD8D0',
      },
    },
  },
}
```

**Arbitrary classes for Claude.ai artifacts:**
```
bg-[#7FAFB0]   text-[#1E2B2E]   border-[#DDD8D0]
bg-[#F7F4F0]   text-[#5E7578]   bg-[#C4874A]
```

---

## 5. Proportion Rule — 80 / 15 / 5

| Weight | Colors | Use |
|---|---|---|
| **80 %** | Warm white `#F7F4F0`, Pure white `#FFFFFF`, Sand `#DDD8D0` | Backgrounds, cards, dividers |
| **15 %** | Seafoam `#7FAFB0`, Deep teal `#3D7F82` | CTAs, nav, active states, icons |
| **5 %** | Caramel `#C4874A` | Tags, badges, highlights, a single accent CTA |

> Caramel must never appear on more than one element per viewport. Overuse destroys the coastal calm.

---

## 6. WCAG Contrast Rules

| Foreground | Background | Ratio | WCAG | Minimum usage |
|---|---|---|---|---|
| `#FFFFFF` on `#3D7F82` | Deep teal | 4.8 : 1 | AA | Body ≥ 16 px or bold ≥ 14 px |
| `#FFFFFF` on `#7FAFB0` | Seafoam | 2.8 : 1 | fail | Large decorative text only (≥ 24 px, non-essential) |
| `#1E2B2E` on `#7FAFB0` | Seafoam | 5.3 : 1 | AA | Preferred for text on teal chips/badges |
| `#1E2B2E` on `#F7F4F0` | Warm white | 13.2 : 1 | AAA | Body copy — default |
| `#5E7578` on `#F7F4F0` | Warm white | 5.1 : 1 | AA | Captions, meta, secondary text |
| `#FFFFFF` on `#C4874A` | Caramel | 3.1 : 1 | fail body | Large bold text only (≥ 18 px bold) |
| `#1E2B2E` on `#C4874A` | Caramel | 6.8 : 1 | AA | Preferred text on caramel badges |

**Practical rules:**
- Never white body text on Seafoam — use Ink `#1E2B2E` instead.
- CTA buttons: Deep teal background + white text is the only fully AA-compliant combo.
- Caramel badges: always pair with Ink text, not white.

---

## 7. Typography Pairing

| Role | Font | Weight | Size |
|---|---|---|---|
| Display / H1 | Playfair Display | 700 | 48–64 px |
| Headings H2–H4 | Inter or DM Sans | 600 | 24–36 px |
| Body | Inter | 400 | 16–18 px |
| Caption / meta | Inter | 400 | 12–14 px |
| CTA label | Inter | 600 | 15–16 px, letter-spacing 0.02em |

---

## 8. Shape & Shadow Language

- **Border radius:** `12px` cards, `8px` inputs, `999px` pills/tags, `4px` tooltips.
- **Shadows:** soft and warm — avoid cold grey shadows.
  ```css
  --shadow-sm: 0 1px 3px rgba(30, 43, 46, 0.08);
  --shadow-md: 0 4px 12px rgba(30, 43, 46, 0.10);
  --shadow-lg: 0 8px 24px rgba(30, 43, 46, 0.12);
  ```
- **Borders:** `1px solid #DDD8D0` — never black borders.
- **Icons:** stroke-based (Lucide / Phosphor), 1.5 px stroke, never filled unless active state.

---

## 9. Dark Mode Variant

```css
@media (prefers-color-scheme: dark) {
  :root {
    --color-bg:               #121B1C;
    --color-surface:          #1C2A2C;
    --color-text:             #E8F0F0;
    --color-text-secondary:   #8AABAC;
    --color-primary:          #7FAFB0;   /* unchanged — reads well on dark */
    --color-primary-dark:     #5E9EA0;   /* lightened for dark bg contrast */
    --color-accent:           #D4975A;   /* caramel lightened +10% lightness */
    --color-border:           #2C3E40;
  }
}
```

---

## 10. System State Palette

| State | Background | Text / Icon | Border |
|---|---|---|---|
| Success | `#E6F4F1` | `#2A7A6A` | `#A8D8CF` |
| Warning | `#FDF3E3` | `#8A5A1A` | `#F0D4A0` |
| Error | `#FAE8E6` | `#9B3A32` | `#E8B8B4` |
| Info | `#E8F2F3` | `#3D7F82` | `#A8CFD1` |

> Derived from the palette hue family — no pure red/green/yellow. Feels coastal, not alarming.

---

## 11. Data-Viz Color Order

For multi-series charts, use in this order to maximise distinction while staying on-brand:

1. `#3D7F82` Deep teal (primary series)
2. `#C4874A` Caramel (secondary series)
3. `#7FAFB0` Seafoam (tertiary)
4. `#8AABAC` Muted teal
5. `#E0B080` Light caramel
6. `#5E7578` Slate (neutral 6th series)

---

## 12. Delivery Checklist

- [ ] CSS variables added to `:root` in global stylesheet
- [ ] Tailwind config extended with palette tokens
- [ ] CTA buttons use `primary-dark` bg + white text (AA compliant)
- [ ] No white text on `#7FAFB0` in body copy
- [ ] Caramel accent appears ≤ 1× per viewport
- [ ] Dark mode override block present
- [ ] System state colours verified against palette
- [ ] Shadows use warm tint (`rgba(30, 43, 46, …)`) not grey
- [ ] Border radius consistent: 12 / 8 / 999 / 4 px
- [ ] Icons: stroke style, 1.5 px weight
