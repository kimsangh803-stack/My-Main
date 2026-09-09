# Skills

Fourteen skills live here, installed two different ways. See "Two install
layouts" below.

## Design taste skills (13)

Thirteen frontend/design skills vendored from
[Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill)
(MIT — see `LICENSE-taste-skill.txt`), pinned at upstream commit `ccbc156`.

Claude Code auto-discovers everything under `.claude/skills/`, so these load in
any session opened in this repo. Invoke one by name (`/design-taste-frontend`)
or just describe the work — each skill's `description` says when it triggers.

### Skills

| Skill | What it does |
|---|---|
| `design-taste-frontend` | Default anti-slop skill for landing pages, portfolios, redesigns. Infers a design direction, tunes VARIANCE / MOTION / DENSITY, runs a pre-flight check. |
| `design-taste-frontend-v1` | The original v1 of the above, kept for exact backward compatibility. |
| `gpt-taste` | Awwwards-level UI plus advanced GSAP motion — AIDA structure, editorial typography, ScrollTrigger pinning/scrubbing. |
| `high-end-visual-design` | The "expensive agency" look: fonts, spacing, shadows, card structure, animation; blocks cheap AI defaults. |
| `minimalist-ui` | Clean editorial interfaces (Notion/Linear): warm monochrome, flat bento grids, no gradients or heavy shadows. |
| `industrial-brutalist-ui` | Swiss print × military terminal. Rigid grids, extreme type contrast, analog degradation. (Beta) |
| `redesign-existing-projects` | Audits an existing site/app, names the generic patterns, upgrades without breaking behavior. |
| `stitch-design-taste` | Generates agent-friendly `DESIGN.md` design systems for Google Stitch. Ships a reference `DESIGN.md`. |
| `image-to-code` | Image-first workflow: generate the design image, analyze it deeply, then build code that matches. |
| `imagegen-frontend-web` | Website design reference images — one horizontal image per section. Images only, no code. |
| `imagegen-frontend-mobile` | Premium mobile screen concepts and flows in phone mockups. Images only, no code. |
| `brandkit` | Brand-guideline boards, logo systems, identity decks. Images only, no code. |
| `full-output-enforcement` | Overrides truncation: complete code, no placeholder comments, clean token-limit splits. |

### Renamed directories

Upstream directory names don't always match the `name` in each `SKILL.md`.
Directories here use the frontmatter name so discovery and validation stay
consistent:

| Upstream | Here |
|---|---|
| `taste-skill` | `design-taste-frontend` |
| `taste-skill-v1` | `design-taste-frontend-v1` |
| `gpt-tasteskill` | `gpt-taste` |
| `soft-skill` | `high-end-visual-design` |
| `minimalist-skill` | `minimalist-ui` |
| `brutalist-skill` | `industrial-brutalist-ui` |
| `redesign-skill` | `redesign-existing-projects` |
| `stitch-skill` | `stitch-design-taste` |
| `image-to-code-skill` | `image-to-code` |
| `output-skill` | `full-output-enforcement` |

`brandkit`, `imagegen-frontend-web`, and `imagegen-frontend-mobile` already
matched.

### Updating

Re-copy from upstream, keeping the rename mapping above, and update the pinned
commit in this file. Upstream `research/`, `examples/`, `scripts/`, and the
`.claude-plugin/` marketplace metadata were not vendored — the skill bodies are
self-contained.


## frontend-design (1)

`frontend-design` comes from [anthropics/skills](https://github.com/anthropics/skills)
(Apache 2.0, `LICENSE.txt` sits beside its `SKILL.md`), installed with
`npx skills add`. It covers aesthetic direction, typography, and copywriting for
new or reshaped UI.

## Two install layouts

The two sources landed differently, and both are kept as-is:

| | Design taste skills | `frontend-design` |
|---|---|---|
| Installed by | manual copy | `npx skills add` |
| Files live in | `.claude/skills/<name>/` | `.agents/skills/<name>/` |
| Discovered via | the directory itself | relative symlink from `.claude/skills/` |
| Pinned by | upstream commit noted above | `skills-lock.json` (content hash) |

`.agents/skills/` is the tool-agnostic location the `skills` CLI installs to, so
those skills are readable by other agent tools too; the symlink is relative, so
it survives a clone. Nothing breaks by mixing the layouts — just know that
`.claude/skills/frontend-design` is a link, not a directory, and that only
`.agents/`-installed skills are tracked in `skills-lock.json`.

## Overlapping triggers

`frontend-design`, `design-taste-frontend`, `gpt-taste`, and
`high-end-visual-design` all match a bare request like "design me a landing
page", and they do not agree with each other. `frontend-design` names as
AI tells several things the taste skills prescribe — warm-cream/serif/terracotta
palettes, ALL-CAPS eyebrow labels, `->` appended to button text, per-section
fade-and-slide-up entrances — while `gpt-taste` mandates GSAP ScrollTrigger
choreography and `high-end-visual-design` fixes specific fonts and shadows.

Name the skill you want explicitly (`/frontend-design`) rather than relying on
description matching, or narrow the descriptions of the ones you keep.
