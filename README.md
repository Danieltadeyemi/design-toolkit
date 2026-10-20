# Design Toolkit

My working index for designing and building UI with AI that doesn't look AI-generated.

Two kinds of tools live here, and they do different jobs:

- **Taste skills** change *how the AI designs*: what it picks, what it avoids, what it checks before calling something done.
- **Component libraries** are ready-made animated pieces to drop into a real build. They don't give the AI taste; they save build time.

Source: a curated list from [@RoundtableSpace](https://x.com/RoundtableSpace/status/2110255627704455591) (Oct 2026), checked one by one. Two of the tweet's links were wrong and are corrected below.

---

## 1. Taste skills

### Design Taste — installed, vendored in [`/skills`](./skills)
[madebymustafa/design-taste](https://github.com/madebymustafa/design-taste) · MIT · 24 skills

The core of this toolkit. Plain-text skill files, no scripts, no external service. Reviewed in full before adding (Oct 20, 2026): pure design guidance, nothing that runs commands or sends data anywhere.

**Core:** `design-taste` bans the LLM defaults (purple gradients, centered badge hero, three equal cards, emoji icons, Inter + slate), forces a one-line "design read" before generating, and runs a pre-flight checklist before calling a page done.

**Style packs** — pick one per project, stack it on the core:

| Pack | Identity | Use for |
|---|---|---|
| `editorial-minimal` | Warm paper, ink, one vermillion accent, big serif, hairline grids | Publications, newsletters, personal brand |
| `quiet-luxury` | Ivory, espresso ink, brass/oxblood accent, serif with italic flourish | Premium consumer, personal brand, private banking |
| `corporate-trust` | White, one deep blue, system type, precise tables, every claim sourced | Fintech, B2B, regulated audiences |
| `dark-tech` | Near-black, hairline borders, one accent, data as the hero | Dev tools, infra, AI products |
| `brutalist-industrial` | Paper, ink, one signal colour, visible grid, uppercase grotesk | Data-heavy tools, studios |
| `neo-brutalism` | Thick borders, hard offset shadows, two hot accents | Loud consumer brands |
| `playful-color` | Giant type, flat colour fields, sticker shapes | D2C, events, youth brands |
| `retro-print` | Risograph inks, halftone, misregistration | Zines, events, food & music |
| `japanese-minimal` | Rice paper, sumi ink, seal red, negative space | Studios, wellness, calm brands |
| `cinematic-motion` | Scroll-driven "film", pinned sections, one electric blue | Launches, award-style portfolios (needs `taste-gsap`) |

**Craft skills** — load as needed:

| Skill | What it enforces |
|---|---|
| `taste-typography` | Pairing, fluid scales, line length, weight limits |
| `taste-color` | 60-30-10 palettes, OKLCH ramps, contrast math, semantic tokens |
| `taste-landing-page` | 8-second rule, section order that sells, CTA and pricing discipline |
| `taste-ux-copy` | Headlines, buttons, errors, empty states, banned filler words |
| `taste-motion` | Duration/easing tokens, what to animate, reduced-motion |
| `taste-gsap` | GSAP architecture, pin/scrub hygiene, no-JS fallbacks |
| `taste-design-system` | Three-tier tokens, scales, component state matrix |
| `taste-brand-identity` | Logo concept, wordmark, lockups, favicon, og-image |
| `taste-accessibility` | WCAG 2.2 AA built in during generation |
| `taste-design-review` | Screenshot-first audit, P0–P3 findings, one verdict |
| `taste-code-craft` | Semantic HTML, tokens over literals, no inline styles |
| `taste-code-review` | Pass-ordered code review with severity |
| `taste-web-performance` | LCP/CLS/INP budgets, font and image loading |

**Install in the Claude app:** upload [`claude-skill/design-taste.zip`](./claude-skill/design-taste.zip). It bundles all 24 as one skill: the core rules load every time, and it opens the matching style pack or craft guide only when a task needs it.

**Install in Claude Code:** copy any folder from `/skills` into `~/.claude/skills/`.

### Superdesign skill — try if needed
[superdesigndev/superdesign-skill](https://github.com/superdesigndev/superdesign-skill) · MIT

A full design process for coding agents: pulls style references, extracts a site's "design DNA" from a URL, generates several branchable variations to compare. Most powerful option, but it runs through the superdesign.dev service and needs a login.

```
/plugin marketplace add superdesigndev/superdesign-skill
/plugin install superdesign@superdesign
npm install -g @superdesign/cli@latest && superdesign login
```

Note: the tweet linked `superdesigndev/superdesign`, which is the old, unmaintained VS Code extension. Use the skill repo above.

### Better Design — for code-heavy projects
[marvkr/better-design](https://github.com/marvkr/better-design) · MIT

A design-token server with 31 ready design systems (Linear, Stripe, Vercel, Apple style), UI principles and review rules, exposed to the agent as tools. Heavier setup (runs a local server), most useful inside a real codebase.

```
npx skills add marvkr/better-design --skill better-design
npx better-design
```

---

## 2. Component libraries

Ranked by maturity. All React-first unless noted.

| Library | What you get | License | Notes |
|---|---|---|---|
| [Motion Primitives](https://github.com/ibelick/motion-primitives) | Animated UI pieces (Motion + Tailwind) | MIT | 6.2k★. Docs: motion-primitives.com/docs. Still labelled beta. |
| [UI Layouts](https://github.com/ui-layouts/ui-layouts) | Creative components, effects, ready blocks | MIT | 3.8k★. Copy from ui-layouts.com. Needs `motion clsx tailwind-merge`. |
| [Paper Shaders](https://github.com/paper-design/shaders) | Animated gradient/shader backgrounds, zero dependencies | Apache-2.0 | 3.4k★. `npm i @paper-design/shaders-react`. Can be designed visually in Paper. Pin the version (0.0.x). |
| [Cursify](https://github.com/ui-layouts/cursify) | Cursor animation effects | **None stated** | 2k★. Check with the authors before commercial use. |
| [Canvas UI](https://github.com/DavidHDev/canvas-ui) | WebGL effects: liquid, glass, shatter, VHS | MIT + Commons Clause | React/Vue/Svelte/vanilla. Best effects need an experimental Chrome flag; falls back to plain WebGL. `npx shadcn@latest add https://canvasui.dev/r/liquid-react.json` |
| [Hyperiux Components](https://github.com/Hyperiux-Immersion-Labs/hyperiux-components) | 50+ free animation effects for Next.js, CLI-installable | MIT (free tier) | 100+ more are paid Pro. Tweet link was wrong; this is the real repo. |
| [Trickle UI Kit](https://github.com/akaieuan/trickle-UI-kit) | Pure-CSS text animations, no runtime | MIT | Small (51★). Tweet link was wrong; this is the real repo. |

### More libraries (from [@DevDsgn](https://x.com/DevDsgn/status/2112483056577835482), Oct 2026)

| Library | What you get | Price / license | Notes |
|---|---|---|---|
| [beUI](https://beui.dev) | 143 animated components, 23 blocks, 13 charts, 18 AI-chat interface pieces (prompt input, voice orb, message); React Native too | Free, MIT · Pro tier paid | **Best of this batch.** Built for agents: has an `llms.txt` and "for coding agents" docs. `npx shadcn add @beui/button`. Pro adds templates, an agent skill and MCP. |
| [interior.dev](https://interior.dev) | 54 micro-interactions: loading button, hold-to-confirm, segmented control, like burst | Free, MIT | 1.1k★. React + Tailwind + Motion, installs via shadcn CLI. Great for making app screens feel finished. |
| [Cue](https://cuedesign.space) | Curated "Awwwards-tier" heroes, animations, interactions, each shipped with a ready AI prompt | Paid ($99 lifetime) · license not stated | The prompts are the selling point. Only worth it if the free libraries don't cover a signature moment. |
| [RareUI](https://github.com/Codewithswappy/RareUI) | Animated premium-look components (e.g. liquid metal) | Free, MIT | Small (17★). `npx rareui add liquid-metal`. Repo points to rareui.in; rareui.com blocks automated checks, so the link between them isn't confirmed. |
| [FeralUI](https://feralui.dev) | Physics-driven experiments: pull cord, claw-machine captcha, crumple, fur | No install or license info | Inspiration, not a library. Look, don't copy-paste. |

**Rule of thumb:** use these for one or two signature moments per page, not everywhere.

**Getting Claude to use them well:** pasting a site URL teaches it little. Install the component into the project first (the shadcn commands above), or point it at a library's `llms.txt`, so it works from the real code. The taste skills (`taste-motion`, `cinematic-motion`) set the budget.

---

## 3. Workflow

1. **Pick the read.** One line: audience, vibe, one style pack. ("Founder-focused publication, editorial-minimal, serif display, vermillion accent.")
2. **Collect 3–5 references** (Mobbin, Godly, Awwwards, real sites). Ask the AI to describe what makes each work, then build from the principles, not a clone.
3. **Lock tokens first** (colours, type scale, spacing) with `taste-design-system`, then build one key screen.
4. **Screenshot and critique** with `taste-design-review`. Iterate 3–6 rounds; that's where the quality comes from.
5. **Add motion last**, from the component libraries, within the budget the pack allows.
6. **Ship checks:** `taste-accessibility`, `taste-web-performance`, and the core pre-flight checklist.

---

*Design Taste skills © 2026 Mustafa, MIT licensed — see [`skills/LICENSE-design-taste`](./skills/LICENSE-design-taste).*
