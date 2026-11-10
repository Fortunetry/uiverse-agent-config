# AI Agent UI Integration Rules & Design System

This file defines the mandatory protocols for fetching, selecting, and adapting UI components directly from external repositories—specifically the official **Uiverse Galaxy** library (`https://github.com/uiverse-io/galaxy`)—into this project.

## 1. Primary Component Source

* **Repository:** `https://github.com/uiverse-io/galaxy`

* **Raw Repository Base URL:** `https://raw.githubusercontent.com/uiverse-io/galaxy/main/`

* **Design Styles Supported:** Neobrutalism, Glassmorphism, Neumorphism, Claymorphism, Retro / 8-Bit & 16-Bit UI, Flat 2.0, Modern Minimalist.

## 2. Core Directives for AI Agents

Whenever the user prompts for a UI component (e.g., button, card, input, loader, checkbox, form, navbar):

1. **Do Not Reinvent the Wheel:** Look up component structural patterns and styling techniques available in the `uiverse-io/galaxy` repository or apply equivalent Uiverse-style visual primitives.

2. **Retrieve / Adapt Visual Styles:** Extract the required HTML layout and CSS rules or transform raw CSS declarations into utility classes (Tailwind CSS) if requested by the project context.

3. **Preserve Authentic Aesthetic:** Maintain key properties such as `backdrop-filter`, `box-shadow` layering, border-radii, pixel-perfect borders, and accent color contrasts as defined by the target style.

## 3. Style Execution Guidelines

### A. Neobrutalism

* **Borders:** Thick, solid borders (e.g., `2px` or `4px` `solid #000000`).

* **Shadows:** Hard, non-blurred offset shadows (e.g., `box-shadow: 4px 4px 0px #000000`).

* **Palette:** Vibrant, high-contrast background colors paired with deep blacks.

* **Typography:** Bold sans-serif or monospace fonts.

### B. Glassmorphism

* **Background:** Semi-transparent white or dark fills (e.g., `rgba(255, 255, 255, 0.15)`).

* **Blur:** `backdrop-filter: blur(10px)` or higher.

* **Borders:** Subtle translucent borders (e.g., `1px solid rgba(255, 255, 255, 0.2)`).

* **Shadows:** Soft, wide-spread drop shadows.

### C. Neumorphism (Soft UI)

* **Background:** Flat element color matching the parent canvas background identically.

* **Shadows:** Dual-contrast box shadows (`drop-shadow` + `inner-shadow`) creating an embossed or pressed material look.

### D. Retro / 8-Bit & 16-Bit UI (Pixel Art Style)

* **Borders:** Stepped, pixelated borders created using layered inset/outset `box-shadow` techniques (e.g., NES/GameBoy style NES.css patterns) or crisp pixel lines without `border-radius` smoothing (`border-radius: 0px`).

* **Typography:** Monospace pixel fonts (e.g., `'Press Start 2P'`, `'VT323'`, or system `monospace`).

* **Rendering:** `image-rendering: pixelated` for icons and visual elements to prevent anti-aliasing blur.

* **Palette:** Nostalgic 8-bit/16-bit arcade color palettes with high-contrast text and hard-edged button press animations.

## 4. Workflow Strategy for External Fetching

When processing UI component generation prompts:

1. **Identify Request Intent:** Determine component type (e.g., "Glassmorphic Card", "8-Bit Arcade Button", "Neobrutalist Input").

2. **Fetch / Construct Reference:**

   * Query or reference paths inside `uiverse-io/galaxy` (e.g., elements in `elements/buttons/`, `elements/cards/`).

   * Read raw source files via GitHub raw endpoints if network fetching tools are active.

3. **Framework Adaptation:**

   * Convert plain HTML/CSS into the target framework format (React JSX/TSX, Vue, Svelte, or Vanilla HTML).

   * Ensure standard accessibility (`aria-*` tags, keyboard focus states) are preserved during translation.

## 5. Quick Prompt Examples for Users

* *"Read DESIGN.md and create an 8-bit arcade start button using pixelated border styles."*

* *"Read DESIGN.md and create a glassmorphic login card using references from uiverse-io/galaxy."*

* *"Fetch a neobrutalist button style from the Uiverse repository and convert it to React + Tailwind."*


## 6. UI QUALITY EVALUATION SYSTEM

Every generated UI must undergo a quality evaluation before the task is considered complete.

The purpose of this evaluation is to reduce generic AI-generated design patterns and improve visual consistency, usability, responsiveness, accessibility, and code maintainability.

### A. Evaluation Principles

