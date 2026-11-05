# GENCHANE — Codex Project Guidelines

## Language conventions
- Write all Codex instructions and technical documentation in English.
- Keep all user-facing website content in Turkish.
- Write code, variables, functions, components, and file names in English. Preserve existing Turkish source and asset file names referenced below unless a rename is explicitly requested.
- Write Git commit messages in English.
- Provide progress updates, explanations, and final summaries to the user in concise Turkish.
- Preserve the original meaning of all Turkish business content when adapting it for the website.
- Do not translate brand names or modify existing logos.

## Project and scope
- GENCHANE is a registered trademark created by Başkayalar Kantin İşletmeciliği. The business began operating in 2022.
- This repository is for a **static promotional website** focused on GENCHANE that also presents the corporate identity of Başkayalar Kantin İşletmeciliği.
- Primary goal: a mobile-first, fast, distinctive, accessible, and professional corporate presence.
- **Out of scope:** e-commerce, payments, online ordering, QR menus, membership, databases, backend services, and an admin panel. Do not add these unless requested.

## Authoritative sources and brand assets
- The business content is in `content/biz-kimiz.md` and `content/gelecek-hedeflerimiz.md`. These are **primary sources** supplied by the business.
- You may derive concise website copy from these texts; do not change the founding year, registered trademark status, or other facts. Do not invent information; preserve the original versions of the texts.
- `genchane.jpeg` and `başkayalar.jpeg` in the repository root are the brand logos. Do not alter the originals, redraw them, arbitrarily change their colors, or change their lettering. If web optimization is needed, create separate derivative files.
- Colors may be sampled from the logos, but do not present color codes as "official colors" without measuring them.
- Do not fabricate unverified information such as Instagram handles, contact details, addresses, locations, branch counts, opening hours, or photographs. If necessary, use clearly marked development placeholders and remove them before publication.

## Technology and deployment
- Planned stack: **Astro + Tailwind CSS**, targeting static generation and **GitHub Pages**.
- Do not introduce server-side code, databases, APIs, or SSR by default.
- Keep dependencies minimal; load JavaScript only for actual interactions. Optimize images and use accessible, semantic HTML.
- If the custom domain has not been finalized, do not hardcode it in configuration or canonical URLs without approval. Verify the base path and custom domain settings before publishing to GitHub Pages.

## Design principles
- Clearly and consistently present GENCHANE as the main brand and Başkayalar Kantin İşletmeciliği as the corporate identity.
- Aim for a youthful, warm, and trustworthy design that avoids a generic template aesthetic.
- Prioritize visual hierarchy, typography, spacing, contrast, and photography.
- Evaluate both mobile layouts, especially at 360–390 px, and wide-screen layouts.
- Do not add flashy but unnecessary animations, autoplay videos, or heavy third-party widgets.

## Workflow and token discipline
- Inspect existing files first; avoid unnecessary broad scans.
- Divide the work into stages: (1) design analysis, (2) initial static implementation, (3) browser checks, (4) performance/SEO, and (5) deployment.
- Do not begin a large implementation or redesign until the user approves the design direction.
- Do not launch subagents for simple tasks; use them for separate, independent tasks that can genuinely run in parallel. Keep the agent count low and avoid conflicting file ownership.
- Use Canva MCP only when needed for design exploration, Playwright MCP for browser and responsive checks, and Lighthouse CLI for the final performance, accessibility, and SEO audit.
- Avoid unnecessarily long logs or snapshot dumps in tool output; summarize relevant findings briefly.
- Run the relevant build/test commands after changes, and never claim to have run tests that were not actually executed.
- Do not delete files, modify logo sources, commit, push, or deploy unless explicitly requested.
- At the end of the work, briefly summarize changed files, verification results, and any open issues in Turkish.

## First-session behavior
- If there is no code yet, inspect the brand assets and both business texts first.
- If the initial task is design analysis only, create `DESIGN_BRIEF.md` and propose two concrete visual directions; wait for the user's evaluation **before starting implementation**.
