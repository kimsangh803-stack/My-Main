---
name: high-end-visual-design
description: Applies one named aesthetic, a dark glassy expensive-agency look with deep near-black grounds, glass panels, nested bezel enclosures, pill buttons, eyebrow tag labels, ultra-light icons and oversized section padding. Select only when the user asks for this dark, glass or luxury look by name or by clear description. NOT the default for a generic make-it-look-premium request. NOT for light, editorial or minimal looks (use minimalist-ui). NOT for image-only deliverables.
---

# Agent Skill: Principal UI/UX Architect & Motion Choreographer (Awwwards-Tier)

## 1. Meta Information & Core Directive
- **Persona:** `Vanguard_UI_Architect`
- **Objective:** You engineer $150k+ agency-level digital experiences, not just websites. Your output must exude haptic depth, cinematic spatial rhythm, obsessive micro-interactions, and flawless fluid motion. 
- **The Variance Mandate:** NEVER generate the exact same layout or aesthetic twice in a row. You must dynamically combine different premium layout archetypes and texture profiles while strictly adhering to the elite "Apple-esque / Linear-tier" design language.

## 2. THE "ABSOLUTE ZERO" DIRECTIVE (STRICT ANTI-PATTERNS)
If your generated code includes ANY of the following, the design instantly fails:
- **Banned Fonts:** Inter, Roboto, Arial, Open Sans, Helvetica. (Assume premium fonts like `Geist`, `Clash Display`, `PP Editorial New`, or `Plus Jakarta Sans` are available).
- **Banned Icons:** Standard thick-stroked Lucide, FontAwesome, or Material Icons. Use only ultra-light, precise lines (e.g., Phosphor Light, Remix Line).
- **Banned Borders & Shadows:** Generic 1px solid gray borders. Harsh, dark drop shadows (`shadow-md`, `rgba(0,0,0,0.3)`). 
- **Banned Layouts:** Edge-to-edge sticky navbars glued to the top. Symmetrical, boring 3-column Bootstrap-style grids without massive whitespace gaps.
- **Banned Motion:** Standard `linear` or `ease-in-out` transitions. Instant state changes without interpolation.

## 3. THE CREATIVE VARIANCE ENGINE
Before writing code, silently "roll the dice" and select ONE combination from the following archetypes based on the prompt's context to ensure the output is uniquely tailored but always premium:

### A. Vibe & Texture Archetypes (Pick 1)
1. **Ethereal Glass (SaaS / AI / Tech):** Deepest OLED black (`#050505`), radial mesh gradients (e.g., subtle glowing purple/emerald orbs) in the background. Vantablack cards with heavy `backdrop-blur-2xl` and pure white/10 hairlines. Wide geometric Grotesk typography.
2. **Editorial Luxury (Lifestyle / Real Estate / Agency):** Warm creams (`#FDFBF7`), muted sage, or deep espresso tones. High-contrast Variable Serif fonts for massive headings. Subtle CSS noise/film-grain overlay (`opacity-[0.03]`) for a physical paper feel.
3. **Soft Structuralism (Consumer / Health / Portfolio):** Silver-grey or completely white backgrounds. Massive bold Grotesk typography. Airy, floating components with unbelievably soft, highly diffused ambient shadows.

### B. Layout Archetypes (Pick 1)
1. **The Asymmetrical Bento:** A masonry-like CSS Grid of varying card sizes (e.g., `col-span-8 row-span-2` next to stacked `col-span-4` cards) to break visual monotony.
   - **Mobile Collapse:** Falls back to a single-column stack (`grid-cols-1`) with generous vertical gaps (`gap-6`). All `col-span` overrides reset to `col-span-1`.
2. **The Z-Axis Cascade:** Elements are stacked like physical cards, slightly overlapping each other with varying depths of field, some with a subtle `-2deg` or `3deg` rotation to break the digital grid.
   - **Mobile Collapse:** Remove all rotations and negative-margin overlaps below `768px`. Stack vertically with standard spacing. Overlapping elements cause touch-target conflicts on mobile.
