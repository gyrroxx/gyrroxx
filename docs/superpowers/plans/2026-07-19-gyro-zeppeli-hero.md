# Gyro Zeppeli Hero Refresh Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the generic robot in the profile hero with an original AI-operator interpretation of Gyro Zeppeli while preserving the current Blacksite Operator composition.

**Architecture:** The current WebP is the edit target and canonical character art is a temporary identity reference. Built-in ImageGen produces one edited candidate; local Pillow conversion normalizes it to the existing 1600-by-533 WebP contract. The README changes only its hero alt text.

**Tech Stack:** Built-in ImageGen edit mode, Pillow, GitHub Flavored Markdown, GitHub Markdown API, Playwright CLI, `git`, `gh`, `curl`.

## Global Constraints

- Preserve the 3:1 hero ratio, OLED-black terminal room, green CRTs, scanlines, low-key lighting, right-third subject placement, and approximately 55 percent dark negative space on the left.
- Gyro Zeppeli is recognizable through a wide-brim teal hat with goggles, long blond hair, confident expression, western-inspired clothing, and one Steel Ball with restrained phosphor-green Spin light.
- Do not add a horse, combat pose, weapon, franchise logo, manga lettering, generated text, excessive glitch, or rainbow neon.
- Change only `assets/gyro-blacksite.webp` and the hero alt text in `README.md`.
- Final repository tree remains `README.md` and `assets/gyro-blacksite.webp`.

---

### Task 1: Generate the edited Gyro Zeppeli hero

**Files:**
- Modify: `assets/gyro-blacksite.webp`
- Temporary identity reference: `/tmp/gyrroxx-profile-imagegen/gyro-zeppeli-reference.png`
- Temporary generated candidate: `/tmp/gyrroxx-profile-imagegen/gyro-zeppeli-candidate.webp`

**Interfaces:**
- Consumes: current `assets/gyro-blacksite.webp` as edit target and canonical character art as identity reference.
- Produces: a visually approved 1600-by-533 replacement WebP at the same repository path.

- [ ] **Step 1: Download the temporary identity reference**

```bash
mkdir -p /tmp/gyrroxx-profile-imagegen
curl -L -sS --max-time 30 'https://static.jojowiki.com/images/thumb/f/fc/latest/20260411021621/Gyro_Zeppeli_Infobox_Anime.png/1200px-Gyro_Zeppeli_Infobox_Anime.png' -o /tmp/gyrroxx-profile-imagegen/gyro-zeppeli-reference.png
sips -g pixelWidth -g pixelHeight -g format /tmp/gyrroxx-profile-imagegen/gyro-zeppeli-reference.png
```

Expected: a valid PNG character reference; it remains outside the repository and is never committed.

- [ ] **Step 2: Inspect both input images**

View `assets/gyro-blacksite.webp` as the edit target and `/tmp/gyrroxx-profile-imagegen/gyro-zeppeli-reference.png` as the supporting identity reference.

Expected: the target has the approved 3:1 terminal scene; the reference clearly shows Gyro's hat, goggles, hair, face, clothing, and Steel Ball design language.

- [ ] **Step 3: Edit the existing hero with built-in ImageGen**

Pass both local images with these roles and this exact prompt:

```text
Use case: compositing
Asset type: wide GitHub profile README hero banner
Input images: Image 1 is the edit target whose environment, framing, palette, lighting, and negative space must be preserved. Image 2 is a supporting identity reference for Gyro Zeppeli only; do not copy its background, pose, layout, or text.
Primary request: Replace only the small generic robot on the right side of Image 1 with an original AI-systems-operator interpretation of Gyro Zeppeli. Keep the existing terminal workstation and make him feel naturally seated or positioned at it.
Subject: recognizable Gyro Zeppeli with a wide-brim teal hat and goggles, long blond hair, confident calm expression, western-inspired clothing, and one Steel Ball resting near the console. Add a restrained phosphor-green Spin circuit glow to the Steel Ball and a subtle green terminal reflection on his face and clothing.
Style/medium: premium retro-computing tech-noir concept art, semi-realistic illustrated character, coherent with Image 1, not a manga panel and not a direct copy of Image 2.
Composition/framing: preserve Image 1's exact 3:1 composition, left 55 percent dark negative space, subject on the right third, and all major terminal geometry.
Lighting/mood: preserve low-key OLED-black lighting, green CRT glow, subtle scanlines, calm clandestine AI-lab mood.
Color palette: preserve #050505 and #111318 base, #39FF88 primary signal, and tiny #35D9FF, #FFB84D, #FF4FD8 diagnostics.
Constraints: change only the robot into Gyro Zeppeli and integrate the Steel Ball; keep the room, monitors, console, crop, reflections, and empty left side unchanged; no text, letters, numbers, logo, watermark, horse, weapon, combat pose, extra person, or franchise title.
Avoid: generic cyberpunk city, rainbow neon, excessive glitch, anime screenshot composition, distorted hands, malformed face, duplicated Steel Balls, cute robot proportions.
```

Expected: one new wide candidate that preserves the banner layout and reads as Gyro Zeppeli at README scale.

- [ ] **Step 4: Inspect the generated source at original resolution**

Reject the candidate if the left side is no longer empty, the subject is not recognizable, the hat/goggles/hair are malformed, the Steel Ball is duplicated, hands or face are distorted, text-like marks appear, or the terminal room changes materially.

