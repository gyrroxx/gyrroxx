# SHAKH Profile README Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Publish a high-impact English GitHub profile README for `gyrroxx` using the approved Blacksite Operator direction and only verified claims.

**Architecture:** A single `README.md` composes one repository-owned WebP hero with Markdown/limited HTML, a FIGlet identity block, reputable remote SVG cards, and standard HTTPS links. There is no application runtime, workflow, dependency, secret, analytics, or custom hosted service.

**Tech Stack:** GitHub Flavored Markdown, repository-hosted WebP, FIGlet ASCII, ImageGen, Shields.io, Readme Typing SVG, GitHub Readme Stats, `git`, `gh`, `curl`.

## Global Constraints

- Use OLED black `#050505`, graphite `#111318`, warm white `#E7ECE8`, phosphor green `#39FF88`, with cyan `#35D9FF`, amber `#FFB84D`, and magenta `#FF4FD8` only as restrained signals.
- Exact positioning is `SHAKH // AI SPECIALIST & DEVELOPER`.
- Exact subtitle is `building intelligent systems, AI products, and experimental software`.
- Public facts are limited to 34 owned repositories, 3 years with AI, 6+ months of deep engineering focus, the verified selected systems, and `https://t.me/dokaqq`.
- Versus LLM is public and linked; GyroLAB and Drip Cards are labeled `PRIVATE SYSTEM` without repository links.
- Avoid Matrix rain, skulls, fake security claims, excessive glitch, rainbow neon, progress bars, invented metrics, client/revenue claims, emoji-heavy headings, and long autobiography.
- Final tree contains only `README.md` and `assets/gyro-blacksite.webp`.

---

### Task 1: Generate and prepare the Gyro hero

**Files:**
- Create: `assets/gyro-blacksite.webp`
- Temporary external input: `/tmp/gyrroxx-profile-imagegen/gyro-blacksite-source.png`

**Interfaces:**
- Consumes: approved Blacksite Operator palette and mascot brief.
- Produces: `assets/gyro-blacksite.webp`, a wide repository-owned hero referenced by `README.md`.

- [ ] **Step 1: Generate one original source image with the built-in ImageGen tool**

Use this exact prompt:

```text
Use case: stylized-concept
Asset type: wide GitHub profile README hero banner
Primary request: Create Gyro, a compact abstract AI operator robot mascot inside a covert old-web terminal workstation. The mascot should feel intelligent, calm, slightly mysterious, and technically capable rather than cute or threatening.
Scene/backdrop: deep OLED-black command room with sparse CRT terminal geometry, subtle scanlines, small diagnostic lights, and generous clean negative space on the left for profile identity placed later outside the image.
Subject: one compact non-humanoid AI operator mascot positioned on the right third, with a simple memorable silhouette and one phosphor-green optical signal.
Style/medium: premium retro-computing concept art, restrained Watch Dogs-like systems mood without copying any franchise asset, sharp graphic detail, cinematic but readable at README width.
Composition/framing: 3:1 wide banner, subject on right third, left 55 percent quiet and dark, no important detail near edges.
Lighting/mood: low-key terminal glow, controlled contrast, confident and clandestine, not horror.
Color palette: #050505 and #111318 base; #39FF88 primary signal; very small #35D9FF, #FFB84D, and #FF4FD8 accents.
Constraints: no text, no letters, no numbers, no logos, no watermark, no human face, no skull, no Matrix rain, no weapon, no busy cityscape.
Avoid: generic cyberpunk wallpaper, rainbow neon, excessive glitch, clutter, cute toy proportions, photorealistic human anatomy.
```

Expected: one landscape raster with no generated typography and usable left-side negative space.

- [ ] **Step 2: Inspect the source image at original resolution**

Use the image viewer and reject it if it contains text-like glyphs, a human face, skull imagery, a franchise logo, excessive neon, or insufficient negative space.

- [ ] **Step 3: Copy and convert the selected image**