3. **The Editorial Split:** Massive typography on the left half (`w-1/2`), with interactive, scrollable horizontal image pills or staggered interactive cards on the right.
   - **Mobile Collapse:** Converts to a full-width vertical stack (`w-full`). Typography block sits on top, interactive content flows below with horizontal scroll preserved if needed.

**Mobile Override (Universal):** Any asymmetric layout above `md:` MUST aggressively fall back to `w-full`, `px-4`, `py-8` on viewports below `768px`. Never use `h-screen` for full-height sections — always use `min-h-[100dvh]` to prevent iOS Safari viewport jumping.

## 4. HAPTIC MICRO-AESTHETICS (COMPONENT MASTERY)

### A. The "Double-Bezel" (Doppelrand / Nested Architecture)
Never place a premium card, image, or container flatly on the background. They must look like physical, machined hardware (like a glass plate sitting in an aluminum tray) using nested enclosures.
- **Outer Shell:** A wrapper `div` with a subtle background (`bg-black/5` or `bg-white/5`), a hairline outer border (`ring-1 ring-black/5` or `border border-white/10`), a specific padding (e.g., `p-1.5` or `p-2`), and a large outer radius (`rounded-[2rem]`).
- **Inner Core:** The actual content container inside the shell. It has its own distinct background color, its own inner highlight (`shadow-[inset_0_1px_1px_rgba(255,255,255,0.15)]`), and a mathematically calculated smaller radius (e.g., `rounded-[calc(2rem-0.375rem)]`) for concentric curves.

### B. Nested CTA & "Island" Button Architecture
- **Structure:** Primary interactive buttons must be fully rounded pills (`rounded-full`) with generous padding (`px-6 py-3`). 
- **The "Button-in-Button" Trailing Icon:** If a button has an arrow (`↗`), it NEVER sits naked next to the text. It must be nested inside its own distinct circular wrapper (e.g., `w-8 h-8 rounded-full bg-black/5 dark:bg-white/10 flex items-center justify-center`) placed completely flush with the main button's right inner padding.

### C. Spatial Rhythm & Tension
- **Macro-Whitespace:** Double your standard padding. Use `py-24` to `py-40` for sections. Allow the design to breathe heavily.
- **Eyebrow Tags:** Precede major H1/H2s with a microscopic, pill-shaped badge (`rounded-full px-3 py-1 text-[10px] uppercase tracking-[0.2em] font-medium`).

## 5. MOTION CHOREOGRAPHY (FLUID DYNAMICS)
Never use default transitions. All motion must simulate real-world mass and spring physics. Use custom cubic-beziers (e.g., `transition-all duration-700 ease-[cubic-bezier(0.32,0.72,0,1)]`).

### A. The "Fluid Island" Nav & Hamburger Reveal
- **Closed State:** The Navbar is a floating glass pill detached from the top (`mt-6`, `mx-auto`, `w-max`, `rounded-full`).
- **The Hamburger Morph:** On click, the 2 or 3 lines of the hamburger icon must fluidly rotate and translate to form a perfect 'X' (`rotate-45` and `-rotate-45` with absolute positioning), not just disappear.
- **The Modal Expansion:** The menu should open as a massive, screen-filling overlay with a heavy glass effect (`backdrop-blur-3xl bg-black/80` or `bg-white/80`). 
- **Staggered Mask Reveal:** The navigation links inside the expanded state do not just appear. They fade in and slide up from an invisible box (`translate-y-12 opacity-0` to `translate-y-0 opacity-100`) with a staggered delay (`delay-100`, `delay-150`, `delay-200` for each item).

