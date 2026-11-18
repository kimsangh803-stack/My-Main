# Skills

Sixteen skills live here, installed two different ways. See "Two install
layouts" below, and "Routing" for which skill owns which kind of request.

## Design taste skills (13)

Thirteen frontend/design skills from
[Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill)
(MIT — see `LICENSE-taste-skill.txt`), all thirteen vendored copies taken from
upstream commit `ccbc156`. Their `description` lines have since been rewritten
for routing (see "Routing"); their bodies are upstream's, with one approved
exception noted there.

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

| | Vendored copies (13) | CLI-installed (3) |
|---|---|---|
| Installed by | manual copy | `npx skills add` |
| Files live in | `.claude/skills/<name>/` | `.agents/skills/<name>/` |
| Discovered via | the directory itself | relative symlink from `.claude/skills/` |
| Pinned by | upstream commit noted above | `skills-lock.json` (content hash) |

**Reinstalling a vendored skill through the CLI silently replaces it.** Running
`npx skills add` for a name that already exists as a real directory under
`.claude/skills/` deletes that directory and puts a symlink in its place; the
CLI reports this only as `overwrites: Claude Code` in its summary. That is how
`high-end-visual-design` moved between layouts, and why it was moved back.

**Why `high-end-visual-design` was restored to the vendored layout.** While it
was CLI-installed it was hash-pinned in `skills-lock.json`, which made its
`description` effectively read-only: editing it would have left the stored hash
stale and the next `npx skills add` would have silently discarded the edit. That
skill needed a description rewrite more than any other — it was mis-matching
three of the routing test cases below — so it was moved back to a real directory
under `.claude/skills/`, its `.agents/` copy removed and its lock entry dropped.
Its body is byte-identical to the CLI-installed copy. Any local edits to a
vendored skill are lost if it is reinstalled, so commit before reinstalling.

`.agents/skills/` is the tool-agnostic location the `skills` CLI installs to, so
those skills are readable by other agent tools too; the symlink is relative, so
it survives a clone. Nothing breaks by mixing the layouts — just know that three
entries under `.claude/skills/` are links rather than directories, and that only
`.agents/`-installed skills are tracked in `skills-lock.json`.

## Routing

Each skill's `description` is its whole routing surface — nothing else about it
is read when a request is matched. The descriptions were rewritten so that every
one states the artifact it produces, the surface it applies to, and what it is
**not** for. Bodies were not touched, with one exception recorded below.

### Priority rules

A single description can only say "I am not for X"; it cannot express a ranking
against another skill. These six rules are the library-level convention, encoded
piecewise into each description's NOT clauses:

| | Rule | Resolves |
|---|---|---|
| R1 | A named aesthetic beats generic design | `minimalist-ui` / `industrial-brutalist-ui` / `high-end-visual-design` vs a generic request |
| R2 | The artifact kind is the first branch: code, images-only, or a document | `imagegen-*` vs code skills vs `stitch-design-taste` |
| R3 | An existing codebase beats a greenfield build | `redesign-existing-projects` vs `frontend-design` |
| R4 | An explicitly named skill always wins | `design-taste-frontend-v1`, which must never be chosen by inferring intent |
| R5 | `full-output-enforcement` is a modifier, never a direction — it may be selected alongside another skill | an orthogonal skill being picked as the design direction |
| R6 | If the artifact kind is still undetermined, ask one question, then proceed | "apply our brand design system", which could mean images, a document, or code |

### Ownership split

- **`frontend-design` owns general frontend UI work.** A bare "build me a
  premium landing page" goes here.
- **`design-taste-frontend` is the specialist for design-quality review and
  anti-slop rule enforcement.** It is selected when the build must conform to a
  named design system (Material, Carbon, Fluent, Polaris, shadcn, with install
  commands) or must pass its mechanical gates. **Do not put these two back into
  competition on generic requests.**
- Its pre-flight checklist (§14, 62 items) and its hard-fail rules — the em-dash
  ban (§9.G) and the eyebrow-label cap (§4) — **are kept, not retired.** They
  are the reason the skill exists.
- **`redesign-existing-projects` owns requests about an existing codebase**, as
  the more specific skill, even though `frontend-design` also mentions
  "reshaping an existing one". That residual co-match is accepted rather than
  resolved by editing a third-party skill.

### Known gap

No skill here owns **admin dashboards, dense product UI or data tables**.
`design-taste-frontend` §13 excludes them explicitly and points to Fluent,
Carbon, Atlassian or Polaris; `industrial-brutalist-ui` covers data-heavy
screens only when that look is asked for by name. Zero matches is the intended
behaviour — use a real design system.

### The one body change

`image-to-code` §2.A (`WHEN THE USER SUPPLIES THE IMAGE`, 11 lines) was added.
Before it, the skill's name won requests to implement a screenshot the user
already had, and then §2 told it to generate its own image instead and ignore
the one supplied. Every extraction rule (§21–25) was written against "the
generated image". §2.A makes a supplied image the source and scopes the
mandatory-generation rule to the case where none was supplied.

### Still overlapping, by design

`design-mobile-apps` and `imagegen-frontend-mobile` both cover mobile app screen
design: the first calls out to sleek.design and needs a paid API key, the second
generates images locally with no external service. Their descriptions now name
each other, but if you want a specific one, say so.

## Follow-up: shared design rules (Candidate 2)

Routing is now separated, but the **rules themselves still have no owner.** The
same rule is restated across up to eight skills — 17 duplicated clusters in all
— and the copies contradict each other. There are only two cross-references in
the whole library, which is why every shared rule drifted independently.

Known contradictions, none of them resolved here:

| Rule | Bans it | Prescribes it |
|---|---|---|
| Inter / Helvetica | 8 skills | `industrial-brutalist-ui:28`, `minimalist-ui:26` |
| purple "AI" gradients | 9 skills | `high-end-visual-design:25` |
| infinite micro-motion | `design-taste-frontend:358` | `design-taste-frontend-v1:70,207`, `stitch-design-taste:92`, `stitch-design-taste/DESIGN.md:95` |
| gradients | `minimalist-ui:3,18` | `minimalist-ui:67,74,84` (same file) |
| GSAP everywhere | `design-taste-frontend:360`, `design-taste-frontend-v1:129`, `high-end-visual-design:70` | `gpt-taste:47` |
| `py-24` minimum | `high-end-visual-design:51`, `gpt-taste:29`, `minimalist-ui:79` | `design-taste-frontend:566` (tight at density 8–10) |
| em-dash | `design-taste-frontend:685` | `stitch-design-taste/DESIGN.md` carries 41 of them |

Candidate 2 should decide, per cluster, **which skill owns the rule, what
precedence applies when two disagree, and how an exception is declared** — and
connect that ownership to `design-taste-frontend`'s pre-flight checks, which are
the only mechanical enforcement point in the library. Nothing in this section
has been implemented.