```bash
mkdir -p assets /tmp/gyrroxx-profile-imagegen
SOURCE_IMAGE="$(find "${CODEX_HOME:-$HOME/.codex}/generated_images" -type f \( -name '*.png' -o -name '*.jpg' -o -name '*.webp' \) -print0 | xargs -0 ls -t | head -n 1)"
test -n "$SOURCE_IMAGE" && cp "$SOURCE_IMAGE" /tmp/gyrroxx-profile-imagegen/gyro-blacksite-source.png
python3 -c 'from PIL import Image; p="/tmp/gyrroxx-profile-imagegen/gyro-blacksite-source.png"; im=Image.open(p).convert("RGB"); w,h=im.size; tw=min(w,h*3); th=min(h,w//3); left=(w-tw)//2; top=(h-th)//2; im=im.crop((left,top,left+tw,top+th)); ow=min(1600,im.width); oh=round(ow/3); im.resize((ow,oh),Image.Resampling.LANCZOS).save("assets/gyro-blacksite.webp","WEBP",quality=88,method=6)'
```

Expected: `assets/gyro-blacksite.webp` exists, width is at most 1600 px, and the image opens correctly.

- [ ] **Step 4: Validate size and visual legibility**

```bash
sips -g pixelWidth -g pixelHeight -g format assets/gyro-blacksite.webp
du -h assets/gyro-blacksite.webp
```

Expected: WebP format, landscape aspect ratio close to 3:1, and file size below 2 MB.

- [ ] **Step 5: Commit the asset**

```bash
git add assets/gyro-blacksite.webp
git commit -m "Add Gyro blacksite profile artwork"
```

---

### Task 2: Build the profile README

**Files:**
- Create: `README.md`

**Interfaces:**
- Consumes: `assets/gyro-blacksite.webp`, verified GitHub/project facts, public remote SVG endpoints.
- Produces: the complete GitHub profile document.

- [ ] **Step 1: Generate FIGlet identity from the official FIGlet ecosystem**

```bash
npx --yes figlet-cli@0.1.0 -f ANSI Shadow SHAKH
```

Expected: deterministic ASCII text spelling `SHAKH`; paste it into the README in a fenced `text` block and include a short FIGlet attribution in an HTML comment.

- [ ] **Step 2: Create the complete README**

Create `README.md` with this exact section order and copy contract:

```markdown
<p align="center"><img src="./assets/gyro-blacksite.webp" alt="Gyro AI operator in a blacksite terminal" width="100%"></p>

<h1 align="center">SHAKH // AI SPECIALIST &amp; DEVELOPER</h1>
<p align="center"><code>building intelligent systems, AI products, and experimental software</code></p>

<p align="center">
  <a href="https://git.io/typing-svg"><img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&amp;weight=500&amp;size=17&amp;duration=2600&amp;pause=900&amp;color=39FF88&amp;center=true&amp;vCenter=true&amp;width=720&amp;lines=booting+intelligence...;agents+%2F+products+%2F+systems;signal+locked+%E2%80%94+building+the+next+thing" alt="Animated terminal introduction"></a>
</p>

<!-- FIGlet 2.2.5 / ANSI Shadow; FIGlet is distributed under the New BSD license. -->
```text
███████╗██╗  ██╗ █████╗ ██╗  ██╗██╗  ██╗
██╔════╝██║  ██║██╔══██╗██║ ██╔╝██║  ██║
███████╗███████║███████║█████╔╝ ███████║
╚════██║██╔══██║██╔══██║██╔═██╗ ██╔══██║
███████║██║  ██║██║  ██║██║  ██╗██║  ██║
╚══════╝╚═╝  ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝
```

## `> whoami`

I build AI agents and full-stack products that turn model capability into useful software. My work sits between product engineering, interface design, and the systems that make AI tools dependable.

`3 YEARS WITH AI` · `6+ MONTHS DEEP FOCUS` · `34 REPOSITORIES`

## `> systems --selected`

### `01 // Versus LLM` · `PUBLIC SYSTEM`
Two LLM agents debate a question in the terminal; a judge model returns a concise verdict. Published as an installable Python CLI.