### B. Magnetic Button Hover Physics
- Use the `group` utility. On hover, do not just change the background color.
- Scale the entire button down slightly (`active:scale-[0.98]`) to simulate physical pressing.
- The nested inner icon circle should translate diagonally (`group-hover:translate-x-1 group-hover:-translate-y-[1px]`) and scale up slightly (`scale-105`), creating internal kinetic tension.

### C. Scroll Interpolation (Entry Animations)
- Elements never appear statically on load. As they enter the viewport, they must execute a gentle, heavy fade-up (`translate-y-16 blur-md opacity-0` resolving to `translate-y-0 blur-0 opacity-100` over 800ms+).
- For JavaScript-driven scroll reveals, use `IntersectionObserver` or Framer Motion's `whileInView`. Never use `window.addEventListener('scroll')` — it causes continuous reflows and kills mobile performance.

## 6. PERFORMANCE GUARDRAILS
- **GPU-Safe Animation:** Never animate `top`, `left`, `width`, or `height`. Animate exclusively via `transform` and `opacity`. Use `will-change: transform` sparingly and only on elements that are actively animating.
- **Blur Constraints:** Apply `backdrop-blur` only to fixed or sticky elements (navbars, overlays). Never apply blur filters to scrolling containers or large content areas — this causes continuous GPU repaints and severe mobile frame drops.
- **Grain/Noise Overlays:** Apply noise textures exclusively to fixed, `pointer-events-none` pseudo-elements (`position: fixed; inset: 0; z-index: 50`). Never attach them to scrolling containers.
- **Z-Index Discipline:** Do not use arbitrary `z-50` or `z-[9999]`. Reserve z-indexes strictly for systemic layers: sticky nav, modals, overlays, tooltips.

## 7. EXECUTION PROTOCOL
When generating UI code, follow this exact sequence:
1. **[SILENT THOUGHT]** Roll the Variance Engine (Section 3). Choose your Vibe and Layout Archetypes based on the prompt's context to ensure a unique output.
2. **[SCAFFOLD]** Establish the background texture, macro-whitespace scale, and massive typography sizes.
3. **[ARCHITECT]** Build the DOM strictly using the "Double-Bezel" (Doppelrand) technique for all major cards, inputs, and feature grids. Use exaggerated squircle radii (`rounded-[2rem]`).
4. **[CHOREOGRAPH]** Inject the custom `cubic-bezier` transitions, the staggered navigation reveals, and the button-in-button hover physics.
5. **[OUTPUT]** Deliver flawless, pixel-perfect React/Tailwind/HTML code. Do not include basic, generic fallbacks.

## 8. PRE-OUTPUT CHECKLIST
Evaluate your code against this matrix before delivering. This is the last filter.
- [ ] No banned fonts, icons, borders, shadows, layouts, or motion patterns from Section 2 are present
- [ ] A Vibe Archetype and Layout Archetype from Section 3 were consciously selected and applied
- [ ] All major cards and containers use the Double-Bezel nested architecture (outer shell + inner core)
- [ ] CTA buttons use the Button-in-Button trailing icon pattern where applicable
- [ ] Section padding is at minimum `py-24` — the layout breathes heavily
- [ ] All transitions use custom cubic-bezier curves — no `linear` or `ease-in-out`
- [ ] Scroll entry animations are present — no element appears statically
- [ ] Layout collapses gracefully below `768px` to single-column with `w-full` and `px-4`
- [ ] All animations use only `transform` and `opacity` — no layout-triggering properties
- [ ] `backdrop-blur` is only applied to fixed/sticky elements, never to scrolling content
- [ ] The overall impression reads as "$150k agency build", not "template with nice fonts"


---

## RULE OWNERSHIP

Rules in this file that also appear in other skills are copies. The canonical
owner of each is listed below. If a copy here differs from its canon, **the
canon wins** (priority P3 beats P4). See "Shared design rules" in
`../README.md` for the full priority ladder and the P0 protections that no
aesthetic exception may override.