- [ ] **Step 5: Normalize the accepted candidate to the repository asset contract**

```bash
export SOURCE_IMAGE="$(find "${CODEX_HOME:-$HOME/.codex}/generated_images" -type f \( -name '*.png' -o -name '*.jpg' -o -name '*.webp' \) -print0 | xargs -0 ls -t | head -n 1)"
test -n "$SOURCE_IMAGE"
python3 -c 'from PIL import Image; import os; p=os.environ["SOURCE_IMAGE"]; im=Image.open(p).convert("RGB"); w,h=im.size; tw=min(w,h*3); th=min(h,w//3); left=(w-tw)//2; top=(h-th)//2; im=im.crop((left,top,left+tw,top+th)); im.resize((1600,533),Image.Resampling.LANCZOS).save("/tmp/gyrroxx-profile-imagegen/gyro-zeppeli-candidate.webp","WEBP",quality=90,method=6)' 
sips -g pixelWidth -g pixelHeight -g format /tmp/gyrroxx-profile-imagegen/gyro-zeppeli-candidate.webp
du -h /tmp/gyrroxx-profile-imagegen/gyro-zeppeli-candidate.webp
```

Expected: WebP, exactly 1600 by 533 pixels, below 2 MB.

- [ ] **Step 6: Compare and accept the replacement**

View `/tmp/gyrroxx-profile-imagegen/gyro-zeppeli-candidate.webp` at original resolution. If it passes the design checks, copy it over `assets/gyro-blacksite.webp`.

```bash
cp /tmp/gyrroxx-profile-imagegen/gyro-zeppeli-candidate.webp assets/gyro-blacksite.webp
```

Expected: Git reports one modified binary asset and the previous version remains recoverable from history.

---

### Task 2: Update the hero accessibility text

**Files:**
- Modify: `README.md:2`

**Interfaces:**
- Consumes: the accepted Gyro Zeppeli hero.
- Produces: accurate accessible text without changing visible README content.

- [ ] **Step 1: Replace only the hero alt text**

Change the first image line to:

```html
  <img src="./assets/gyro-blacksite.webp" alt="Gyro Zeppeli reimagined as an AI operator in a blacksite terminal" width="100%">
```

- [ ] **Step 2: Prove the textual diff is narrow**

```bash
git diff -- README.md
```

Expected: exactly one alt-text line changes; all other README content is unchanged.

- [ ] **Step 3: Render through GitHub's Markdown API**

```bash
jq -n --rawfile text README.md '{text: $text, mode: "gfm", context: "gyrroxx/gyrroxx"}' > /tmp/gyrroxx-markdown.json
gh api markdown --input /tmp/gyrroxx-markdown.json > /tmp/gyrroxx-readme-gyro.html
rg -n 'gyro-blacksite|Gyro Zeppeli reimagined|Versus LLM|t\.me/dokaqq' /tmp/gyrroxx-readme-gyro.html
```

Expected: the new alt text, hero reference, project link, and Telegram link survive GitHub rendering.

---

### Task 3: Validate, publish, and verify the live profile

**Files:**
- Delete from final tree: `docs/superpowers/specs/2026-07-19-gyro-zeppeli-hero-design.md`
- Delete from final tree: `docs/superpowers/plans/2026-07-19-gyro-zeppeli-hero.md`
- Keep: `README.md`
- Keep: `assets/gyro-blacksite.webp`

**Interfaces:**
- Consumes: final asset and alt text.
- Produces: updated live profile at `https://github.com/gyrroxx`.

- [ ] **Step 1: Verify the complete diff and final asset**

```bash
git status -sb
git diff --check
git diff --stat origin/main...HEAD
git diff -- README.md
sips -g pixelWidth -g pixelHeight -g format assets/gyro-blacksite.webp
```

Expected: only the temporary spec/plan, one alt-text line, and the WebP replacement differ; asset is 1600 by 533 WebP.

- [ ] **Step 2: Remove temporary planning documents from the final tree**

Use `apply_patch` to delete both planning files, then stage only the two final deliverables and those two tracked deletions:

```bash
git add README.md assets/gyro-blacksite.webp
git add -u docs/superpowers/specs/2026-07-19-gyro-zeppeli-hero-design.md docs/superpowers/plans/2026-07-19-gyro-zeppeli-hero.md
git diff --cached --check
```

- [ ] **Step 3: Commit the approved replacement**

```bash
git commit -m "Feature Gyro Zeppeli in profile hero"
```

- [ ] **Step 4: Verify the clean local result**

```bash
test -z "$(git status --porcelain)"
git ls-tree -r --name-only HEAD
git diff --check origin/main...HEAD
```

Expected: clean worktree; final files are only `README.md` and `assets/gyro-blacksite.webp`.

- [ ] **Step 5: Push the approved main branch update**

```bash
git push origin main
```

Expected: `origin/main` advances to the local commit.

- [ ] **Step 6: Verify the live desktop and mobile profile**

Open `https://github.com/gyrroxx` with Playwright CLI, snapshot the page, and inspect at 1440 by 1000 and 390 by 844. At mobile width evaluate both `document.documentElement.scrollWidth` and `document.documentElement.clientWidth`.

Expected: the new mascot loads through GitHub Camo, the hero remains readable, and mobile scroll width equals client width.
