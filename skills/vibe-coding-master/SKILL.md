---
name: vibe-coding-master
description: Entry point for building, changing, and shipping apps and landing pages from a plain-language idea. Use for any request to build an app, add to or fix an app, or make a landing page. Routes each stage to the right skill in order. Triggers: "build me an app", "vibe code", "make an app for", "add a feature", "fix this app", "ship this".
---

# Vibe Coding Master

## Purpose
Turn an idea into a working, tested, shipped app or landing page, one stage at a time. This skill decides what runs next. Specialist skills do the work.

## Operating rules
1. Ask once at the start of a new project (Step 0). Don't re-ask decisions already made.
2. Plan before code. The user approves the plan in Stage 1 before any code is written.
3. Each concern has one owner (see Ownership).
4. Build in thin vertical slices. Each slice ends with a passing check.
5. Never report a check as passed if it didn't run. List what ran and what didn't.
6. The user's global rules in AGENTS.md (palette, glass, and similar preferences) override every skill default.

## Step 0: Intake (new projects only, always asked)
Ask in one message with these labeled fields. Skip any the user has already answered.

- **App or page:** what it is, in one sentence.
- **Users:** who uses it and what they care about most.
- **Core action:** the one thing a user must be able to do.
- **Platform:** web, mobile web, iOS, Android, or cross-platform.
- **Data:** what gets stored, and whether it includes personal or payment data.
- **Auth:** none, Supabase Auth (web default), Firebase Auth, or other.
- **Real material:** screenshots, copy, numbers, logos. If none exist, use labeled placeholders. Never invent metrics, testimonials, or logos.
- **Look and feel:** for landing pages, a tone such as editorial, utilitarian, or technical. For apps, use the default unless the user specifies.

If the user says "just build it," proceed with the defaults below and list every assumption at the top of the first reply.

**Defaults:** Web: Next.js App Router, Tailwind, shadcn/ui, Supabase. Mobile: Expo with React Native and NativeWind. iOS-only: SwiftUI.

Revisions skip Step 0 and start at Stage 7.

## Routing

| Request | Path |
| :--- | :--- |
| New app | Stages 1 to 6, then 8 to 12 |
| New landing page or showcase | master-ui (Persuade mode), then Stages 8, 10, 11 |
| New screen in an existing app | screen-builder, then Stages 8, 10 |
| Add a feature | orch-add-feature, then Stages 8, 10 |
| Change existing behavior | orch-change-feature, then Stages 8, 10 |
| Fix a bug | orch-fix-defect, then Stage 8 |
| Clean up code | orch-refine-code, then Stage 8 |
| Mobile web fix | mobile-native |
| Figma file requested | figma-designer (opt-in only) |

## Stage 1: Plan
**Skill:** js-mastery-prompter
- **Input:** Step 0 answers.
- **Overrides:** auth and stack from intake. Don't use Clerk unless the user already has it set up.
- **Output:** AGENTS.md and an ordered prompts folder.
- **Check:** the user approves the plan. Stop here until they do.

## Stage 2: Foundation
Run the planned prompts in order, one at a time. Each ends with a check before the next starts. Typical order: setup, theme and tokens, mock state, navigation, backend.

- Create one design token file here. It holds color, type, spacing, motion, and material values. Screens read from it, and none hardcode values.
- **Check:** the project builds, typechecks, and runs.

orch-build-mvp is not in this chain. Use it only after it passes a test build on a throwaway project.

## Stage 3: App shell
**Skill:** app-shell. Once per project.
- Builds the sidebar or top bar, profile menu, and mobile drawer.
- **Check:** the shell renders at 390px and 1440px, and navigation works.

## Stage 4: Screens
One skill per screen. Never give the same screen to two skills.

| Screen type | Skill |
| :--- | :--- |
| Web app screen | screen-builder |
| iOS screen | swiftui-patterns (unreviewed; verify output) |
| Cross-platform mobile screen | react-native-patterns (unreviewed; verify output) |
| Landing page | master-ui (Persuade mode) |

Build the core action screen first, then its neighbors.
- **Check per screen:** default, empty, loading, and error states all implemented. No placeholder text. Responsive at 390px and 1440px.

