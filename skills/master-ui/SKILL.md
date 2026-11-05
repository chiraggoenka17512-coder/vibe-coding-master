---
name: master-ui
description: "Master UI & Storytelling Skill. Orchestrates UI/UX Pro Max, Hallmark, Landing Page Design, Dembrandt, Anatomy, Emil Kowalski (EK) Motion, Impeccable, Liquid Glass, Genjutsu, Awwwards MCP, and Responsively through a strict 4-mode entry router, single-source DTCG tokens, blocking Sloplint, and verification done-checks."
allowed-tools: Bash, Read, Edit, Write, Grep, Glob, WebSearch, Artifact, awwwards, dembrandt
---

# Master UI — Architecture & Operating System

`master-ui` transforms product ideas and prompts into production-grade, narrative-driven interfaces with verified craft, single-token governance, and zero AI slop. It enforces a strict separation of concerns across specialized sub-skills with clear ownership boundaries.

---

## 🧭 1. Entry Router

Before initiating design or code generation, the router evaluates two decisions: **Surface Mode** and **Lifecycle Phase**.

### Surface Mode Decision Matrix

| Request Signal | Mode | Focus & Strategy | Narrative Archetype (When Applicable) |
| :--- | :--- | :--- | :--- |
| Landing page, hero, showcase, portfolio | **Persuade** | High-conversion storytelling, emotional resonance, Anatomy physical machine centerpiece. | **Developer / Data Infra**: 24-Hour Builder's Descent Arc.<br>**Consumer / Platform**: 4-Zone Architectural Cutaway. |
| Dashboard, editor, workbench, forms, admin | **Operate** | Task efficiency, strict keyboard ergonomics, high data density, zero decorative motion. | *N/A (Functional Flow)* |
| Telemetry, scanner results, X-ray, live state, gauges | **Diagnostic** | State transparency, CAD/HUD readouts, dials bound to truth, optical loupe diffs. | **Developer / Data Infra**: 24-Hour Builder's Descent Arc.<br>**Consumer / Platform**: 4-Zone Architectural Cutaway. |
| Docs, guides, changelogs, articles | **Read** | Editorial clarity, modular typography, distraction-free reading surfaces. | *N/A (Modular Information)* |

> **Mixed Requests**: If a request spans multiple surfaces (e.g., a landing page + an admin dashboard), assign the mode **per-view or per-section**. Run the respective skill subsets and quality gates for each view independently.

### Lifecycle Phase
- **New Build**: Executes the full sequence starting with Step 0 Intake.
- **Revision**: Skips Step 0 (Intake), Step 2 (Benchmark), and Step 5 (Thesis). Reuses and preserves the existing DTCG token file. **Must execute Steps 9–11 (Build, Gate, Verify).**

---

## 🧰 2. Skill Subset Per Mode

Only skills permitted for the active mode may run. All others are strictly excluded:

| Mode | Active Skills (Always-On + Added) | Strictly Excluded |
| :--- | :--- | :--- |
| **Persuade** | **Always-On**: `ui-ux-pro-max`, `dembrandt`, `responsively`, `impeccable`<br>**Added**: `awwwards` MCP, `genjutsu`, `anatomy`, `emil-design-eng`, `framer-motion`, `liquid-glass-design` (header), `hallmark`, `landing-page-design` | *None* |
| **Operate** | **Always-On**: `ui-ux-pro-max`, `dembrandt`, `responsively`, `impeccable`<br>**Added**: `emil-design-eng` (snappy values), `framer-motion` (popovers only), `liquid-glass-design` (floating chrome only), `ux-copy` | `awwwards`, `anatomy`, `genjutsu`, `hallmark` (themes/floor) |
| **Diagnostic** | **Always-On**: `ui-ux-pro-max`, `dembrandt`, `responsively`, `impeccable`<br>**Added**: `anatomy` (dials bound to state), `emil-design-eng` (tactile springs), `genjutsu` (thesis), `liquid-glass-design` (HUD chips), `ux-copy` | `awwwards` |
| **Read** | **Always-On**: `ui-ux-pro-max`, `dembrandt`, `responsively`, `impeccable`<br>**Added**: `emil-design-eng` (calm 120ms values) | `anatomy`, `genjutsu`, `awwwards`, `liquid-glass-design` |

*Note*: **`brag-slim`** runs only when the user requests a writeup. Full **`brag`** runs only if a comprehensive postmortem is requested.

---

## 📋 3. Order of Operations (New Build)

```
[0. Intake (Ask)] ──► [1. Route & Probe] ──► [2. Benchmark (Persuade)] ──► [3. Foundation (Pro Max)]
                                                                                     │
[7. Motion (EK)] ◄── [6. Centerpiece (Anatomy)] ◄── [5. Thesis (Genjutsu)] ◄── [4. Token File (master-ui)]
       │
       ▼
[8. Chrome (Glass)] ─► [9. Build] ─► [10. Sloplint (Blocking)] ─► [11. Gate (Impeccable)] ─► [12. Verify]
```