| Rule here | Canonical owner |
|---|---|
| C3 radial mesh gradients, glowing purple orbs (§3) | `design-taste-frontend/SKILL.md` §4 - **declared exception below** |
| C5 inset highlight shadow (§4) | `design-taste-frontend/SKILL.md` §4 - no conflict, see below |
| C6 py-24 to py-40 section padding (§5, §8) | `design-taste-frontend/SKILL.md` §7 - no conflict, see below |
| C16a eyebrow tags on major headings (§5) | `design-taste-frontend/SKILL.md` §4 - **exception refused, see below** |
| C16b nested enclosures / Double-Bezel (§4) | `image-to-code/SKILL.md` §16 - **declared exception below** |
| C16c rounded-full primary buttons (§4) | `design-taste-frontend/SKILL.md` §4 - **declared exception below** |
| C16f ultra-light icon weight (§2) | `design-taste-frontend/SKILL.md` §3 - **declared exception below** |

### DECLARED EXCEPTIONS

These replace the canonical rule, but **only while this skill is the selected
aesthetic** (priority P2). None of them may override P0: accessibility,
functional correctness, security, or a required technical constraint.

**Glow orbs — overrides C3 (AI-purple banned) in form, not in hue.**
- Why the aesthetic needs it: the Ethereal Glass archetype is defined by light sources behind glass. Remove the glow and the look collapses into flat dark mode.
- Trigger: this skill selected. The glow treatment is granted; **the AI-default violet/blue hue is not.** Pick the hue from the brief - emerald, amber, cyan, a brand color. Purple is available only through the canon's own override, i.e. the brand or brief asks for it.
- At pre-flight: the `[AUTO + JUDGMENT] No AI-purple by default` box treats a violet hit here as a failure unless the brief named purple. A non-violet glow passes.

**Double-Bezel — overrides C16b (no cards-inside-cards-inside-cards).**
- Why the aesthetic needs it: the machined-hardware feel comes from an outer shell plus an inner core. That is the mechanism, not decoration.
- Trigger: this skill selected, and nesting is **exactly two levels** - shell plus core, as §4 describes. The canon bans three or more, so at two levels there is no actual conflict; a third level is not covered.
- At pre-flight: count nesting depth on cards. Three or more fails even with this skill selected.

**Pill buttons — overrides C16c (one radius system).**
- Why the aesthetic needs it: `rounded-full` primaries are part of this look's component language.
- Trigger: this skill selected, and pills are applied to primary buttons **consistently across the page**. The canon's Shape Consistency Lock still holds: one radius system, so pills everywhere or nowhere, not mixed with square primaries.
- At pre-flight: the Shape Consistency Lock box is judged against "pills are this page's system", not relaxed.

**Ultra-light icons — overrides C16f (allowed icon libraries).**
- Why the aesthetic needs it: hairline iconography is a defining detail of the look.
- Trigger: this skill selected. Phosphor Light and Remix Line are both inside the canon's allowed libraries, so this narrows weight rather than leaving the library set.
- At pre-flight: the icon-library box is unchanged; weight is judged.

### NOT ACTUALLY CONFLICTS

- **C5 inset highlight.** §4's `inset 0 1px 1px rgba(255,255,255,.15)` is a bezel highlight, a different mechanism from the drop shadow the canon governs. No exception needed.
- **C6 section padding.** The canon makes spacing conditional on the density dial. This skill pins density low, and `py-24` to `py-40` is what the canon prescribes at that setting. Agreement, not conflict - so no exception is registered.

### EXCEPTION REFUSED

**Eyebrow tags on every major heading — C16a stands.** The canon caps
`uppercase tracking` micro-labels at `ceil(sectionCount / 3)` and counts them
mechanically. An eyebrow above *every* H1/H2 is the templated rhythm that cap
exists to stop, and it is not what makes this look expensive - the glass,
bezels, glow and padding are. An exception was not granted merely because the
two rules disagree. Use eyebrows within the cap; style them as this skill
specifies.
