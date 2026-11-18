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

## Shared design rules

The same design rule is restated across up to eight skills — 17 clusters in all,
and the copies had drifted into contradiction. The structure here is **one
canonical owner per rule, with an explicit priority order**. Duplicate text is
left in place; each copy now carries a pointer to its canon in a
`## RULE OWNERSHIP` section at the end of its `SKILL.md`.

### Priority ladder

| | | |
|---|---|---|
| **P0** | **Protected constraints — nothing overrides these** | Accessibility (contrast, focus visibility, `prefers-reduced-motion`, semantics), functional correctness, security, and required technical constraints (dependency checks before importing a library, viewport stability, no scroll-repaint patterns, animation cleanup). An aesthetic exception that would break one of these is refused, not granted. |
| P1 | The user's explicit requirement | The brief wins over the canon. |
| P2 | A declared exception of the selected aesthetic skill | Registered in that skill's `RULE OWNERSHIP` section, active only while that skill is selected. |
| P3 | The canonical rule | The default for every other request. |
| P4 | A copy of the rule left in another skill | If it differs from the canon, the canon wins. |

P2 beating P3 is safe because routing (see "Routing") only selects an aesthetic
skill when the user asked for that look by name — so by the time an exception
fires, P1 has effectively already been satisfied.

### Canonical owners

| Cluster | Rule | Canonical owner | Copies |
|---|---|---|---|
| C1 | banned typefaces / Inter | `design-taste-frontend` §4 | 9 |
| C2 | em-dash ban (page copy only) | `design-taste-frontend` §9.G | 1 |
| C3 | AI-purple / LILA | `design-taste-frontend` §4 | 9 |
| C4 | gradient policy | `imagegen-frontend-web` §13 | 6 |
| C5 | shadow discipline | `design-taste-frontend` §4 | 8 |
| C6 | spacing scale | `design-taste-frontend` §7 | 6 |
| C7 | motion library, never-mix | `design-taste-frontend` §5, §10 | 4 |
| C8 | infinite micro-motion | `design-taste-frontend` §5 | 4 |
| C9 | emoji policy | `design-taste-frontend` §3 | 5 |
| C10 | placeholder-content bans | `design-taste-frontend` §9 | 8 |
| C11 | anti-slop image rules | `imagegen-frontend-web` §8 | 2 |
| C12 | Variation Engine | `imagegen-frontend-web` §2 | 2 |
| C13 | do-not-crop rule | `image-to-code` §5 | 2 |
| C14 | dial baselines | `design-taste-frontend` §7 | 6 |
| C15 | pre-flight checklist | `design-taste-frontend` §14 | 7 |
| C16a | eyebrow-label cap | `design-taste-frontend` §4 | 3 |
| C16b | nested-container ban | `image-to-code` §16 | 2 |
| C16c | corner-radius consistency | `design-taste-frontend` §4 | 3 |
| C16d | centered hero | `design-taste-frontend` §4 | 6 |
| C16e | pure #000000 / #ffffff | `design-taste-frontend` §9 | 3 |
| C16f | icon library | `design-taste-frontend` §3 | 3 |
| C16g | hero headline line cap | `design-taste-frontend` §4 | 4 |
| C16h | grain / noise placement | `design-taste-frontend` §6 | 5 |
| C17 | v1 rule set restated in `stitch-design-taste` | `design-taste-frontend` overall | 4 |

`design-taste-frontend` owns 11 of the 17 clusters plus 6 of the 8 C16
sub-items. It was chosen because it is the only skill that already carried an
override mechanism — explicit exceptions for Inter, emoji, purple, the
beige-brass palette and the centered hero — so "the canon has declared
exceptions" is its existing shape, not a new one. C4, C11 and C12 went to
`imagegen-frontend-web` because its gradient section is the only graded policy
(an allowed list and a banned list) rather than a flat ban, and because it holds
the complete Variation Engine of which `image-to-code` §12 is a subset.

**C2 is scoped.** The em-dash ban governs rendered page copy, as §14's wording
already said. It is not a house style for markdown, specs, READMEs or commit
messages, and it is not applied to documents a skill writes into someone else's
project.

### Declared exceptions

