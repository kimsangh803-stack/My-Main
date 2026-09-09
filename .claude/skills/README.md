# Design taste skills

Thirteen frontend/design skills vendored from
[Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill)
(MIT — see `LICENSE-taste-skill.txt`), pinned at upstream commit `ccbc156`.

Claude Code auto-discovers everything under `.claude/skills/`, so these load in
any session opened in this repo. Invoke one by name (`/design-taste-frontend`)
or just describe the work — each skill's `description` says when it triggers.

## Skills

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

## Renamed directories

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

## Updating

Re-copy from upstream, keeping the rename mapping above, and update the pinned
commit in this file. Upstream `research/`, `examples/`, `scripts/`, and the
`.claude-plugin/` marketplace metadata were not vendored — the skill bodies are
self-contained.
