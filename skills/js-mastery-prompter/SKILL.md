---
name: js-mastery-prompter
description: Turns any app idea into a complete set of phased prompts using the JS Mastery agentic development framework. Use when the user wants to break down an app idea into incremental, agent-ready prompts.
---

# JS Mastery Prompter Skill

When the user asks you to convert an app idea into a set of prompts using the JS Mastery framework, you must act as an expert prompt architect and generate a highly structured, incremental sequence of prompt files.

## 1. The Core Philosophy
The JS Mastery framework relies on **Incremental Agentic Development**. You must break the user's app idea down into ~15-18 atomic, sequentially dependent prompts, strictly following this phased architecture:

*   **Phase 1: Infrastructure & Rules:** Initial setup, scaffolding, and styling engines (e.g., NativeWind).
*   **Phase 2: Visual Foundation & Static UI:** Global CSS, design tokens, and static screens (Onboarding, Auth UI). No logic yet.
*   **Phase 3: State & Data Modeling:** Hardcoded TypeScript mock data and global state setup (e.g., Zustand).
*   **Phase 4: Complex UI & Navigation:** Navigators (Tabs/Drawers), routing, and heavy UI screens wired to the mock data.
*   **Phase 5: Backend & Service Integration:** Replacing mock data with real APIs (e.g., Clerk Auth, Databases, AI integrations, WebRTC).
*   **Phase 6: Polish & Telemetry:** Analytics (PostHog), performance fixes, and UX refinement.

## 2. Generate AGENTS.md First
Always begin by generating an `AGENTS.md` file tailored to the user's idea.
*   **Tech Stack:** Default to the JS Mastery stack (Expo, React Native, TypeScript, NativeWind, Zustand, Clerk, AI services) unless the user specifically asks for web (Next.js/Tailwind) or a different stack.
*   **Sections:** Must include `Project Overview`, `Tech Stack`, `Development Philosophy`, `Decision Making`, and `Architecture Guidelines`.

## 3. Anatomy of Every Generated Prompt
When generating the numbered prompts (e.g., `01-setup.md`, `02-theme.md`), you MUST enforce these rules for each file:
1.  **The Anchor Rule:** The very first line of EVERY prompt MUST be exactly: `Read AGENTS.md first and follow it strictly.`
2.  **Negative Constraints:** Explicitly tell the AI what NOT to do in that step (e.g., "Do not implement the home screen yet", "Do not write backend logic").
3.  **Documentation Injection:** Include placeholders where the user should paste exact docs for external tools (e.g., `(Here paste the latest Clerk Expo documentation)`).
4.  **Visual Grounding:** End UI-related prompts with a mockup reference (e.g., `@prompt_material/0X-screen-name.png`).

## 4. Execution Workflow
When activated, follow these steps:
1.  **Understand the Idea:** If the user's idea is vague, ask clarifying questions about core features.
2.  **Generate AGENTS.md:** Present the system instruction file.
3.  **Generate the Prompt Sequence:** Output the exact contents for 15-18 prompt files (e.g., `01-setup.md` through `18-analytics.md`). You can either print them in markdown blocks or offer to write them directly into a `prompts/` folder in the user's workspace using your file system tools.
