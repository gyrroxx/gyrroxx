# Gyro Puppet Master Hero Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the profile hero with a centered, colored manga-style Gyro Zeppeli controlling the AI systems beneath his hands.

**Architecture:** Generate one raster candidate from the existing hero and canonical character reference, validate it visually, then replace the existing WebP without changing the README layout. Verify the local Markdown render and the live GitHub profile at desktop and `390px` mobile width.

**Tech Stack:** Built-in ImageGen, Pillow, GitHub Markdown API, Playwright, Git

## Global Constraints

- Final asset must be WebP at exactly `1600 x 533`.
- Gyro must be centered, youthful, manga-influenced, and framed from the waist up.
- Both arms extend diagonally downward toward controlled terminal systems.
- Use near-black, muted teal, CRT green, and small cyan highlights.
- No text, logos, watermark, excessive neon, religious symbols, or visual clutter.
- Do not change README content outside the hero alt text if needed.

---

### Task 1: Generate and Select the Hero

**Files:**
- Reference: `assets/gyro-blacksite.webp`
- Create: `/tmp/gyrroxx-profile-imagegen/gyro-puppet-master-candidate.png`

**Interfaces:**
- Consumes: current hero composition and a canonical Gyro Zeppeli character reference
- Produces: one visually approved 3:1 raster candidate with no embedded text

- [ ] **Step 1: Inspect both input images**

Open the existing hero and canonical reference at original detail. Confirm the current blacksite palette and Gyro's youthful manga traits before generation.

- [ ] **Step 2: Generate the candidate with built-in ImageGen**

Use the existing hero as the edit target and the canonical art as the identity reference. Request the centered puppet-master composition, colored manga ink rendering, and restrained CRT interface elements described in the spec.

- [ ] **Step 3: Inspect the candidate at original resolution**

Accept only if Gyro is centered, both hands are anatomically plausible, the Steel Ball count is exactly one, the face is youthful and manga-like, and there is no text, watermark, or visible generation artifact. Otherwise perform one targeted regeneration.

### Task 2: Integrate and Validate the Asset

**Files:**
- Modify: `assets/gyro-blacksite.webp`
- Modify only if needed: `README.md:2`

**Interfaces:**
- Consumes: approved PNG candidate from Task 1
- Produces: compressed `1600 x 533` WebP referenced by the existing README hero markup

- [ ] **Step 1: Convert the approved candidate**

Run Pillow through the configured workspace Python to fit the source to `1600 x 533` using a centered crop and save WebP at quality `88`, method `6`.

- [ ] **Step 2: Verify the binary asset**

Run:

```bash
file assets/gyro-blacksite.webp
```

Expected: WebP image data with dimensions `1600 x 533`.

- [ ] **Step 3: Render the README through GitHub Markdown**

Post `README.md` to GitHub's Markdown API and verify the returned HTML contains `assets/gyro-blacksite.webp`, the Versus LLM repository link, and the Telegram link.

- [ ] **Step 4: Review the focused diff**

Run:

```bash
git diff --check
git diff --stat
git status --short
```

Expected: only the hero asset and, if required, its alt-text line are modified.

### Task 3: Publish and Verify the Live Profile

**Files:**
- Remove after use: `docs/superpowers/specs/2026-07-19-gyro-puppet-master-hero-design.md`
- Remove after use: `docs/superpowers/plans/2026-07-19-gyro-puppet-master-hero.md`

**Interfaces:**
- Consumes: validated README hero asset
- Produces: clean `main` branch published to `origin/main`

- [ ] **Step 1: Remove temporary process documents**

Remove the design and plan files so the profile repository remains limited to user-facing content.

- [ ] **Step 2: Commit the focused implementation**

Stage the exact changed paths and commit with:

```bash
git add README.md assets/gyro-blacksite.webp docs/superpowers/specs/2026-07-19-gyro-puppet-master-hero-design.md docs/superpowers/plans/2026-07-19-gyro-puppet-master-hero.md
git commit -m "Center manga Gyro in profile hero"
```

- [ ] **Step 3: Push the approved change**

Run:

```bash
git push origin main
```

Expected: `main` advances successfully with no force push.

- [ ] **Step 4: Check the live desktop and mobile profile**

Open `https://github.com/gyrroxx`, capture desktop and `390 x 844` views, and evaluate:

```js
({
  scrollWidth: document.documentElement.scrollWidth,
  clientWidth: document.documentElement.clientWidth
})
```

Expected: the new centered hero is visible and `scrollWidth === clientWidth` at mobile width.

- [ ] **Step 5: Confirm repository state**

Run:

```bash
git status -sb
git rev-parse HEAD
git rev-parse origin/main
```

Expected: clean worktree and identical local/remote revisions.