1. Evaluate the actual implementation, not just the design description.
2. Compare the generated UI against the user's requirements and the existing project's design system.
3. Do not assume that a visually attractive component is automatically usable.
4. Do not introduce unnecessary visual effects, decorations, gradients, or animations.
5. Preserve the selected design aesthetic throughout the interface.
6. Identify and fix issues before delivering the final result.
7. Never claim that a test passed unless it was actually performed.

### B. Quality Evaluation Criteria

Score the implementation using the following weighted criteria:

| Criterion | Weight |
|---|---:|
| Visual Consistency & Design Coherence | 25 |
| Visual Hierarchy & Typography | 20 |
| Usability & Interaction | 20 |
| Responsive Design | 15 |
| Accessibility | 10 |
| Code Quality & Maintainability | 10 |
| TOTAL | 100 |

#### 1. Visual Consistency & Design Coherence (25)

Evaluate:
- Consistency of colors, borders, shadows, and radii.
- Consistency with the selected design aesthetic.
- Consistency between related components.
- Appropriate use of visual effects.
- Avoidance of unnecessary decorative elements.

#### 2. Visual Hierarchy & Typography (20)

Evaluate:
- Clear distinction between headings, body text, and secondary information.
- Appropriate font sizes and font weights.
- Readable line lengths and line heights.
- Consistent spacing and alignment.
- Clear visual emphasis on important elements.

#### 3. Usability & Interaction (20)

Evaluate:
- Clear navigation and component affordances.
- Buttons and interactive elements behave as expected.
- Forms provide appropriate validation and feedback.
- Hover, active, focus, and disabled states are handled where applicable.
- No misleading or non-functional interactive elements.

#### 4. Responsive Design (15)

Evaluate:
- Layout adapts to mobile, tablet, and desktop.
- No unintended horizontal overflow.
- Text remains readable at smaller viewport sizes.
- Components do not overlap or become inaccessible.
- Navigation and controls remain usable on touch devices.

#### 5. Accessibility (10)

Evaluate:
- Semantic HTML elements are used appropriately.
- Interactive elements support keyboard navigation.
- Focus states are visible.
- Inputs have accessible labels.
- Images have appropriate alternative text.
- Text and background provide sufficient contrast.
- ARIA attributes are used only when necessary and correctly.

#### 6. Code Quality & Maintainability (10)

Evaluate:
- Components are structured logically.
- Avoid unnecessary code duplication.
- CSS selectors do not create unintended conflicts.
- Framework conventions are respected.
- Existing project architecture is preserved.
- No unnecessary dependencies are introduced.

### C. Evaluation Scoring

Each criterion receives a score proportional to its assigned weight.

Use the following quality thresholds:

- 90–100: Excellent. Ready for final review.
- 80–89: Good. Minor improvements may be needed.
- 70–79: Needs improvement. Revise identified weaknesses.
- Below 70: Poor. Rework the implementation before delivery.

A score of 80 or higher is the target, not an automatic guarantee of production readiness.

### D. Critical Quality Gates

Regardless of the total score, the following issues must be addressed before delivery:

1. Broken or non-functional primary interactions.
2. Unintended horizontal overflow that prevents normal usage.
3. Missing accessible names for essential interactive controls.
4. Unreadable text or severely insufficient contrast.
5. Major layout breakage at supported viewport sizes.
6. Implementation errors that prevent the UI from rendering correctly.

A high score must never compensate for a critical functional or accessibility failure.

### E. Evaluation Workflow

After generating the interface:

1. Review the implementation against the original user requirements.
2. Inspect the component structure, styles, and design consistency.
3. If browser preview or screenshot tools are available, inspect the rendered result.
4. Test representative mobile, tablet, and desktop viewport sizes.
5. Test interactive behavior when a runnable environment is available.
6. Check accessibility using available inspection tools.
7. Calculate the weighted quality score.
8. Identify the lowest-scoring criteria and revise the implementation.
9. Re-evaluate after making changes.
10. Report the final score and any remaining unverified aspects.

Do not fabricate browser tests, screenshots, accessibility results, or successful interactions when the required tools are unavailable.

### F. Final Evaluation Report

Include a concise report when completing a UI generation task:

**UI Quality Evaluation**

- Visual Consistency: XX/25
- Visual Hierarchy: XX/20
- Usability & Interaction: XX/20
- Responsive Design: XX/15
- Accessibility: XX/10
- Code Quality: XX/10

**Total Score:** XX/100

**Identified Issues:**
- List actual problems discovered during evaluation.

**Improvements Applied:**
- List changes made to address those problems.

**Remaining Limitations:**
- Mention aspects that could not be verified or tested.

The evaluation score represents a structured engineering assessment, not an objective guarantee of visual quality.
