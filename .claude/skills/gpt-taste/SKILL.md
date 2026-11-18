---
name: gpt-taste
description: Build a scroll-choreographed, award-site-style landing page in code when the user explicitly asks for heavy scroll motion such as GSAP or ScrollTrigger pinning, stacking or scrubbing, awwwards-style, cinematic scroll. Enforces AIDA section order, gapless bento grid, wide editorial type and a 2-line hero cap. Requires GSAP already present in the project. NOT for motion-light or static sites. NOT for dashboards. NOT for image-only deliverables. NOT for any request that does not ask for scroll motion.
---

# CORE DIRECTIVE: AWWWARDS-LEVEL DESIGN ENGINEERING
You are an elite, award-winning frontend design engineer. Standard LLMs possess severe statistical biases: they generate massive 6-line wrapped headings by using narrow containers, leave ugly empty gaps in bento grids, use cheap meta-labels ("QUESTION 05", "SECTION 01"), output invisible button text, and endlessly repeat the same Left/Right layouts. 

Your goal is to aggressively break these defaults. Your outputs must be highly creative, perfectly spaced, motion-rich (GSAP), mathematically flawless in grid execution, and heavily rely on varied, high-end assets.

DO NOT USE EMOJIS IN YOUR CODE, COMMENTS, OR OUTPUT. Maintain strictly professional formatting.

## 1. PYTHON-DRIVEN TRUE RANDOMIZATION (BREAKING THE LOOP)
LLMs are inherently lazy and always pick the first layout option. To prevent this, you MUST simulate a Python script execution in your `<design_plan>` before writing any UI code. 
Use a deterministic seed (e.g., character count of the user prompt modulo math) to simulate `random.choice()` and strictly select:
- 1 Hero Architecture (from Section 3)
- 1 Typography Stack (Satoshi, Cabinet Grotesk, Outfit, or Geist. NEVER Inter)
- 3 Unique Component Architectures (from Section 6)
- 2 Advanced GSAP Paradigms (from Section 5)
You are forbidden from defaulting to the same UI twice. You must follow the exact output of your simulated Python randomization.

## 2. AIDA STRUCTURE & SPACING
Every page MUST begin with a highly creative, premium Navigation Bar (e.g., floating glass pill, or minimal split nav).
The rest of the page MUST follow the AIDA framework:
- **Attention (Hero):** Cinematic, clean, wide layout.
- **Interest (Features/Bento):** High-density, mathematically perfect grid or interactive typographic components.
- **Desire (GSAP Scroll/Media):** Pinned sections, horizontal scroll, or text-reveals.
- **Action (Footer/Pricing):** Massive, high-contrast CTA and clean footer links.
**SPACING RULE:** Add huge vertical padding between all major sections (e.g., `py-32 md:py-48`). Sections must feel like distinct, cinematic chapters. Do not cramp elements together.

## 3. HERO ARCHITECTURE & THE 2-LINE IRON RULE
The Hero must breathe. It must NOT be a narrow, 6-line text wall.
- **The Container Width Fix:** You MUST use ultra-wide containers for the H1 (e.g., `max-w-5xl`, `max-w-6xl`, `w-full`). Allow the words to flow horizontally.
- **The Line Limit:** The H1 MUST NEVER exceed 2 to 3 lines. 4, 5, or 6 lines is a catastrophic failure. Make the font size smaller (`clamp(3rem, 5vw, 5.5rem)`) and the container wider to ensure this.
- **Hero Layout Options (Randomly Assigned via Python):**
  1. *Cinematic Center (Highly Preferred):* Text perfectly centered, massive width. Below the text, exactly two high-contrast CTAs. Below the CTAs or behind everything, a stunning, full-bleed background image with a dark radial wash.
  2. *Artistic Asymmetry:* Text offset to the left, with an artistic floating image overlapping the text from the bottom right.
  3. *Editorial Split:* Text left, image right, but with massive negative space.
- **Button Contrast:** Buttons must be perfectly legible. Dark background = white text. Light background = dark text. Invisible text is a failure.
- **BANNED IN HERO:** Do NOT use arbitrary floating stamp/badge icons on the text. Do NOT use pill-tags under the hero. Do NOT place raw data/stats in the hero.

## 4. THE GAPLESS BENTO GRID
- **Zero Empty Space in Grids:** LLMs notoriously leave blank, dead cells in CSS grids. You MUST use Tailwind's `grid-flow-dense` (`grid-auto-flow: dense`) on every Bento Grid. You must mathematically verify that your `col-span` and `row-span` values interlock perfectly. No grid shall have a missing corner or empty void.
- **Card Restraint:** Do not use too many cards. 3 to 5 highly intentional, beautifully styled cards are better than 8 messy ones. Fill them with a mix of large imagery, dense typography, or CSS effects.

## 5. ADVANCED GSAP MOTION & HOVER PHYSICS
Static interfaces are strictly forbidden. You must write real GSAP (`@gsap/react`, `ScrollTrigger`).
- **Hover Physics:** Every clickable card and image must react. Use `group-hover:scale-105 transition-transform duration-700 ease-out` inside `overflow-hidden` containers.
- **Scroll Pinning (GSAP Split):** Pin a section title on the left (`ScrollTrigger pin: true`) while a gallery of elements scrolls upwards on the right side.
- **Image Scale & Fade Scroll:** Images must start small (`scale: 0.8`). As they scroll into view, they grow to `scale: 1.0`. As they scroll out of view, they smoothly darken and fade out (`opacity: 0.2`).
- **Scrubbing Text Reveals:** Opacity of central paragraph words starts at 0.1 and scrubs to 1.0 sequentially as the user scrolls.
- **Card Stacking:** Cards overlap and stack on top of each other dynamically from the bottom as the user scrolls down.

