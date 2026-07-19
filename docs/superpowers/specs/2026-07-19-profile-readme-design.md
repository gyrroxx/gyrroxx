# SHAKH profile README — design specification

## Goal

Create an English GitHub profile README for `gyrroxx` that feels memorable and technically credible. The profile should present Shakh as an AI specialist and developer, primarily for hiring visibility and personal brand, without inventing clients, revenue, employment history, or project metrics.

## Verified facts

- Display name: **Shakh**.
- Positioning: **AI Specialist & Developer**.
- Contact: `https://t.me/dokaqq`.
- GitHub inventory on 2026-07-19: **34 owned repositories — 3 public, 31 private**.
- Experience copy supplied by the owner: **3 years with AI; 6+ months of deep engineering focus**.
- Public flagship: **Versus LLM** — a Python CLI where two LLM agents debate and a judge returns a verdict.
- Private selected systems: **GyroLAB** — a local browser-first coding agent; **Drip Cards** — a Telegram collectible product with bot, Mini App, economy, and real-prize mechanics.

## Art direction: Blacksite Operator

The visual language combines a restrained old-web terminal with a premium AI laboratory. It must feel authored, not like a collection of generic neon badges.

- Base: OLED black `#050505`, graphite `#111318`, warm white `#E7ECE8`.
- Primary signal: phosphor green `#39FF88`.
- Secondary signals used sparingly: cyan `#35D9FF`, amber `#FFB84D`, magenta `#FF4FD8`.
- Typography: monospace-led terminal voice; strong hierarchy and short copy.
- Effects: subtle CRT scanlines, controlled glow, one typing animation, small system-status labels.
- Avoid: Matrix rain, skulls, fake security claims, excessive glitch, rainbow neon, skill progress bars, fake terminal commands, emoji-heavy headings, and long autobiography.

## Hero and mascot

Generate one original wide raster hero with ImageGen. It shows **Gyro**, an abstract compact AI operator/robot mascot inside a dark terminal workstation. The composition leaves clean negative space for the profile identity and uses the approved signal colors without generated text, logos, watermarks, or a human face.

Exact text remains outside the generated bitmap so it is readable and typo-free:

- `SHAKH // AI SPECIALIST & DEVELOPER`
- `building intelligent systems, AI products, and experimental software`

ASCII identity uses output from the BSD-licensed FIGlet tool/font ecosystem rather than hand-drawn or copied character art. Attribution is kept unobtrusive in a source comment or footer.

## README structure

1. **Hero:** generated Gyro banner, exact identity line, and restrained animated typing line.
2. **Status strip:** `3 YEARS WITH AI`, `6+ MONTHS DEEP FOCUS`, `34 REPOSITORIES`. Location is omitted because it was not requested for the public profile.
3. **Operator profile:** two short sentences explaining the focus on AI agents, useful products, and production-grade full-stack systems.
4. **Systems:** three compact cards/sections. Versus LLM is linked publicly; GyroLAB and Drip Cards are labeled `PRIVATE SYSTEM` and have no dead or inaccessible links.
5. **Technical arsenal:** only technologies supported by the selected repositories: Python, TypeScript, Next.js, Node.js, PostgreSQL, Docker, Telegram Mini Apps, OpenRouter/LLM agents, Git, and macOS tooling.
6. **GitHub signal:** live public GitHub statistics with an explicit note that most work lives in private repositories. External dynamic cards are limited to reputable open-source services and must degrade harmlessly if unavailable.
7. **Contact:** one clear Telegram button linking to `t.me/dokaqq`.
8. **Footer:** compact FIGlet/terminal sign-off with Gyro status text.

## Files and scope

Final repository tree:

```text
README.md
assets/
  gyro-blacksite.webp
```

The generated source image remains local and is not shipped. No workflow, dependency, application code, analytics, tracking pixel, database, secret, or deployment configuration is added. The temporary design specification is removed from the final tree after implementation review.

## Reliability and accessibility

- The README remains understandable if animations or remote stat cards fail.
- Every image has useful alt text; decorative images use concise alt text.
- Links are standard HTTPS links and the Telegram control has a text label.
- The fixed dark hero remains legible in both GitHub light and dark themes.
- Copy avoids unsupported claims and clearly identifies private work.

## Verification

- Review the final diff and staged paths explicitly.
- Run `git diff --check`.
- Render Markdown through GitHub's Markdown API and inspect the produced HTML.
- Validate all external URLs and local asset references.
- Inspect the generated banner at original resolution and at README-width scale.
- After push, open the live profile and verify desktop/mobile layout, image loading, links, animation fallback, and light/dark GitHub themes where available.

## Ready when

The live `github.com/gyrroxx` profile shows a polished English Blacksite Operator README, all factual claims match the verified account/repositories, Versus LLM is clickable, private projects are honest, Telegram works, and the visual remains readable without depending on animation.