[`OPEN REPOSITORY`](https://github.com/gyrroxx/versus-llm)

### `02 // GyroLAB` · `PRIVATE SYSTEM`
A local browser-first coding agent with streaming tool calls, workspace editing, diff review, rollback, PTY, model controls, and guarded execution through OpenRouter.

### `03 // Drip Cards` · `PRIVATE SYSTEM`
A Telegram collectible product spanning an aiogram bot, Next.js Mini App, PostgreSQL economy, live operations tooling, and real-prize mechanics.

## `> arsenal --verified`

Python · TypeScript · Next.js · Node.js · PostgreSQL · Docker · Telegram Mini Apps · OpenRouter / LLM Agents · Git · macOS tooling

## `> github --signal`

<p align="center">
  <img height="165" src="https://github-readme-stats.vercel.app/api?username=gyrroxx&amp;show_icons=true&amp;hide_border=true&amp;bg_color=050505&amp;title_color=39FF88&amp;text_color=E7ECE8&amp;icon_color=35D9FF&amp;ring_color=FF4FD8" alt="Shakh's GitHub statistics">
  <img height="165" src="https://github-readme-stats.vercel.app/api/top-langs?username=gyrroxx&amp;layout=compact&amp;hide_border=true&amp;bg_color=050505&amp;title_color=39FF88&amp;text_color=E7ECE8" alt="Most used public repository languages">
</p>

Most active systems are private; public statistics show only part of the work.

## `> contact --open-channel`

<a href="https://t.me/dokaqq"><img src="https://img.shields.io/badge/OPEN_SECURE_CHANNEL-TELEGRAM-35D9FF?style=for-the-badge&amp;logo=telegram&amp;logoColor=050505" alt="Contact Shakh on Telegram"></a>

`GYRO STATUS: ONLINE // CHANNEL SECURE // READY FOR THE NEXT SYSTEM`
```

Use one green typing animation, compact Shields.io signal badges, and at most two GitHub stats cards. Encode all query values correctly. Do not make the Telegram control look like an inert image: wrap the badge in a text-capable anchor.

- [ ] **Step 3: Review claims and private-project treatment**

Run:

```bash
rg -n "client|revenue|income|users|downloads|professional|expert|private.*github.com/gyrroxx/(gyro-lab|drip-cards)" README.md
```

Expected: no invented outcome metrics and no link to either private repository.

- [ ] **Step 4: Render through GitHub Markdown API**

```bash
jq -n --rawfile text README.md '{text: $text, mode: "gfm", context: "gyrroxx/gyrroxx"}' > /tmp/gyrroxx-markdown.json
gh api markdown --input /tmp/gyrroxx-markdown.json > /tmp/gyrroxx-readme.html
rg -n "gyro-blacksite|Versus LLM|t.me/dokaqq|readme-typing-svg" /tmp/gyrroxx-readme.html
```

Expected: all four elements appear in the rendered HTML.

- [ ] **Step 5: Commit README**

```bash
git add README.md
git diff --cached --check
git commit -m "Build Blacksite Operator profile README"
```

---

### Task 3: Validate, clean the final tree, and publish

**Files:**
- Delete from final tree: `docs/superpowers/specs/2026-07-19-profile-readme-design.md`
- Delete from final tree: `docs/superpowers/plans/2026-07-19-profile-readme.md`
- Keep: `README.md`
- Keep: `assets/gyro-blacksite.webp`

**Interfaces:**
- Consumes: completed hero and README.
- Produces: live `https://github.com/gyrroxx` profile.

- [ ] **Step 1: Validate local and remote links**

```bash
test -s assets/gyro-blacksite.webp
for url in https://t.me/dokaqq https://github.com/gyrroxx/versus-llm https://readme-typing-svg.demolab.com https://github-readme-stats.vercel.app; do curl -LIsS --max-time 20 "$url" | head -n 1; done
```

Expected: local asset is non-empty and each endpoint returns an HTTP response without DNS/TLS failure.

- [ ] **Step 2: Remove planning artifacts from the final tree**

```bash
git rm docs/superpowers/specs/2026-07-19-profile-readme-design.md docs/superpowers/plans/2026-07-19-profile-readme.md
git add README.md assets/gyro-blacksite.webp
git commit -m "Finalize GitHub profile"
```

- [ ] **Step 3: Run final repository checks**

```bash
git diff --check HEAD~3..HEAD
git status --short
find . -type f -not -path './.git/*' -print | sort
git log --oneline --decorate -5
```

Expected: clean worktree; final non-git files are only `README.md` and `assets/gyro-blacksite.webp`.

- [ ] **Step 4: Push the profile branch**

```bash
git push -u origin main
```

Expected: `main` is created on `gyrroxx/gyrroxx` and tracks `origin/main`.

- [ ] **Step 5: Verify the live GitHub profile**

```bash
gh api repos/gyrroxx/gyrroxx/readme --jq '.html_url'
curl -LIsS --max-time 20 https://github.com/gyrroxx | head -n 1
```

Open `https://github.com/gyrroxx` and verify hero loading, no horizontal overflow, readable hierarchy, working project/Telegram links, graceful typing/stat-card rendering, and acceptable appearance in GitHub light and dark themes.
