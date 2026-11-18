---
name: industrial-brutalist-ui
description: Applies one named aesthetic, industrial brutalism fusing Swiss typographic print with military terminal, using rigid grids, extreme type-scale contrast, utilitarian color, halftone, CRT and dither degradation, and no gradients or soft shadows. Select only when the user asks for brutalist, terminal, blueprint or declassified-document styling by name. Data-heavy screens only when that look is explicitly requested. This is NOT a default for dashboards or admin UI.
---

# SKILL: Industrial Brutalism & Tactical Telemetry UI

## 1. Skill Meta
**Name:** Industrial Brutalism & Tactical Telemetry Interface Engineering
**Description:** Advanced proficiency in architecting web interfaces that synthesize mid-century Swiss Typographic design, industrial manufacturing manuals, and retro-futuristic aerospace/military terminal interfaces. This discipline requires absolute mastery over rigid modular grids, extreme typographic scale contrast, purely utilitarian color palettes, and the programmatic simulation of analog degradation (halftones, CRT scanlines, bitmap dithering). The objective is to construct digital environments that project raw functionality, mechanical precision, and high data density, deliberately discarding conventional consumer UI patterns.

## 2. Visual Archetypes
The design system operates by merging two distinct but highly compatible visual paradigms. **Pick ONE per project and commit to it. Do not alternate or mix both modes within the same interface.**

### 2.1 Swiss Industrial Print
Derived from 1960s corporate identity systems and heavy machinery blueprints.
*   **Characteristics:** High-contrast light modes (newsprint/off-white substrates). Reliance on monolithic, heavy sans-serif typography. Unforgiving structural grids outlined by visible dividing lines. Aggressive, asymmetric use of negative space punctuated by oversized, viewport-bleeding numerals or letterforms. Heavy use of primary red as an alert/accent color.

### 2.2 Tactical Telemetry & CRT Terminal
Derived from classified military databases, legacy mainframes, and aerospace Heads-Up Displays (HUDs).
*   **Characteristics:** Dark mode exclusivity. High-density tabular data presentation. Absolute dominance of monospaced typography. Integration of technical framing devices (ASCII brackets, crosshairs). Application of simulated hardware limitations (phosphor glow, scanlines, low bit-depth rendering).

## 3. Typographic Architecture
Typography is the primary structural and decorative infrastructure. Imagery is secondary. The system demands extreme variance in scale, weight, and spacing.

### 3.1 Macro-Typography (Structural Headers)
*   **Classification:** Neo-Grotesque / Heavy Sans-Serif.
*   **Optimal Web Fonts:** Neue Haas Grotesk (Black), Inter (Extra Bold/Black), Archivo Black, Roboto Flex (Heavy), Monument Extended.
*   **Implementation Parameters:**
    *   **Scale:** Deployed at massive scales using fluid typography (e.g., `clamp(4rem, 10vw, 15rem)`).
    *   **Tracking (Letter-spacing):** Extremely tight, often negative (`-0.03em` to `-0.06em`), forcing glyphs to form solid architectural blocks.
    *   **Leading (Line-height):** Highly compressed (`0.85` to `0.95`).
    *   **Casing:** Exclusively uppercase for structural impact.

### 3.2 Micro-Typography (Data & Telemetry)
*   **Classification:** Monospace / Technical Sans.
*   **Optimal Web Fonts:** JetBrains Mono, IBM Plex Mono, Space Mono, VT323, Courier Prime.
*   **Implementation Parameters:**
    *   **Scale:** Fixed and small (`10px` to `14px` / `0.7rem` to `0.875rem`).
    *   **Tracking:** Generous (`0.05em` to `0.1em`) to simulate mechanical typewriter spacing or terminal matrices.
    *   **Leading:** Standard to tight (`1.2` to `1.4`).
    *   **Casing:** Exclusively uppercase. Used for all metadata, navigation, unit IDs, and coordinates.

