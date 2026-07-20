# Theme & Frontend Color Standards

## Purpose
Define a reusable, single-brand-hue color recipe for theming CSS-variable-driven UIs (shadcn/Tailwind or equivalent).

## Scope
CSS custom-property color tokens — background, foreground, card, primary, accent, border, ring, status/severity colors — in Tailwind/shadcn-style or equivalent design-token systems.

## Rules

### Always
- Derive every themed neutral (`background`, `foreground`, `card`, `border`, `muted`) from the single brand hue `H_b` (± a few degrees), never from a desaturated gray.
- Keep foreground text off the extremes: never `L 0-5%` or `L 95-100%`.
- Keep dark-mode `background` off near-black (`L < 8%`) and light-mode `background` off stark white (`L > 98%` — reserve that for elevated `card` surfaces only).
- Drive all interactive brand presence — primary actions, active nav state, focus rings, links — from the one brand hue at varying `L`.
- Give `ring` the same value as `primary`.
- Give `accent` (hover/active surface) a visible tint of the brand hue, not plain gray.
- Elevate `card` via lightness — one step lighter (light mode) or lighter-than-bg (dark mode) than the page background — instead of heavy drop shadows.
- Keep `destructive`/`warning` semantically separate from the brand hue; `info` may reuse the brand hue since blue reads universally as "info."
- Pair `warning` (amber) with a dedicated `-foreground` token — white-on-amber fails WCAG.
- Route all themed color usage through the CSS-variable tokens, not hardcoded utility classes.
- Verify contrast in both themes: body text ≥ 4.5:1, badge/small-bold text ≥ 3:1 — check `warning` and `info` badges specifically, they fail most often.
- If the target repo already has a themed `:root`/`.dark` block, re-derive it in place by substituting `H_b` rather than rebuilding the palette from scratch.

### Never
- Introduce a second brand accent hue "for variety" — get more color from saturation/lightness variation on the single hue, or from status colors.
- Use `0%` saturation anywhere in a themed surface token (`background`, `card`, `border`, `muted`) — treat it as a defect, not a stylistic choice.
- Hardcode `bg-black`, `text-white`, or `gray-*`/`zinc-*`/`slate-*`/`neutral-*` utility classes in app/component code. Modal scrims (e.g. `bg-black/80`) are the one sanctioned pure-black exception — they're a compositing overlay, not a themed surface.
- Duplicate the CSS-variable palette inside `tailwind.config` (or equivalent) color config.
- Repurpose a status hue (`destructive`, `warning`) as a decorative accent.

### Ask Before
- Picking the brand hue if the user hasn't specified one — confirm the target hex/HSL before generating tokens.

## Token Recipe (HSL, `H S% L%`)

Given brand `H_b S_b L_b`:

| Token | Light | Dark |
|---|---|---|
| `background` | `H_b±4 S_b-10% L 93-95%` | `H_b S_b-10% L 10-13%` |
| `card` | `H_b-8 S_b L 98-99%` | `H_b S_b-10% L 14-16%` (one step lighter than bg) |
| `foreground` | `H_b S_b-15% L 18-22%` | `H_b-2 S_b-15% L 87-90%` |
| `primary` | brand as-is | brand, `L` raised ~20pt for legibility (`L 60-68%`) |
| `secondary` / `muted` | `H_b S_b-15% L 88-92%` | `H_b S_b-15% L 17-20%` |
| `muted-foreground` | `H_b S_b-25% L 40-46%` | `H_b S_b-25% L 58-64%` |
| `accent` | brand tint, `L 92-94%` (visible tint, not gray) | brand shade, `L 22-26%` |
| `border` / `input` | `H_b S_b-20% L 80-84%` | `H_b S_b-20% L 20-23%` |
| `ring` | = `primary` | = `primary` |
| `destructive` | `H 4 S~62% L~51%` | same, `L` +2-4pt |

Status/log severity (kept off the brand hue except `info`):

- `debug` → neutral, `S~10% L~48%` (light) / `L~58%` (dark)
- `info` → brand hue, `L~55%` (light) / `L~65%` (dark)
- `warning` → amber `H~36 S~80% L~46%` (light) / `L~56%` (dark) — pair with a dedicated `-foreground` token
- `error` → = `destructive`

## Verification Checklist

- [ ] Every token in `:root` / `.dark` (or platform equivalent) carries the brand hue or a deliberate status hue — no `0%` saturation.
- [ ] `grep -rE 'bg-black|text-white|gray-[0-9]|zinc-[0-9]|slate-[0-9]|neutral-[0-9]'` over component code returns only sanctioned scrim exceptions.
- [ ] Contrast verified in both themes for body text, badges, and severity indicators.
- [ ] Visual check in both light and dark: sidebar/nav active state, primary button, focus ring, at least one data table/card list, and any severity/status badges.
