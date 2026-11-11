AI Agent UI Integration Rules & Design System
This file defines the mandatory protocols for fetching, selecting, and
adapting UI components directly from external
repositories---specifically the official Uiverse Galaxy library
(https://github.com/uiverse-io/galaxy)---into this project.
1. Primary Component Source
- Repository: https://github.com/uiverse-io/galaxy
- Raw Repository Base URL:
  https://raw.githubusercontent.com/uiverse-io/galaxy/main/
- Design Styles Supported: Neobrutalism, Glassmorphism, Liquid
  Glass & Dynamic Material UI, Neumorphism, Claymorphism, Retro /
  8-Bit & 16-Bit UI, Flat 2.0, Modern Minimalist.
2. Core Directives for AI Agents
Whenever the user prompts for a UI component (e.g., button, card, input,
loader, checkbox, form, navbar):
1. Do Not Reinvent the Wheel: Look up component structural patterns
   and styling techniques available in the uiverse-io/galaxy
   repository or apply equivalent Uiverse-style visual primitives.
2. Retrieve / Adapt Visual Styles: Extract the required HTML layout
   and CSS rules or transform raw CSS declarations into utility classes
   (Tailwind CSS) if requested by the project context.
3. Preserve Authentic Aesthetic: Maintain key properties such as
   backdrop-filter, box-shadow layering, border-radii,
   pixel-perfect borders, and accent color contrasts as defined by the
   target style.
3. Style Execution Guidelines
A. Neobrutalism
- Borders: Thick, solid borders (e.g., 2px or 4px
  solid #000000).
- Shadows: Hard, non-blurred offset shadows (e.g.,
  box-shadow: 4px 4px 0px #000000).
- Palette: Vibrant, high-contrast background colors paired with
  deep blacks.
- Typography: Bold sans-serif or monospace fonts.
B. Glassmorphism
- Background: Semi-transparent white or dark fills (e.g.,
  rgba(255, 255, 255, 0.15)).
- Blur: backdrop-filter: blur(10px) or higher.
- Borders: Subtle translucent borders (e.g.,
  1px solid rgba(255, 255, 255, 0.2)).
- Shadows: Soft, wide-spread drop shadows.
C. Liquid Glass & Dynamic Material UI
Liquid Glass and Dynamic Material UI are related but distinct concepts:
- Liquid Glass defines the visual material: contextual
  translucency, restrained backdrop blur, theme-aware tint, subtle
  specular highlights, edge definition, and layered depth.
- Dynamic Material UI defines how surfaces adapt to context and
  state: hover, focus, pressed, selected, scrolling, background
  complexity, theme, viewport, and reduced-motion preferences.
Treat Liquid Glass as a material treatment and Dynamic Material UI as
the behavior system around that material. Do not reduce either concept
to applying backdrop-filter: blur() to every component.
1. Core Design Principles
- Keep content and primary actions more prominent than decorative
  material effects.
- Use transparency only when it communicates useful depth or preserves
  a relationship with the background.
- Increase surface opacity or use a solid surface when the background
  is visually busy or text contrast is insufficient.
- Establish a small, consistent hierarchy of material levels: base
  surface, secondary surface, floating material, elevated material,
  and emphasized/selected material.
- Define predictable state changes; do not make surfaces change
  arbitrarily.
- Use blur, highlights, reflections, and motion sparingly. More
  effects do not automatically produce a better design.
- Preserve the interface's hierarchy and usability when blur, shadows,
  or animation are disabled.
2. Material Anatomy
A Liquid Glass surface may use the following layers. Not every component
needs every layer.
  Layer                   Purpose                 Implementation guidance
  Base fill               Establishes tint and    Use a restrained
opacity                 theme-aware color with
sufficient opacity

  Backdrop sampling       Connects the surface to Use backdrop-filter
content behind it       where supported and
provide a fallback

  Color tint              Gives the material      Use subtle, consistent
identity                theme-aware tint

  Specular highlight      Suggests reflected      Use a faint gradient or
light or curvature      inset highlight

  Edge definition         Separates the surface   Use a low-contrast
from its surroundings   border or inner
highlight

  Elevation               Communicates overlap    Use restrained shadows
and stacking            with consistent depth
levels

  Shape                   Defines the surface     Follow the project's
silhouette              radius scale
Motion                  Communicates            Animate only meaningful
interaction or state    transitions
Decorative layers must not intercept pointer events or cover functional
content. Use a deliberate stacking order and avoid unnecessary stacking
contexts that break menus, tooltips, or dialogs.
3. Component Application
- Navigation and toolbars: Good candidates for translucent
  materials. Keep labels readable, provide a clear active state, and
  increase opacity over busy content.
- Cards and panels: Use glass selectively for compact summaries,
  media controls, and floating utility panels. Prefer solid or nearly
  solid surfaces for long text, dense tables, forms, and code editors.
- Dialogs, popovers, and menus: Use stronger opacity and clear
  separation. Preserve keyboard focus behavior and prevent clipping.
- Buttons and controls: Provide distinct default, hover,
  focus-visible, pressed, selected, and disabled states. Do not rely
  on color or glow alone.
- Data-dense interfaces: Keep charts, tables, filters, and form
  fields on stable, readable surfaces. Limit glass to navigation and a
  small number of floating controls.
4. Dynamic Material Behavior
Use explicit, understandable states and context variants.
  State or context                    Recommended response
  Default                             Balanced tint, blur, and edge
definition

  Hover                               Slightly stronger tint or highlight

  Focus-visible                       High-contrast focus indicator

  Pressed                             Subtle compression or reduced
elevation

  Selected                            Persistent tint, marker, or
stronger edge

  Scrolled                            Optional opacity or density
adjustment

  Busy background                     Increase opacity or use a solid
fallback

  Dark theme                          Use theme-specific fill, border,
and shadow

  Reduced motion                      Remove nonessential movement
Unsupported backdrop filter         Use a readable solid or translucent
fallback
For scroll-responsive headers, use a deliberate threshold or a small
number of stable states. Avoid layout shifts and avoid updating
framework state on every scroll event when CSS or an existing scroll
abstraction is sufficient.

Prefer explicit variants such as default, over-image,
dense-content, navigation, light, and dark over fragile attempts
to infer arbitrary background colors.
5. Implementation and Performance
- Define shared tokens for surface opacity, blur levels, tint, radius,
  border, elevation, focus ring, and transition timing.
- Use reusable material variants rather than hardcoding different
  effects into every component.
- Provide a more opaque fallback when backdrop-filter is
  unavailable.
- Use @supports where appropriate to progressively enhance the
  material.
- Limit the number of simultaneously visible blurred surfaces.
- Avoid continuously animating backdrop-filter, large shadows, or
  full-screen blur.
- Prefer small opacity or transform transitions when appropriate.
- Test on lower-powered devices and realistic viewport sizes.
- Do not add dependencies when CSS and the project's existing
  architecture are sufficient.
Example starting point (adapt values to the actual background and
theme):
.glass-surface {
  color: var(--text-primary, #172033);
  background: rgb(255 255 255 / 92%);
  border: 1px solid rgb(255 255 255 / 70%);
  border-radius: var(--material-radius-md, 1rem);
  box-shadow: var(--material-shadow);
}

@supports ((backdrop-filter: blur(1px)) or
           (-webkit-backdrop-filter: blur(1px))) {
  .glass-surface {
    background: rgb(255 255 255 / 68%);
    -webkit-backdrop-filter: blur(16px) saturate(140%);
    backdrop-filter: blur(16px) saturate(140%);
  }
}

@media (prefers-reduced-motion: reduce) {
  .glass-control {
    transition: none;
  }
}
If using pseudo-elements for highlights or borders, establish a
positioning context and ensure decorative layers remain behind content
and use pointer-events: none.
6. Accessibility and Responsive Requirements
- Check contrast against the actual rendered material, not only the
  declared background color.
- Use more opaque surfaces behind small text and essential controls.
- Preserve semantic HTML, accessible names, logical keyboard order,
  and visible focus indicators.
- Respect prefers-reduced-motion.
- Do not encode selected, error, or status states using color alone.
- Keep floating controls away from screen edges and device safe areas.
- Ensure menus and dialogs fit within the viewport and do not cover
  essential content.
- Test mobile and desktop layouts, including relevant orientations.
- Where relevant, test forced-colors or high-contrast modes.
7. Anti-Patterns
Avoid: 1. Applying blur to every card, button, and section. 2. Using
low-opacity surfaces over complex backgrounds when text becomes
unreadable. 3. Repeating identical glass cards without a meaningful
hierarchy. 4. Excessive glow, bright borders, reflections, or floating
animation. 5. Stacking many translucent layers until colors become
muddy. 6. Using large shadows on every component. 7. Inconsistent
opacity, blur, radius, and elevation for similar components. 8. Omitting
a fallback for unsupported backdrop filtering. 9. Using effects to hide
weak spacing, typography, alignment, or information hierarchy.
8. Required Agent Workflow
When a user requests Liquid Glass or Dynamic Material UI:
1. Identify the interface type, primary tasks, content density,
   framework, and target devices.
2. Select only the components that benefit from translucency; keep
   reading-heavy and data-heavy areas stable.
3. Define shared material tokens and a clear surface hierarchy before
   styling individual components.
4. Implement explicit context and interaction variants.
5. Add only meaningful state changes for focus, selection, scrolling,
   or context.
6. Provide solid fallbacks and reduced-motion behavior.
7. Check contrast, semantics, keyboard access, responsive behavior, and
   performance.
8. Inspect the rendered result and test real interactions when tools
   are available.
9. Refine issues before delivery and report anything that could not be
   verified.
Do not claim that a web implementation is an official Apple
implementation or uses Apple's proprietary platform APIs unless that is
actually true. Treat Liquid Glass as a visual and interaction direction
in web projects. Do not copy a platform interface pixel-for-pixel when
the user asks for an original design. Never claim that browser support,
contrast, responsiveness, or performance was tested unless the checks
were actually performed.
9. Liquid Glass Quality Checklist
Evaluate: - Material levels are distinct and consistently applied. -
Transparency reveals useful context without reducing readability. -
Primary content and actions remain more prominent than decoration. -
Dynamic changes correspond to understandable states. - Opacity, blur,
tint, radius, edge, and elevation use shared tokens. - Focus, keyboard
use, semantics, contrast, and reduced motion are addressed. - Floating
controls and overlays work across target viewports. - Blur and animation
are limited and purposeful. - The interface remains usable without
backdrop filtering. - Material variants are reusable and maintainable.

A strong implementation should remain coherent when blur, shadows, and
animation are removed. If the hierarchy collapses without those effects,
improve the underlying layout and design.
D. Neumorphism (Soft UI)
- Background: Flat element color matching the parent canvas
  background identically.
- Shadows: Dual-contrast box shadows (drop-shadow +
  inner-shadow) creating an embossed or pressed material look.
E. Retro / 8-Bit & 16-Bit UI (Pixel Art Style)
- Borders: Stepped, pixelated borders created using layered
  inset/outset box-shadow techniques (e.g., NES/GameBoy style
  NES.css patterns) or crisp pixel lines without border-radius
  smoothing (border-radius: 0px).
- Typography: Monospace pixel fonts (e.g., 'Press Start 2P',
  'VT323', or system monospace).
- Rendering: image-rendering: pixelated for icons and visual
  elements to prevent anti-aliasing blur.
- Palette: Nostalgic 8-bit/16-bit arcade color palettes with
  high-contrast text and hard-edged button press animations.
4. Workflow Strategy for External Fetching
When processing UI component generation prompts:
1. Identify Request Intent: Determine component type (e.g.,
   "Glassmorphic Card", "8-Bit Arcade Button", "Neobrutalist Input").
2. Fetch / Construct Reference:
   - Query or reference paths inside uiverse-io/galaxy (e.g.,
     elements in elements/buttons/, elements/cards/).
   - Read raw source files via GitHub raw endpoints if network
     fetching tools are active.
3. Framework Adaptation:
   - Convert plain HTML/CSS into the target framework format (React
     JSX/TSX, Vue, Svelte, or Vanilla HTML).
   - Ensure standard accessibility (aria-* tags, keyboard focus
     states) are preserved during translation.
5. Quick Prompt Examples for Users
- "Read uiverse_ui_agent.md and create an 8-bit arcade start button
  using pixelated border styles."
- "Read uiverse_ui_agent.md and create a glassmorphic login card
  using references from uiverse-io/galaxy."
- "Fetch a neobrutalist button style from the Uiverse repository and
  convert it to React + Tailwind."
6. UI QUALITY EVALUATION SYSTEM
Every generated UI must undergo a quality evaluation before the task is
considered complete.

The purpose of this evaluation is to reduce generic AI-generated design
patterns and improve visual consistency, usability, responsiveness,
accessibility, and code maintainability.
A. Evaluation Principles
1. Evaluate the actual implementation, not just the design description.
2. Compare the generated UI against the user's requirements and the
   existing project's design system.
3. Do not assume that a visually attractive component is automatically
   usable.
4. Do not introduce unnecessary visual effects, decorations, gradients,
   or animations.
5. Preserve the selected design aesthetic throughout the interface.
6. Identify and fix issues before delivering the final result.
7. Never claim that a test passed unless it was actually performed.
B. Quality Evaluation Criteria
Score the implementation using the following weighted criteria:

  Criterion                                 Weight
  Visual Consistency & Design Coherence         25
Visual Hierarchy & Typography                 20
Usability & Interaction                       20
Responsive Design                             15
Accessibility                                 10
Code Quality & Maintainability                10
TOTAL                                        100
1. Visual Consistency & Design Coherence (25)
Evaluate: - Consistency of colors, borders, shadows, and radii. -
Consistency with the selected design aesthetic. - Consistency between
related components. - Appropriate use of visual effects. - Avoidance of
unnecessary decorative elements.
2. Visual Hierarchy & Typography (20)
Evaluate: - Clear distinction between headings, body text, and secondary
information. - Appropriate font sizes and font weights. - Readable line
lengths and line heights. - Consistent spacing and alignment. - Clear
visual emphasis on important elements.
3. Usability & Interaction (20)
Evaluate: - Clear navigation and component affordances. - Buttons and
interactive elements behave as expected. - Forms provide appropriate
validation and feedback. - Hover, active, focus, and disabled states are
handled where applicable. - No misleading or non-functional interactive
elements.
4. Responsive Design (15)
Evaluate: - Layout adapts to mobile, tablet, and desktop. - No
unintended horizontal overflow. - Text remains readable at smaller
viewport sizes. - Components do not overlap or become inaccessible. -
Navigation and controls remain usable on touch devices.
5. Accessibility (10)
Evaluate: - Semantic HTML elements are used appropriately. - Interactive
elements support keyboard navigation. - Focus states are visible. -
Inputs have accessible labels. - Images have appropriate alternative
text. - Text and background provide sufficient contrast. - ARIA
attributes are used only when necessary and correctly.
6. Code Quality & Maintainability (10)
Evaluate: - Components are structured logically. - Avoid unnecessary
code duplication. - CSS selectors do not create unintended conflicts. -
Framework conventions are respected. - Existing project architecture is
preserved. - No unnecessary dependencies are introduced.
C. Evaluation Scoring
Each criterion receives a score proportional to its assigned weight.

Use the following quality thresholds:
- 90--100: Excellent. Ready for final review.
- 80--89: Good. Minor improvements may be needed.
- 70--79: Needs improvement. Revise identified weaknesses.
- Below 70: Poor. Rework the implementation before delivery.
A score of 80 or higher is the target, not an automatic guarantee of
production readiness.
D. Critical Quality Gates
Regardless of the total score, the following issues must be addressed
before delivery:
1. Broken or non-functional primary interactions.
2. Unintended horizontal overflow that prevents normal usage.
3. Missing accessible names for essential interactive controls.
4. Unreadable text or severely insufficient contrast.
5. Major layout breakage at supported viewport sizes.
6. Implementation errors that prevent the UI from rendering correctly.
A high score must never compensate for a critical functional or
accessibility failure.
E. Evaluation Workflow
After generating the interface:
1. Review the implementation against the original user requirements.
2. Inspect the component structure, styles, and design consistency.
3. If browser preview or screenshot tools are available, inspect the
   rendered result.
4. Test representative mobile, tablet, and desktop viewport sizes.
5. Test interactive behavior when a runnable environment is available.
6. Check accessibility using available inspection tools.
7. Calculate the weighted quality score.
8. Identify the lowest-scoring criteria and revise the implementation.
9. Re-evaluate after making changes.
10. Report the final score and any remaining unverified aspects.
Do not fabricate browser tests, screenshots, accessibility results, or
successful interactions when the required tools are unavailable.
F. Final Evaluation Report
Include a concise report when completing a UI generation task:

UI Quality Evaluation
- Visual Consistency: XX/25
- Visual Hierarchy: XX/20
- Usability & Interaction: XX/20
- Responsive Design: XX/15
- Accessibility: XX/10
- Code Quality: XX/10
Total Score: XX/100

Identified Issues: - List actual problems discovered during
evaluation.

Improvements Applied: - List changes made to address those problems.

Remaining Limitations: - Mention aspects that could not be verified
or tested.

The evaluation score represents a structured engineering assessment, not
an objective guarantee of visual quality.