### 3.3 Textural Contrast (Artistic Disruption)
*   **Classification:** High-Contrast Serif.
*   **Optimal Web Fonts:** Playfair Display, EB Garamond, Times New Roman.
*   **Implementation Parameters:** Used exceedingly sparingly. Must be subjected to heavy post-processing (halftone filters, 1-bit dithering) to degrade vector perfection and create textural juxtaposition against the clean sans-serifs.

## 4. Color System
The color architecture is uncompromising. Gradients, soft drop shadows, and modern translucency are strictly prohibited. Colors simulate physical media or primitive emissive displays.

**CRITICAL: Choose ONE substrate palette per project and use it consistently. Never mix light and dark substrates within the same interface.**

### If Swiss Industrial Print (Light):
*   **Background:** `#F4F4F0` or `#EAE8E3` (Matte, unbleached documentation paper).
*   **Foreground:** `#050505` to `#111111` (Carbon Ink).
*   **Accent:** `#E61919` or `#FF2A2A` (Aviation/Hazard Red). This is the ONLY accent color. Used for strike-throughs, thick structural dividing lines, or vital data highlights.

### If Tactical Telemetry (Dark):
*   **Background:** `#0A0A0A` or `#121212` (Deactivated CRT. Avoid pure `#000000`).
*   **Foreground:** `#EAEAEA` (White phosphor). This is the primary text color.
*   **Accent:** `#E61919` or `#FF2A2A` (Aviation/Hazard Red). Same red, same rules.
*   **Terminal Green (`#4AF626`):** Optional. Use ONLY for a single specific UI element (e.g., one status indicator or one data readout) — never as a general text color. If it doesn't serve a clear purpose, omit it entirely.

## 5. Layout and Spatial Engineering
The layout must appear mathematically engineered. It rejects conventional web padding in favor of visible compartmentalization.

*   **The Blueprint Grid:** Strict adherence to CSS Grid architectures. Elements do not float; they are anchored precisely to grid tracks and intersections.
*   **Visible Compartmentalization:** Extensive utilization of solid borders (`1px` or `2px solid`) to delineate distinct zones of information. Horizontal rules (`<hr>`) frequently span the entire container width to segregate operational units.
*   **Bimodal Density:** Layouts oscillate between extreme data density (tightly packed monospace metadata clustered together) and vast expanses of calculated negative space framing macro-typography.
*   **Geometry:** Absolute rejection of `border-radius`. All corners must be exactly 90 degrees to enforce mechanical rigidity.

## 6. UI Components and Symbology
Standard web UI conventions are replaced with utilitarian, industrial graphic elements.

*   **Syntax Decoration:** Utilization of ASCII characters to frame data points.
    *   *Framing:* `[ DELIVERY SYSTEMS ]`, `< RE-IND >`
    *   *Directional:* `>>>`, `///`, `\\\\`
*   **Industrial Markers:** Prominent integration of registration (`®`), copyright (`©`), and trademark (`™`) symbols functioning as structural geometric elements rather than legal text.
*   **Technical Assets:** Integration of crosshairs (`+`) at grid intersections, repeating vertical lines (barcodes), thick horizontal warning stripes, and randomized string data (e.g., `REV 2.6`, `UNIT / D-01`) to simulate active mechanical processes.

## 7. Textural and Post-Processing Effects
To prevent the design from appearing purely digital, simulated analog degradation is engineered into the frontend via CSS and SVG filters.

*   **Halftone and 1-Bit Dithering:** Transforming continuous-tone images or large serif typography into dot-matrix patterns. Achieved via pre-processing or CSS `mix-blend-mode: multiply` overlays combined with SVG radial dot patterns.
*   **CRT Scanlines:** For terminal interfaces, applying a `repeating-linear-gradient` to the background to simulate horizontal electron beam sweeps (e.g., `repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(0,0,0,0.1) 2px, rgba(0,0,0,0.1) 4px)`).
*   **Mechanical Noise:** A global, low-opacity SVG static/noise filter applied to the DOM root to introduce a unified physical grain across both dark and light modes.