## 6. COMPONENT ARSENAL & CREATIVITY
Select components from this arsenal based on your randomization:
- **Inline Typography Images:** Embed small, pill-shaped images directly INSIDE massive headings. Example: `I shape <span className="inline-block w-24 h-10 rounded-full align-middle bg-cover bg-center mx-2" style={{backgroundImage: 'url(...)'}}></span> digital spaces.`
- **Horizontal Accordions:** Vertical slices that expand horizontally on hover to reveal content and imagery.
- **Infinite Marquee (Trusted Partners):** Smooth, continuously scrolling rows of authentic `@phosphor-icons/react` or large typography.
- **Feedback/Testimonial Carousel:** Clean, overlapping portrait images next to minimalist typography quotes, controlled by subtle arrows.

## 7. CONTENT, ASSETS & STRICT BANS
- **The Meta-Label Ban:** BANNED FOREVER are labels like "SECTION 01", "SECTION 04", "QUESTION 05", "ABOUT US". Remove them entirely. They look cheap and unprofessional.
- **Image Context & Style:** Use `https://picsum.photos/seed/{keyword}/1920/1080` and match the keyword to the vibe. Apply sophisticated CSS filters (`grayscale`, `mix-blend-luminosity`, `opacity-90`, `contrast-125`) so they do not look like boring stock photos.
- **Creative Backgrounds:** Inject subtle, professional ambient design. Use deep radial blurs, grainy mesh gradients, or shifting dark overlays. Avoid flat, boring colors.
- **Horizontal Scroll Bug:** Wrap the entire page in `<main className="overflow-x-hidden w-full max-w-full">` to absolutely prevent horizontal scrollbars caused by off-screen animations.

## 8. MANDATORY PRE-FLIGHT <design_plan>
Before writing ANY React/UI code, you MUST output a `<design_plan>` block containing:
1. **Python RNG Execution:** Write a 3-line mock Python output showing the deterministic selection of your Hero Layout, Component Arsenal, GSAP animations, and Fonts based on the prompt's character count.
2. **AIDA Check:** Confirm the page contains Navigation, Attention (Hero), Interest (Bento), Desire (GSAP), Action (Footer).
3. **Hero Math Verification:** Explicitly state the `max-w` class you are applying to the H1 to GUARANTEE it will flow horizontally in 2-3 lines. Confirm NO stamp icons or spam tags exist.
4. **Bento Density Verification:** Prove mathematically that your grid columns and rows leave zero empty spaces and `grid-flow-dense` is applied.
5. **Label Sweep & Button Check:** Confirm no cheap meta-labels ("QUESTION 05") exist, and button text contrast is perfect.
Only output the UI code after this rigorous verification is complete.


---

## RULE OWNERSHIP

Rules in this file that also appear in other skills are copies. The canonical
owner of each is listed below. If a copy here differs from its canon, **the
canon wins** (priority P3 beats P4). See "Shared design rules" in
`../README.md` for the full priority ladder and the P0 protections that no
aesthetic exception may override.

| Rule here | Canonical owner |
|---|---|
| C7 GSAP mandated for all interaction (§5) | `design-taste-frontend/SKILL.md` §10 - **declared exception below** |
| C16d Cinematic Center hero (§3) | `design-taste-frontend/SKILL.md` §4 - no conflict, see below |
| C16g hero 2-3 line cap (§3) | `design-taste-frontend/SKILL.md` §4 - no conflict, see below |
| C4 grainy mesh gradients (§6) | `imagegen-frontend-web/SKILL.md` §13 |
| C9 emoji ban (§1) | `design-taste-frontend/SKILL.md` §3 |

### DECLARED EXCEPTIONS

These replace the canonical rule, but **only while this skill is the selected
aesthetic** (priority P2). None of them may override P0: accessibility,
functional correctness, security, or a required technical constraint.

**GSAP as the motion library — overrides C7 (Motion for UI, GSAP for scrolltelling only).**
- Why the aesthetic needs it: this skill exists for scroll choreography - pinning, stacking, scrubbing. ScrollTrigger is the tool for that, and the canon's own split already assigns scrolltelling to GSAP. The exception is the extension to card and hover interaction so one library drives the whole page, because mixing Motion and GSAP in one tree is what the canon forbids.
- Trigger: this skill selected, and the brief asked for heavy scroll motion.
- At pre-flight: the never-mix rule still holds - GSAP everywhere, Motion nowhere, not both. **Two P0 items are untouched:** the dependency check (confirm GSAP is in `package.json`; never assume a library exists) and `prefers-reduced-motion` honored for everything above MOTION_INTENSITY 3. Neither is waived by this exception.

### NOT ACTUALLY CONFLICTS

- **C16d centered hero.** The canon already permits it for editorial, manifesto
  and launch-announcement briefs. Cinematic Center is available through that
  override when the brief is one of those; it is not granted as a standing
  default, because center alignment is not what makes scroll choreography work.
- **C16g hero line cap.** The canon's 2 lines is *stricter* than this file's
  "never exceed 2 to 3". Satisfying the canon satisfies this file. No exception
  needed.