17 candidates were reviewed against one test: *does the aesthetic actually need
this, or do the two rules merely disagree?* Result: **10 granted, 2 refused, 5
were not conflicts at all.** Each granted exception records the canon it
replaces, why the look needs it, its trigger, and how pre-flight treats it — in
the owning skill's `RULE OWNERSHIP` section.

| Skill | Granted | Refused | Not a conflict |
|---|---|---|---|
| `industrial-brutalist-ui` | heavy-grotesque / period fonts (C1), scanline gradient (C4), bimodal density (C6) | DOM-root noise filter (C16h) | — |
| `high-end-visual-design` | glow orbs, hue narrowed (C3), Double-Bezel at 2 levels (C16b), pill primaries (C16c), ultra-light icons (C16f) | eyebrow on every heading (C16a) | inset highlight (C5), section padding (C6) |
| `minimalist-ui` | pure-white surfaces, paired with an off-white canvas (C16e), Bold/Fill icon weight (C16f) | — | Helvetica as third fallback (C1) |
| `gpt-taste` | GSAP as the page's single motion library (C7) | — | centered hero (C16d), hero line cap (C16g) |

The two refusals are the point of the test. **C16h** was refused because the
canon's reason is a performance constraint — "continuous GPU repaints destroy
mobile FPS" — which sits at P0; the same grain renders identically on a fixed
`pointer-events-none` layer. **C16a** was refused because an eyebrow above every
heading is the templated rhythm the mechanical cap exists to catch, and it is
not what makes that look expensive.

Two granted exceptions carry P0 carve-outs written into them: the GSAP exception
does not waive the `package.json` dependency check or `prefers-reduced-motion`,
and the pure-white exception does not extend to pure `#000000`.

### D1–D3

- **D1 — `minimalist-ui` gradients.** The file banned gradients at §2 and then
  prescribed `radial-gradient` at §6, §7 and §8. Resolved inside the file rather
  than by exception, because it was a self-contradiction, not a clash with the
  canon: §2 now bans gradients *as decoration* and states the single carve-out —
  ambient light at `opacity: 0.02–0.04` on a fixed `pointer-events-none` layer,
  which is what §6 and §7 already specified.
- **D2 — infinite micro-motion.** `design-taste-frontend` reversed v1 on this
  deliberately. `stitch-design-taste` (both files) carried the v1 form and is now
  aligned to the canon: looping cues for genuinely live state, still cards
  otherwise. `design-taste-frontend-v1` keeps its original rule — it is a frozen
  archive and rewriting it would defeat the reason it exists — with a note at the
  rule naming the divergence and pointing to v2.
- **D3 — em-dashes in `stitch-design-taste/DESIGN.md`.** Not resolved by
  stripping the 41 instances. That template is a design-system document emitted
  into someone's project, and the canon's ban covers page copy. Both stitch files
  now state that scope explicitly. Applying one skill's page-copy style rule to
  another project's documentation would have been the wrong fix.

### Pre-flight

All 62 checks are kept. One bundled item — `No AI Tells from Section 9 (Inter as
default, AI-purple, three-equal cards, Jane Doe, Acme...)`, which was the sole
verification point for clusters C1, C3 and C10 and their 26 copies — was split
into four, each tagged for how it is verified. The checklist is now 65 items.

| New item | Verification |
|---|---|
| Inter not the default typeface | `[AUTO]` |
| No AI-purple by default | `[AUTO + JUDGMENT]` — a hit is judged, not failed outright |
| No three-equal-cards block | `[JUDGMENT]` — not greppable |
| No placeholder-content tells | `[AUTO]` |

**False positives were checked, not assumed.** Searching the bare string `Inter`
across this library returns 59 hits, almost all of them `Interpretation`,
`Interactions`, `Interface`, `Internal`, `Interactive`. The check therefore
specifies a whole-token match inside a `font-family` value, or `font-inter`, or
`family=Inter` in a Google Fonts URL, and says explicitly not to grep the bare
string. AI-purple cannot be decided by search at all — a purple brand is
legitimate under P1 — so that item lists the AI-default violet tokens and leaves
the verdict to judgment. Three-equal-cards is structural and marked judgment-only.

### Not implemented

Deleting the duplicate text (~370 lines across the 17 clusters) is not part of
this. The minimal-modification structure leaves copies in place and resolves
them by priority. Removing them is a separate decision.