## 8. Web Engineering Directives
1.  **Grid Determinism:** Utilize `display: grid; gap: 1px;` with contrasting parent/child background colors to generate mathematically perfect, razor-thin dividing lines without complex border declarations.
2.  **Semantic Rigidity:** Construct the DOM using precise semantic tags (`<data>`, `<samp>`, `<kbd>`, `<output>`, `<dl>`) to accurately reflect the technical nature of the telemetry.
3.  **Typography Clamping:** Implement CSS `clamp()` functions exclusively for macro-typography to ensure massive text scales aggressively while maintaining structural integrity across viewports.


---

## RULE OWNERSHIP

Rules in this file that also appear in other skills are copies. The canonical
owner of each is listed below. If a copy here differs from its canon, **the
canon wins** (priority P3 beats P4). See "Shared design rules" in
`../README.md` for the full priority ladder and the P0 protections that no
aesthetic exception may override.

| Rule here | Canonical owner |
|---|---|
| C1 optimal web fonts (§3) | `design-taste-frontend/SKILL.md` §4 - **declared exception below** |
| C4 gradients prohibited (§4) | `imagegen-frontend-web/SKILL.md` §13 - **declared exception below** |
| C6 bimodal density (§5) | `design-taste-frontend/SKILL.md` §7 - **declared exception below** |
| C16h mechanical noise (§7) | `design-taste-frontend/SKILL.md` §6 - **exception refused, see below** |

### DECLARED EXCEPTIONS

These replace the canonical rule, but **only while this skill is the selected
aesthetic** (priority P2). None of them may override P0: accessibility,
functional correctness, security, or a required technical constraint.

**Heavy grotesques and period serifs — overrides C1 (Inter / Roboto / Times are banned by default).**
- Why the aesthetic needs it: this look is Swiss print plus military terminal. It is built from heavy neo-grotesques (Neue Haas Grotesk Black, Archivo Black, Monument Extended) and, for the dossier archetype, period serifs. Inter at Extra Bold / Black and Roboto Flex Heavy belong to that set; the canon bans Inter as a *default body face at regular weight*, which is a different use. Times New Roman is period-correct for a declassified document.
- Trigger: this skill selected, and the weight actually used is Black / Extra Bold / Heavy. Times New Roman only in the dossier / declassified archetype.
- At pre-flight: the `[AUTO] Inter is not the default typeface` box passes if every Inter instance is at those weights. An Inter instance at 400-600 is still a failure.

**Scanline texture — overrides C4 (decorative gradients banned).**
- Why the aesthetic needs it: `repeating-linear-gradient` here is a CRT scanline generator, not a color wash. There is no other CSS primitive for it.
- Trigger: this skill selected, and the gradient is a repeating one-hue scanline or halftone pattern.
- At pre-flight: judged, not grepped. A multi-stop or multi-hue gradient is not covered by this exception.

**Bimodal density — overrides C6 (dial-conditional spacing).**
- Why the aesthetic needs it: the look depends on oscillation between cockpit-dense data and vast calculated negative space. A uniform section-padding floor flattens exactly the contrast that defines it.
- Trigger: this skill selected.
- At pre-flight: the hero `pt-24` cap still applies; section padding is judged against the stated oscillation instead of a floor.

### EXCEPTION REFUSED

**DOM-root noise filter — C16h stands.** The canon (`design-taste-frontend` §6)
requires grain on fixed `pointer-events-none` pseudo-elements and never on
scrolling containers, because continuous GPU repaints destroy mobile FPS. That
is a required technical constraint, so it sits at P0 and no aesthetic exception
reaches it. Section 7's "applied to the DOM root" wording is not granted an
exception: render the same unified grain on a `fixed inset-0 pointer-events-none`
layer, which is visually equivalent and does not repaint on scroll.