### Step 0: Intake Questionnaire
Always runs on new builds. Send a **single prompt with labeled text fields** (free text for materials, options for tone and use):
```text
[Material]: Real URLs, screenshots, metrics, quotes, logos (or state "none")
[Audience]: Who reaches this surface and what do they care about?
[Use]: The primary action or conversion outcome this page drives
[Tone]: 
  - Persuade options: editorial | brutalist | soft | utilitarian | luxury | playful | technical | austere
  - Operate / Diagnostic options: utilitarian | technical | austere
```
*Revisions skip this step and reuse existing context.*

### Step 1: Route and Probe
Determine active mode(s), archetype, and lifecycle phase. Probe MCP servers (`awwwards`, `dembrandt`) and local skills. Record any missing dependencies for the fallback report.

### Step 2: Benchmark (Persuade Only)
`awwwards` queries live award-winning references (`search_sites`, `get_motion_dna`) for layout pacing and motion density. **Raw values and code are never copied.**

### Step 3: Foundation
`ui-ux-pro-max` establishes the color palette, typography pairing, spacing cadence, and contrast targets matching the domain.

### Step 4: Token File
`master-ui` writes a single, canonical W3C Design Tokens Community Group (`tokens.json` or `tokens.css`) file:
- **Single Source of Truth**: Contains `color`, `typography`, `spacing`, `motion`, and `material`.
- **Material Tokens**: All Liquid Glass values (blur radius, border opacity, specular highlights) must be declared as tokens. No literal `rgba()` in component code.
- **Motion Tokens**: All durations and curves from `emil-design-eng` must be declared as tokens.
- **Dembrandt**: Validates the DTCG file. If an existing brand or URL was provided in Step 0, `dembrandt` extracts tokens first, and `ui-ux-pro-max` fills gaps.

### Step 5: Interaction Thesis (Persuade and Diagnostic)
`genjutsu` drafts the **Interaction Thesis** (the core physical metaphor and tactile premise). It must pass its anti-slop check. If `genjutsu` is unavailable, `master-ui` writes the thesis directly against the banned list.

### Step 6: Centerpiece (Persuade and Diagnostic Only)
`anatomy` builds the isometric machine or state visualization. Every lever, needle, dial, and gauge must be strictly wired to real state.

### Step 7: Motion Specification
`emil-design-eng` (EK) defines all motion parameters. Durations, easing curves, and trigger origins are read directly from the DTCG motion tokens. No hardcoded spring numbers or fixed staggers.

### Step 8: Surface Chrome & Materials
`liquid-glass-design` styles the persistent island header, floating docks, and status pills using the DTCG material tokens.
- **Performance Rule**: Maximum **2 `backdrop-filter` layers** visible on screen at once.
- **Accessibility Fallback**: `@media (prefers-reduced-transparency: reduce)` replaces glass blur with solid opaque surfaces.

### Step 9: Build
Implement components and views. Revisions resume directly here using the existing token file.
- **Copy Governance**:
  - `Persuade`: Follows `landing-page-design` / `hallmark` rules (no periods in hero headline, break lines at semantic phrases, no hyphens).
  - `Operate` & `Diagnostic`: Governed by `ux-copy` rules (concise labels, unambiguous action verbs, clear error recovery).

### Step 10: Sloplint (Blocking Gate)
Run Hallmark's `sloplint.mjs` against the rendered output in headless Chrome before Impeccable review:
- **Persuade & Read**: Evaluates all rules, including card-inside-card bans, all-caps eyebrow label bans, and typography cleanliness.
- **Operate & Diagnostic**: Card containers and uppercase telemetry labels are permitted; gradient bans and fake placeholder bans remain strictly enforced.
- **Result**: **Blocking.** Any `FAIL` terminates the pipeline until resolved.

### Step 11: Craft Gate
`impeccable` evaluates the build against the mode's craft floor with full veto authority. For `Diagnostic`, it applies an *Operate + Experience* hybrid standard (high data density + CAD-level tactile precision).

### Step 12: Verify
1. `dembrandt` audits contrast (WCAG AA: $\ge 4.5:1$ body, $\ge 3:1$ display) and token drift.
2. `responsively` tests 4 viewports: `390px`, `768px`, `1440px`, and `1920px`.
3. Verify that `prefers-reduced-motion` is fully honored, and **zero animation occurs on repeated keyboard actions**.
4. Hero above-the-fold check (headline + CTA visible at 1280×800) is evaluated for `Persuade`.

*(Optional Step 13: `brag-slim` writeup generated only if requested).*

---

## ⚖️ 4. Ownership Rules & Conflict Resolutions