## Stage 5: Components and micro-UX
Use only when the element is needed.

- Forms: form-design
- Modals, sheets, popovers: modal-and-overlay-patterns
- Tabs: tab-navigation
- Loading states and skeletons: loading-states-and-perceived-performance
- Mobile web fixes (safe areas, tap delay, 100dvh, input zoom): mobile-native

**Check:** each element works by keyboard and by touch.

## Stage 6: Data, auth, and backend
- **Supabase (default):** supabase for setup, postgres-patterns for schema, indexes, and RLS.
- **Firebase:** firebase-auth-basics and firebase-firestore, only if chosen at intake.
- **Python API:** fastapi-python.
- **Node API:** backend-patterns or nestjs-patterns, only if chosen.
- **Check:** RLS is on for every table, every server route checks the session, and no secret appears in client code.

## Stage 7: Changes after launch
Route each request by type:
- Add: orch-add-feature
- Modify: orch-change-feature
- Bug: orch-fix-defect
- Cleanup: orch-refine-code

Every change goes through Stage 8 before it counts as done.

## Stage 8: Tests
**No installed skill. Run directly.**
- Unit tests for core logic: calculations, validation, permissions.
- One end-to-end test per core flow (sign up, core action, sign out), using Playwright.
- **Check:** all tests pass. If Playwright isn't available, report tests as not run.

## Stage 9: Security
**No installed skill. Checklist.**
- No API keys or service secrets in client code or committed files.
- `.env` files are gitignored.
- RLS is on for every Supabase table. Policies are tested with a non-owner account.
- Server routes validate input and check the session.
- Error messages don't expose stack traces or table names.

## Stage 10: Visual gates
- **Viewports:** 390px, 768px, and 1440px for all apps. Add 1920px for landing pages. No horizontal overflow, no clipped text, and the primary action visible at 390px.
- **Contrast:** WCAG AA for text, including text on translucent surfaces.
- **Reduced motion:** respected. No animation on repeated keyboard actions.
- **Sloplint:** landing pages only. Blocking: failures stop delivery.
- **Tool:** Playwright directly. vibelens-ui-loop is not used until its paths are fixed.
- **No headless browser:** mark Stage 10 as not run. Don't deliver as verified.

## Stage 11: Final UI gate
**Skill:** impeccable. Reviews all UI against the craft floor. Its veto stands.

## Stage 12: Ship
**No installed skill for deployment. Manual.**
- **Web:** deploy to Vercel. Set environment variables in the host, never in the repo.
- **Mobile:** Expo EAS build. App store submission is manual.
- **Before deploy:** Stages 8 to 11 passed, or the user has waived them in writing.
- **Store screenshots:** app-store-screenshots, for marketing images only.
- **Optional writeup:** Brag-Slim, on request only.

## Ownership

| Concern | Owner |
| :--- | :--- |
| Plan and sequence | js-mastery-prompter |
| App token file | Created in Stage 2, read by all screens |
| Landing token file | master-ui, reads project tokens if they exist |
| App shell | app-shell |
| App screens | screen-builder, or the platform pattern skill |
| Landing page | master-ui |
| In-app microcopy | ux-copy if installed; otherwise ui-ux-pro-max copy rules |
| Landing copy | master-ui |
| Changes and fixes | orch-* skills |
| Final UI judgment | impeccable |
| Figma | figma-designer, opt-in only |

If two skills give different defaults for the same screen, the owner in this table wins.

## Excluded
- **v0-ui-designer:** replaced by screen-builder.
- **image-to-code-skill:** unverified.
- **orch-build-mvp:** unverified. Test first.
- **vibelens-ui-loop:** broken paths.
- **framer-motion, animate, animate-expo:** not installed. Use CSS transitions with the token file's motion values.

## Fallbacks
- **Missing skill:** follow the stage's checklist directly and say so in the report.
- **No headless browser:** Stages 8 (E2E) and 10 are marked not run.
- **No Supabase CLI:** say RLS is unverified. Don't claim it was tested.

## Report (end of every build or change)
- Stage reached
- Skills used
- Checks passed
- Checks not run, with reason
- Step 0 assumptions
- Next action for the user
