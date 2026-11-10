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