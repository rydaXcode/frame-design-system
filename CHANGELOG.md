# Changelog

All notable changes to Frame are recorded here.

Every change to the system — a token, a component, a rule — gets a line. If it changed in Figma, it changes here. AI agents read this file to understand what's new and what's gone.

Format: [Keep a Changelog](https://keepachangelog.com) · Versioning: [Semantic Versioning](https://semver.org)
- **Major**: something was removed or renamed. Existing code may break.
- **Minor**: something was added. Nothing breaks.
- **Patch**: a value or rule was fixed. Nothing breaks.

---

## [Unreleased]

<!-- Add changes here as you make them. Move them under a version when you release. -->

---

## [1.0.0] — 2026-10

First release of Frame.

### Added
- **Tokens**
  - Primitives: `neutral` (50–950), `lime`, `blue`, `green`, `red`, `amber` (50–900), `white`, `black`
  - Semantic colour tokens with Light and Dark modes: `bg`, `surface`, `text`, `border`, `brand` (near-black + lime), `status` (success, error, warning, info)
  - Spacing scale on a 4px base: `space.0`–`space.24`
  - Radius scale: `radius.none`–`radius.full`
  - Type scale in Inter: Display, Heading, Body, Label, Caption, Overline
  - Elevation: `shadow.xs`–`shadow.2xl`
- **Components (21)**
  - Actions: Button
  - Form controls: Input, Textarea, Select, Checkbox, Radio, Switch
  - Navigation: Top Nav, Nav Item, Tab, Breadcrumb Item
  - Feedback: Alert, Toast, Tooltip
  - Data display: Badge, Tag, Avatar, Table Row, List Item, Separator
  - Containers: Card, Dialog
- **Icons (36)** from Lucide (ISC), as swappable Figma components
- Component names aligned with shadcn/ui (Switch, Tabs, Separator, Dialog)
- **Docs**
  - `DESIGN.md` with token tables, component rules and instructions for AI coding agents
  - `tokens.json` in Tokens Studio format, matching the Figma variables

---

<!--
Template for future entries:

## [1.1.0] — YYYY-MM-DD

### Added
- New component or token, and what it's for.

### Changed
- What changed, from → to, and why.

### Deprecated
- What will be removed, and what to use instead.

### Removed
- What was removed, and what to use instead.

### Fixed
- What was wrong, and what it is now.
-->