### Responsibility Matrix

| Concern | Primary Owner | Role of Other Skills |
| :--- | :--- | :--- |
| **Step 0 Intake** | `master-ui` | Collects labeled fields (*Material, Audience, Use, Tone*). |
| **Tone & Themes** | `hallmark` | Provides curated themes for `Persuade`. `ui-ux-pro-max` provides styles for other modes. |
| **Palette, Type, Spacing** | `ui-ux-pro-max` | Defines the foundation; `dembrandt` validates; `impeccable` holds veto. |
| **Token File** | `master-ui` (writes single file) | `dembrandt` validates/extracts; all skills read from it; none hardcode values. |
| **Motion Values & Curves** | `emil-design-eng` | `framer-motion` executes; `genjutsu` decides if an interaction warrants motion. |
| **Materials & Chrome** | `liquid-glass-design` | Converted to DTCG material tokens; maximum 2 blur layers on screen. |
| **Centerpiece Geometry** | `anatomy` | `genjutsu` sets the physical interaction thesis. |
| **Copy & Content** | `landing-page-design` *(Persuade)*<br>`ux-copy` *(Operate/Diagnostic)* | Enforces mode-appropriate copy cadence and tone. |
| **Sloplint & The Floor** | `hallmark` | Sloplint is blocking before Impeccable; Floor rules scoped by mode. |
| **Final Craft Floor Gate** | `impeccable` | Possesses unconditional veto authority over all visual output. |
| **1920px Viewport Check** | `master-ui` | Enforces 1920px container constraints (gutters grow, measure does not). |
| **Benchmarks** | `awwwards` MCP | Informs visual rhythm in `Persuade` only. |
| **Figma Export (Opt-In)** | `figma-designer` | Triggered only via explicit `/master-ui figma` invocation. |

---

## 🛡️ 5. Fallback Matrix

Every output must conclude with a tool disclosure table stating which skills ran and which fell back:

| Missing Dependency | Fallback Procedure |
| :--- | :--- |
| **Sloplint** | Mark build as `"Sloplint: unverified"`. Do not claim automated sloplint verification. |
| **Hallmark Intake** | `master-ui` executes the labeled intake questions directly. |
| **Hallmark Themes** | `ui-ux-pro-max` internal catalog supplies the aesthetic theme. |
| **Dembrandt** | `master-ui` hand-validates DTCG tokens and runs local contrast calculations. |
| **Awwwards MCP** | Skip benchmark; proceed directly to `ui-ux-pro-max` style generation. |
| **Responsively** | Run headless browser viewports or browser DevTools device emulation at 390, 768, 1440, and 1920px. |
| **Responsively @ 1920px**| `master-ui` launches headless browser at 1920px to verify gutter expansion. |
| **Anatomy WebGL** | Output pure isometric SVG without shader layers. |
| **Framer Motion** | Execute CSS transitions using `emil-design-eng` duration and curve tokens. |
| **Genjutsu** | `master-ui` writes the thesis directly, auditing against the banned list. |
| **Impeccable** | `master-ui` executes Impeccable's craft floor checklist manually and reports gaps. |
| **Brag-Slim** | `master-ui` outputs a concise architectural summary directly in the final message. |

---

## ✅ 6. Done-Check Checklist

Verify every item before completing any run:

- [ ] **Mode & Archetype Stated**: Surface mode (`Persuade`, `Operate`, `Diagnostic`, `Read`) and archetype are stated; only permitted skills ran.
- [ ] **Single DTCG Token File**: Exactly one token file exists containing `color`, `typography`, `spacing`, `motion`, and `material`; components reference tokens exclusively.
- [ ] **Interaction Thesis Written**: Passed anti-slop check for `Persuade` and `Diagnostic`.
- [ ] **Sloplint Passed**: Sloplint ran and exited with zero failures (mode-scoped rules applied).
- [ ] **Multi-Viewport Parity**: Clean layouts with zero overflow at 390px, 768px, 1440px, and 1920px (gutters expand at 1920px).
- [ ] **Hero 1280×800 Check**: Headline, sentence, and primary CTA visible without scrolling at 1280×800 (`Persuade` only).
- [ ] **WCAG AA Contrast**: All text passes $\ge 4.5:1$ ($\ge 3:1$ display), including text over liquid glass.
- [ ] **Motion & Performance Ergonomics**: `prefers-reduced-motion` and `prefers-reduced-transparency` supported; max 2 blur layers; **zero animation on repeated keyboard actions**.
- [ ] **Data Grounding**: Every gauge, dial, and telemetry chip reflects real application state.
- [ ] **Impeccable Gate Passed**: Passed mode's craft floor review without unresolved vetoes.
- [ ] **Execution Report**: Final report includes a disclosure table listing all active skills and fallbacks engaged.
