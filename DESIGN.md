# DESIGN.md — Frame

> Frame v1.0 · A design system blueprint by [Design x Machine](https://designxmachine.beehiiv.com)
> Figma file: ❖ Frame UI – PRO LITE (FREE) · Tokens: `tokens.json` · Changes: `CHANGELOG.md`

This file describes the Frame design system for AI coding agents and the humans working with them.

It is the written half of the system. Figma is where the system is designed. This file is where it is explained. Same tokens. Same names. Same rules.

If something you need isn't in here, don't guess. Ask.

---

## 1. How to use this file (for AI agents)

Read this before you write any UI code in this repository.

**Always**
- Use tokens. Every colour, space, radius, font and shadow in this system has a name. Use the name.
- Use semantic colour tokens (`color.text.primary`, `color.brand.primary`). Never primitives (`blue.600`) in component code.
- Use the components listed in section 7 before building anything new.
- Match the variant names exactly as written here. `Style=Primary`, not `variant="main"`.
- Support Light and Dark. Semantic tokens already switch; don't hardcode either theme.

**Never**
- Hardcode hex values, pixel values or font sizes.
- Invent a new token, variant or component without flagging it.
- Use a primitive colour directly in a component.
- Override a component's internal spacing to "make it fit". Change the layout around it instead.

**When something is missing**
1. Stop.
2. Say what's missing and what you would need.
3. Suggest the closest existing token or component.
4. Wait, or use the closest match and leave a `// TODO(design):` comment explaining the gap.

---

## 2. Token architecture

Three layers. Components only touch the middle one.

| Layer | What it holds | Who uses it |
|---|---|---|
| **Primitives** | Raw values: `neutral.50`–`950`, `blue`, `green`, `red`, `amber` (50–900), `white`, `black` | Semantic tokens only |
| **Semantic** | Meaning: `bg`, `surface`, `text`, `border`, `brand`, `status`. Has **Light** and **Dark** modes | Components and layouts |
| **Scales** | `space`, `radius`, `type`, `shadow` | Components and layouts |

### Naming across layers

| Figma variable | DESIGN.md / tokens.json | CSS variable |
|---|---|---|
| `brand/primary` | `color.brand.primary` | `var(--color-brand-primary)` |
| `text/primary` | `color.text.primary` | `var(--color-text-primary)` |
| `border/default` | `color.border.default` | `var(--color-border-default)` |
| `status/error` | `color.status.error` | `var(--color-status-error)` |
| `space/4` | `space.4` | `var(--space-4)` |
| `radius/md` | `radius.md` | `var(--radius-md)` |
| `Label/Medium` | `type.label.md` | `var(--type-label-md)` |
| `Shadow/MD` | `shadow.md` | `var(--shadow-md)` |

Rule: Figma uses `/`, tokens use `.`, CSS uses `-` with a category prefix. The words stay the same.

---

## 3. Colour

### Semantic tokens

| Token | Light | Dark | Use for |
|---|---|---|---|
| `color.bg.primary` | white | neutral.950 | Page background |
| `color.bg.secondary` | neutral.50 | neutral.900 | Subtle sections, table headers, hover |
| `color.bg.tertiary` | neutral.100 | neutral.800 | Code blocks, wells, pressed states |
| `color.surface.default` | white | neutral.900 | Cards, modals, nav bars |
| `color.surface.elevated` | white | neutral.800 | Toasts, dropdown menus, popovers |
| `color.text.primary` | neutral.900 | neutral.50 | Headings, body, input values |
| `color.text.secondary` | neutral.600 | neutral.400 | Descriptions, helper text, inactive nav |
| `color.text.tertiary` | neutral.400 | neutral.600 | Placeholders, disabled text, metadata |
| `color.text.inverse` | white | neutral.950 | Text on brand or dark fills |
| `color.border.default` | neutral.200 | neutral.700 | Inputs, cards, dividers that need to be seen |
| `color.border.subtle` | neutral.100 | neutral.800 | Table rows, quiet separators |
| `color.border.strong` | neutral.300 | neutral.600 | Hover borders, emphasis |
| `color.brand.primary` | blue.600 | blue.500 | Primary actions, focus, selected states |
| `color.brand.secondary` | blue.50 | blue.900 | Selected backgrounds, info fills, avatars |
| `color.brand.text` | blue.600 | blue.400 | Links, active tabs, brand-coloured text |
| `color.status.success` | green.600 | green.500 | Success icons and text |
| `color.status.success-bg` | green.50 | green.900 | Success fills |
| `color.status.error` | red.600 | red.500 | Errors, destructive actions |
| `color.status.error-bg` | red.50 | red.900 | Error fills |
| `color.status.warning` | amber.600 | amber.500 | Warnings |
| `color.status.warning-bg` | amber.50 | amber.900 | Warning fills |

### Colour rules
- Text on `color.brand.primary` is always `color.text.inverse`.
- Status colours are for status. Don't use `color.status.success` as a decorative green.
- Pair every status colour with an icon or label. Colour is never the only signal.
- Body text uses `color.text.primary` or `color.text.secondary`. `color.text.tertiary` is not for anything a user must read.

---

## 4. Typography

One family: **Inter**.

| Token | Weight | Size / line height | Use for |
|---|---|---|---|
| `type.display.lg` | Bold | 56 / 64 | Marketing hero only |
| `type.display.md` | Bold | 44 / 52 | Page heroes, docs titles |
| `type.display.sm` | Semi Bold | 36 / 44 | Large section intros |
| `type.heading.h1` | Semi Bold | 32 / 40 | Page title (one per page) |
| `type.heading.h2` | Semi Bold | 24 / 32 | Section titles |
| `type.heading.h3` | Semi Bold | 20 / 28 | Sub-sections, modal titles |
| `type.heading.h4` | Medium | 18 / 26 | Card titles, small group titles |
| `type.body.lg` | Regular | 18 / 28 | Intro paragraphs |
| `type.body.md` | Regular | 16 / 24 | Default body text |
| `type.body.sm` | Regular | 14 / 20 | Dense UI text, descriptions, table cells |
| `type.label.lg` | Medium | 16 / 24 | Large buttons |
| `type.label.md` | Medium | 14 / 20 | Buttons, form labels, nav items, tabs |
| `type.label.sm` | Medium | 12 / 16 | Small buttons, badges, tags |
| `type.caption` | Regular | 12 / 16 | Helper text, error messages, timestamps |
| `type.overline` | Semi Bold | 11 / 16 | Eyebrow labels above titles (uppercase) |

### Type rules
- One `heading.h1` per page.
- Don't skip heading levels for visual size. Choose the level for structure, then the token.
- Interactive text (buttons, tabs, nav, labels) uses `label.*`. Reading text uses `body.*`.

---

## 5. Spacing, radius and elevation

### Spacing — 4px base

`space.0` 0 · `space.1` 4 · `space.2` 8 · `space.3` 12 · `space.4` 16 · `space.5` 20 · `space.6` 24 · `space.8` 32 · `space.10` 40 · `space.12` 48 · `space.16` 64 · `space.20` 80 · `space.24` 96

- Inside components: `space.1`–`space.4`.
- Between components in a group: `space.3`–`space.6`.
- Between sections: `space.8` and up.
- No values outside the scale. If 10px feels right, use 8 or 12.

### Radius

`radius.none` 0 · `radius.sm` 4 · `radius.md` 8 · `radius.lg` 12 · `radius.xl` 16 · `radius.2xl` 24 · `radius.full` 9999

- Controls (buttons, inputs, selects, nav items, alerts, toasts): `radius.md`
- Containers (cards, modals): `radius.lg`
- Pills (badges, tags, toggles, avatars): `radius.full`
- Small inner elements (checkbox, icon frames): `radius.sm`

### Elevation

| Token | Use for |
|---|---|
| `shadow.xs` | Inputs, subtle lift |
| `shadow.sm` | Cards at rest |
| `shadow.md` | Elevated cards, dropdown menus |
| `shadow.lg` | Toasts, popovers |
| `shadow.xl` | Modals |
| `shadow.2xl` | Rare. Large overlays only |

In Dark mode, prefer `color.surface.elevated` over stronger shadows to show depth.

---

## 6. Layout

- Grid: 12 columns on desktop, 8pt baseline.
- Pages sit on `color.bg.primary`. Content groups sit on `color.surface.default`.
- Top navigation is 64px high. Sidebar navigation items are 240px wide.
- Keep line length for reading text under ~75 characters.

---

## 7. Components

Frame ships 21 components. Property names below match Figma exactly.

### Actions

#### Button
Use for actions. Links that go somewhere are links, not buttons.

- **Style**: `Primary` | `Secondary` | `Outline` | `Ghost` | `Danger`
- **Size**: `SM` | `MD` | `LG`
- **State**: `Default` | `Disabled`
- **Props**: `Label` (text), `Show Icon Left`, `Show Icon Right` (boolean)
- **Tokens**: Primary fill `color.brand.primary`, text `color.text.inverse`, radius `radius.md`, label `type.label.md` (SM uses `type.label.sm`, LG uses `type.label.lg`)

Rules
- One `Primary` button per view or section.
- `Danger` is only for destructive, hard-to-undo actions.
- Use `Ghost` in dense UI: tables, toolbars, card footers.
- Disabled buttons still need a reason nearby. Don't disable without explaining why.

### Form controls

#### Input
- **State**: `Default` | `Filled` | `Focused` | `Error` | `Disabled`
- **Props**: `Label`, `Value`
- **Tokens**: border `color.border.default`, focus border `color.brand.primary`, error border and message `color.status.error`, label `type.label.md`, value `type.body.sm`, radius `radius.md`
- Always show a visible label. Placeholder text is not a label.
- Error messages say what to do, not just what went wrong.

#### Textarea
- **State**: `Default` | `Filled` | `Error`
- Same tokens and rules as Input. Use when the answer is longer than one line.

#### Select
- **State**: `Default` | `Open` | `Error`
- Use for 5+ options. For 2–4 options, prefer Radio.
- Open menu uses `color.surface.elevated` and `shadow.md`.

#### Checkbox
- **Checked**: `Off` | `On` · **State**: `Default` | `Disabled`
- For independent yes/no choices, or selecting several items from a list.

#### Radio
- **Selected**: `Off` | `On` · **State**: `Default` | `Disabled`
- For one choice from a small set. Always in a group; never a single radio.

#### Toggle
- **State**: `Off` | `On` · **Enabled**: `Yes` | `No`
- For settings that apply immediately. If the user has to press Save, use a Checkbox instead.

### Navigation

#### Top Nav
- Logo, primary links, action Button (`Primary`, `SM`) and Avatar (`SM`).
- **Tokens**: fill `color.surface.default`, bottom border `color.border.default`, horizontal padding `space.6`, height 64
- Current page link uses `color.text.primary`; others use `color.text.secondary`.

#### Nav Item
- **State**: `Default` | `Hover` | `Active` · **Props**: `Label`, `Show Icon`
- **Tokens**: padding `space.2` / `space.3`, gap `space.3`, radius `radius.md`; Active fill `color.brand.secondary`, Active text `color.brand.text`; Hover fill `color.bg.secondary`
- One `Active` item per navigation.

#### Tab Item
- **State**: `Active` | `Inactive`
- Use to switch views of the same content. Not for navigating between pages.

#### Breadcrumb Item
- **Type**: `Link` | `Current` | `Separator`
- The last item is always `Current` and is not a link.

### Feedback

#### Alert
- **Type**: `Info` | `Success` | `Warning` | `Error` · **Props**: `Title`, `Description`
- Inline and persistent. Use for messages about the content on screen.
- **Tokens**: radius `radius.md`; each type uses its `status.*` (or `brand.*` for Info) colour and matching `-bg` fill

#### Toast
- **Type**: `Success` | `Error` | `Warning` | `Info` · **Props**: `Title`, `Description`
- Temporary confirmation of something the user just did. Auto-dismisses unless it's an Error.
- **Tokens**: fill `color.surface.elevated`, border `color.border.subtle`, radius `radius.md`, `shadow.lg`
- Never put the only copy of important information in a toast.

#### Tooltip
- Short helper text on hover or focus. One line where possible.
- Never put actions or essential information in a tooltip.

### Data display

#### Badge
- **Type**: `Neutral` | `Primary` | `Success` | `Error` | `Warning` · **Size**: `SM` | `MD`
- Short status labels. One or two words. Radius `radius.full`.

#### Tag
- **Style**: `Filled` | `Outlined` · **Dismissible**: `No` | `Yes`
- User-applied labels or filters. Use Badge for system status, Tag for things the user can add or remove.

#### Avatar
- **Size**: `SM` | `MD` | `LG` | `XL` · **Props**: `Initials`
- Fill `color.brand.secondary`, text `color.brand.text`. Two initials maximum.

#### Table Row
- **Type**: `Header` | `Row` | `Row Striped`
- Header uses `type.label.sm` on `color.bg.secondary`. Cells use `type.body.sm`.
- Use `Row Striped` only for wide tables where rows are hard to follow.

#### List Item
- **Type**: `Default` | `With Description` | `With Icon` · **Props**: `Title`

#### Divider
- **Direction**: `Horizontal` | `Vertical` · Colour `color.border.subtle`
- Prefer spacing over dividers. Use a divider when spacing alone doesn't separate groups.

### Containers

#### Card
- **Style**: `Default` | `Outlined` | `Elevated` · **Props**: `Title`, `Description`
- **Tokens**: fill `color.surface.default`, radius `radius.lg`, title `type.heading.h4`, description `type.body.sm`
- Don't nest cards inside cards.

#### Modal
- Title (`type.heading.h3`), body text, and an action row: `Secondary` cancel on the left, `Primary` (or `Danger`) confirm on the right.
- **Tokens**: fill `color.surface.default`, radius `radius.lg`, `shadow.xl`
- Use for decisions that block the flow. Anything else belongs on the page.

---

## 8. Accessibility

- Text contrast meets WCAG 2.1 AA: 4.5:1 for body text, 3:1 for large text and UI boundaries.
- Every interactive element has a visible focus state using `color.brand.primary`.
- Touch targets are at least 40×40px (Button `MD` and up).
- Icons that carry meaning need a text label or `aria-label`.

---

## 9. Changing the system

1. Change it in Figma.
2. Make the same change here.
3. Update `tokens.json` (Tokens Studio sync, or by hand).
4. Add a line to `CHANGELOG.md`.
5. Commit.

Not an announcement in Slack. Not a Notion page nobody opens. A commit.

The rules in this file are starter rules. Edit them. Delete the ones that don't fit your product. Add the ones that do. Frame is the blueprint. Your product is what gives it its identity.
