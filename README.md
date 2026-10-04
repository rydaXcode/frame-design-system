# Frame UI

**A design system blueprint for designers starting from scratch — with the DESIGN.md that helps an AI agent understand it.**

By [Design x Machine](https://designxmachine.beehiiv.com) · Free · v1.0

---

You open a new Figma file. You create the first frame. Then you're staring at an empty page wondering where to begin.

Frame is that beginning. Tokens, type, spacing, radius, elevation, 21 components and 36 icons — each with a name, a token, a rule and a place in the system. Plus the written half: a `DESIGN.md` your coding agent can actually read.

Not a finished system. A starting point.

## What's in this repo

| File | What it is |
|---|---|
| [`DESIGN.md`](./DESIGN.md) | The system in writing: tokens, components, rules, and instructions for AI coding agents |
| [`tokens.json`](./tokens.json) | Every token, in [Tokens Studio](https://tokens.studio) format. Light and Dark themes included |
| [`CHANGELOG.md`](./CHANGELOG.md) | Every change to the system, with a template for your own |

The Figma file is free on Gumroad: **[Get Frame UI →](https://designxmachine.gumroad.com/l/frame-ui)**

## How to use it

1. **Duplicate the Figma file** into your workspace.
2. **Change it.** Colours, type scale, components. Remove what you don't need. Add what you do.
3. **Fork this repo** and make the same changes in `DESIGN.md` and `tokens.json`.
4. **Put `DESIGN.md` in your product's repo** and point your coding agent at it. For example, reference it from your `CLAUDE.md`, `AGENTS.md` or `.cursorrules`:
   ```
   Before writing UI code, read DESIGN.md and follow it.
   ```
5. **Log every change** in `CHANGELOG.md`.

Now you're not asking the agent to figure out your design system. You're giving it one.

## Syncing tokens with Figma

`tokens.json` uses Tokens Studio's multi-set format:

- `primitives` — raw colour values
- `semantic/light`, `semantic/dark` — semantic colours (two themes)
- `spacing`, `radius`, `typography`, `elevation`

In Figma, open Tokens Studio, add this repo as a GitHub sync provider, and pull. Token names match the Figma variables (`brand/primary` in Figma = `brand.primary` here).

## Who it's for

- Designers starting a new design system and not wanting to begin from a blank file
- Product designers asked to "set up a design system"
- Developers working with a designer who uses Frame
- Anyone curious how a design layer and a DESIGN.md layer work together

## The DESIGN.md Series

Frame came out of a five-part series on making design systems machine-readable. Start at Part 1 on [Design x Machine](https://designxmachine.beehiiv.com).

## Built for React + Tailwind + shadcn/ui

Component names follow [shadcn/ui](https://ui.shadcn.com) and icons are [Lucide](https://lucide.dev), so what you design in Figma matches what you (or your AI agent) build in code.

## License

Free to use in personal and commercial projects. Please don't resell Frame itself as a template or UI kit.

Icons: [Lucide](https://lucide.dev), ISC licence.
