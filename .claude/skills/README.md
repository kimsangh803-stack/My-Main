# Skills

Sixteen skills live here, installed two different ways. See "Two install
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


## Skills installed via the `skills` CLI (3)

`frontend-design` comes from [anthropics/skills](https://github.com/anthropics/skills)
(Apache 2.0, `LICENSE.txt` sits beside its `SKILL.md`). It covers aesthetic
direction, typography, and copywriting for new or reshaped UI.

`improve-codebase-architecture` comes from
[mattpocock/skills](https://github.com/mattpocock/skills). It scans a codebase
for deepening opportunities, renders them as a visual HTML report, then walks
through whichever one you pick. It sets `disable-model-invocation: true`, so it
never triggers on its own — invoke it as `/improve-codebase-architecture`.

That skill delegates to three sibling skills from the same repo that are **not
installed here**: `codebase-design` (its architecture vocabulary),
`grilling` (the decision-tree walkthrough after you pick a candidate), and
`domain-modeling` (keeping `CONTEXT.md` current). Without them the vocabulary
has to be pulled in by hand and the follow-up steps degrade. Install them the
same way if you want the full flow:

```
npx skills add https://github.com/mattpocock/skills --skill codebase-design
npx skills add https://github.com/mattpocock/skills --skill grilling
npx skills add https://github.com/mattpocock/skills --skill domain-modeling
```

It also expects a `CONTEXT.md` domain glossary and ADRs in `docs/adr/`; neither
exists in this repo yet.

`design-mobile-apps` comes from
[designed-by-ai/skills](https://github.com/designed-by-ai/skills). Unlike the
other two it is not standalone guidance — it is a client for
[sleek.design](https://sleek.design), a commercial mobile-app design service,
and it does nothing without that service. Before relying on it:

- **It needs a `SLEEK_API_KEY`**, which is not set in this environment. The skill
  can obtain one through a device flow (`/api/v1/device/start` + `/poll`) or via
  `https://sleek.design/agents/setup`.
- **It is a paid service.** The skill states free accounts get one-time trial
  credits worth roughly one design run, and that sustained use needs a Pro plan
  it prices at $49.99/month or $360/year. Those figures are the skill's own
  claims, unverified here.
- **Its declared host allowlist is incomplete.** The frontmatter says
  `allowed-hosts: https://sleek.design`, but the body also directs fetches to
  `https://api.iconify.design` (icon SVGs) and Google Fonts, and embeds an image
  from `raw.githubusercontent.com`. Whatever enforces that allowlist will not
  match what the skill actually does.
- **Provenance is worth a look.** It was installed from `designed-by-ai/skills`,
  but its hero image points at `sleekdotdesign/agent-skills` — so this copy is a
  third-party mirror of the vendor's own skill rather than the vendor repo.
- **No licence file ships with it**, unlike `frontend-design`.

Nothing in it is hostile: it is an API reference plus usage discipline, with no
destructive or data-exfiltrating instructions. But it sends your design briefs,
and any `imageUrls` you pass, to a third-party service.

## Two install layouts

The two sources landed differently, and both are kept as-is:

| | Design taste skills | CLI-installed skills |
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

`design-mobile-apps` and `imagegen-frontend-mobile` both claim mobile app screen
design, by very different means: the first calls out to sleek.design and needs a
paid API key, the second generates images locally with no external service. A
request like "design my app's screens" matches both. Name the one you want.
