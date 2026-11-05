---
name: screen-builder
description: Builds production-grade, state-complete web application screens — dashboards, settings, login/auth, forms, and onboarding. Ingests reference images or specs, enforces full state handling (default, empty, loading, error), binds to design tokens, and guarantees multi-viewport responsiveness. Replaces v0-ui-designer.
---

# Screen Builder

Specialized skill for crafting production-ready web application screens (dashboards, settings, authentication, complex forms, and multi-step onboarding). It replaces generic UI generation with token-grounded, state-complete, accessible layouts.

---

## 🎯 1. Core Principles

1. **Token Grounding**: Every component binds strictly to the project's DTCG token file (`tokens.json`, `tokens.css`, or Tailwind semantic tokens). Never use raw hex values or arbitrary utility arbitrary values like `bg-[#123456]`.
2. **Four-State Completeness**: Every screen must explicitly define and render:
   - **Default State**: Populated with realistic, domain-grounded data.
   - **Empty State**: Clear guidance, helpful microcopy, and an immediate primary CTA.
   - **Loading State**: Content-shaped skeleton loaders (`Skeleton`), never a blank screen with a central spinner.
   - **Error State**: Non-blocking alerts with clear recovery paths or retry actions.
3. **Reference Ingestion**: Can directly ingest UI screenshots or mockup images. Extracts layout structure, visual hierarchy, and component relationships without blind pixel-copying.
4. **Keyboard & Touch Parity**: Every action is focusable, has a visible 3:1 focus ring, and touch targets are $\ge 44\times 44$px on mobile viewports.
5. **No AI Slop / Placeholders**: Zero "Lorem Ipsum", "Acme Corp", or fake metrics. All labels, numbers, and dates must be realistic and context-appropriate.

---

## 🛠️ 2. Screen Archetypes & Patterns

### A. Dashboards
- **Structure**: Sticky shell / sidebar navigation, ambient status bar, top stat counter row (value + label + trend delta badge), primary visualization/chart, and an interactive data table or recent activity list.
- **Data Density**: High density with clear visual hierarchy. Use tabular figures (`font-mono tabular-nums`) for numeric readouts.

### B. Settings & Preferences
- **Structure**: Grouped sections by domain concept (Profile, Security, Workspace, Billing, Notifications).
- **Behavior**: Clear destructive action isolation (e.g. Danger Zone in a red-tinted sub-card with confirmation dialogs).
- **Save Paradigm**: Auto-save with subtle inline status indicator, or an explicit sticky bottom action bar when dirty.

### C. Authentication & Login
- **Structure**: Centered single-card or split 50/50 hero layout. Focus cleanly on credentials input, OAuth social buttons, and secondary recovery links (Forgot password, Sign up).
- **Security**: Explicit autocomplete tags (`autocomplete="username"`, `autocomplete="current-password"`), inline validation errors, and disabled states during submit.

### D. Complex Data Forms
- **Structure**: Progressive disclosure or multi-step wizard when exceeding 6 fields. Group related fields into fieldsets.
- **Validation**: Inline validation on blur, accessible `aria-invalid` and `aria-describedby` error associations, and disabled submit states while pending.

### E. Onboarding Flows
- **Structure**: Guided progression with step tracker (progress bar or dots), clear milestone completion, and skip affordances where permissible.

---

## 📐 3. Workflow & Order of Operations

1. **Inspect Tokens & Shell**: Read the project's token file and verify the persistent shell layout from `app-shell`.
2. **Build Core Action Screen First**: Identify the primary screen driving the user's core action, then implement its neighbors.
3. **Structure & Skeletons**: Lay out flex/grid structures mobile-first (390px), expanding seamlessly to tablet (768px) and desktop (1440px).
4. **Implement State Matrix**: Wire up toggleable or condition-driven previews for Default, Empty, Loading, and Error states.
5. **Quality Verification**:
   - Verify layout at 390px, 768px, and 1440px (zero horizontal scroll).
   - Ensure WCAG AA contrast ($\ge 4.5:1$ body, $\ge 3:1$ UI parts).
   - Verify keyboard navigability and focus visibility.

---

## ✅ 4. Done-Check Checklist

- [ ] All 4 states (Default, Empty, Loading, Error) implemented and functional.
- [ ] Responsive across 390px, 768px, and 1440px without overflow or clipping.
- [ ] Binds exclusively to design tokens / semantic CSS classes.
- [ ] Realistic, domain-specific mock data; zero placeholder filler.
- [ ] Accessible form labels, focus rings, and ARIA attributes in place.
