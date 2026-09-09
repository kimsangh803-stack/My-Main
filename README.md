# My-Main

Working repository. Skills for Claude Code live in
[`.claude/skills/`](.claude/skills/README.md) — sixteen of them, from four
sources:

- thirteen design-taste skills from
  [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill) (MIT)
- `frontend-design` from
  [anthropics/skills](https://github.com/anthropics/skills) (Apache 2.0)
- `improve-codebase-architecture` from
  [mattpocock/skills](https://github.com/mattpocock/skills)
- `design-mobile-apps` from
  [designed-by-ai/skills](https://github.com/designed-by-ai/skills)

Twelve are vendored copies; the other four were installed with `npx skills add`
and are hash-pinned in `skills-lock.json`. Most load automatically in any Claude
Code session opened here. `improve-codebase-architecture` is invoked explicitly,
and `design-mobile-apps` needs a `SLEEK_API_KEY` and a paid sleek.design plan —
see the [skills README](.claude/skills/README.md) before using it.
