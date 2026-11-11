# Uiverse Agent Config

**Build distinctive, consistent, and functional interfaces with AI
coding assistants using Uiverse component references.**

Uiverse Agent Config is an open-source UI design directive that guides
AI coding assistants to discover, select, adapt, and implement UI
component patterns from the official [Uiverse Galaxy
repository](https://github.com/uiverse-io/galaxy).

Instead of generating generic interfaces from scratch, the agent uses
existing component references as design inspiration and adapts them to
the project's framework, design requirements, and visual identity.

The goal is not simply to generate attractive UI, but to produce
interfaces that are visually coherent, usable, responsive, and
maintainable.

## Features

-   **Uiverse Integration** --- Uses Uiverse Galaxy as a reference
    source for UI component patterns.
-   **Distinctive Visual Styles** --- Supports multiple design
    aesthetics instead of relying on generic AI-generated layouts.
-   **Framework Adaptation** --- Adapts HTML/CSS component references to
    React, Vue, Svelte, or Vanilla HTML.
-   **Design Consistency** --- Encourages consistent colors, typography,
    spacing, borders, and component behavior.
-   **UI Quality Evaluation** --- Evaluates visual hierarchy, usability,
    responsiveness, accessibility, and implementation quality.
-   **Accessibility Awareness** --- Encourages semantic HTML, keyboard
    navigation, focus states, and appropriate ARIA attributes.

## Supported Design Styles

  -----------------------------------------------------------------------
  Style                               Design Characteristics
  ----------------------------------- -----------------------------------
  Neobrutalism                        Bold borders, high contrast, hard
                                      offset shadows

  Glassmorphism                       Translucent surfaces, backdrop
                                      blur, subtle borders

  Neumorphism                         Soft shadows and embossed surfaces

  Claymorphism                        Rounded shapes, soft lighting,
                                      dimensional appearance

  Retro / 8-bit / 16-bit              Pixel-inspired borders, nostalgic
                                      palettes, pixel typography

  Modern Minimalist                   Clean layouts, restrained colors,
                                      clear spacing

  Flat 2.0                            Simple surfaces with subtle depth
                                      and hierarchy
  -----------------------------------------------------------------------

The selected aesthetic should match the project's purpose. Avoid
combining unrelated styles without a clear design rationale.

### Liquid Glass & Dynamic Material UI

Uiverse Agent Config also supports **Liquid Glass & Dynamic Material
UI** as an integrated design direction. It extends basic glassmorphism
with a more deliberate material hierarchy and context-aware behavior.

-   **Liquid Glass** focuses on the surface appearance: controlled
    translucency, backdrop blur, theme-aware tint, subtle highlights,
    edge definition, and layered depth.
-   **Dynamic Material UI** focuses on how surfaces respond to interface
    state and context, such as hover, focus, selection, scrolling, dark
    mode, busy backgrounds, and reduced-motion preferences.

The style is intended for navigation bars, floating toolbars, compact
utility panels, contextual controls, and selected dashboard elements.
Dense tables, long-form text, forms, and other reading-heavy areas
should generally use solid or more opaque surfaces to preserve
readability.

Unlike generic glassmorphism, this approach does not apply blur to every
component. It uses a small, consistent set of material levels and
increases opacity or switches to a solid fallback when transparency
harms contrast. It also considers performance, keyboard focus,
responsive layouts, and `prefers-reduced-motion`.

Example prompt:

``` text
Create a responsive dashboard using Liquid Glass and Dynamic Material UI.
Use contextual translucent materials for the navigation and compact floating
controls, while keeping charts and data tables on stable readable surfaces.
Add clear hover, focus, selected, and scrolled states, provide a solid fallback,
and evaluate accessibility and responsive behavior.
```

The detailed implementation rules, CSS guidance, accessibility
requirements, anti-patterns, and evaluation checklist are integrated
into `uiverse_ui_agent.md`.

## How It Works

The agent follows a structured workflow:

1.  **Understand the Request** --- Identify the component type, intended
    purpose, framework, and visual requirements.
2.  **Find References** --- Search Uiverse Galaxy for relevant component
    patterns.
3.  **Evaluate References** --- Select references based on relevance,
    visual quality, and compatibility.
4.  **Adapt Components** --- Convert the reference into the target
    framework while preserving its essential visual characteristics.
5.  **Maintain Consistency** --- Follow the existing project's design
    tokens and component conventions.
6.  **Evaluate UI Quality** --- Review the generated interface for
    visual coherence, usability, responsiveness, accessibility, and
    implementation quality.
7.  **Refine the Result** --- Fix identified issues before considering
    the task complete.

If Uiverse cannot be accessed, the agent should report the limitation
and use an appropriate fallback rather than claiming that a component
was successfully retrieved.

## Installation

### Method 1: Local Project Instructions

1.  Clone this repository:

    ``` bash
    git clone https://github.com/Fortunetry/uiverse-agent-config.git
    ```

2.  Copy `uiverse_ui_agent.md` into your web project's root directory.

3.  Ask your AI coding assistant to read the instruction file before
    generating UI.

    Example:

    ``` text
    Read uiverse_ui_agent.md and follow its rules.

    Create a Liquid Glass login interface using React and Tailwind CSS.\nUse contextual translucency, clear focus states, and a solid fallback.
    Use relevant Uiverse references and evaluate the final UI quality.
    ```

### Method 2: Direct GitHub Reference

You can reference the raw instruction file directly:

``` text
Read and follow:
https://raw.githubusercontent.com/Fortunetry/uiverse-agent-config/main/uiverse_ui_agent.md

Create a responsive neobrutalist dashboard using React.
Find relevant Uiverse references, adapt them to the project,
and evaluate the resulting interface.
```

This method requires the AI agent to have access to external URLs.

### Method 3: Agent Rules Integration

You can integrate the contents of `uiverse_ui_agent.md` into your coding
assistant's project-level instruction system.

For example: - Cursor: Project Rules. - Claude Code: `CLAUDE.md` or
project instructions. - OpenCode: `AGENTS.md` or configured
instructions. - GitHub Copilot: Repository custom instructions.

Follow each tool's current configuration format. Do not assume that
every agent automatically reads `uiverse_ui_agent.md`.

## Example Prompts

**Glassmorphism Login**

``` text
Create a modern glassmorphic login form.
Find a suitable Uiverse reference, adapt it to React,
and ensure the form is responsive and accessible.
```

**Liquid Glass & Dynamic Material Dashboard**

``` text
Create a responsive dashboard using Liquid Glass and Dynamic Material UI.
Use translucent materials for navigation and compact floating controls,
but keep charts, tables, and forms readable on stable surfaces.
Add clear interaction states and evaluate accessibility and performance.
```

**Neobrutalist Dashboard**

``` text
Build a neobrutalist dashboard with a sidebar,
statistics cards, and a transaction table.
Maintain a consistent visual language across components.
```

**Retro Game Interface**

``` text
Create a retro 8-bit game menu with start,
settings, and exit buttons.
Use pixel-inspired visual elements and typography.
```

## UI Quality Evaluation

Generated interfaces should be evaluated before completion.

The evaluation should consider:

-   Visual consistency and design coherence.
-   Typography and visual hierarchy.
-   Usability and interaction behavior.
-   Responsive behavior across screen sizes.
-   Accessibility and keyboard navigation.
-   Code quality and maintainability.

The agent should identify problems, revise the implementation, and
report any remaining limitations.

See `uiverse_ui_agent.md` for the complete evaluation system and the
integrated Liquid Glass & Dynamic Material UI implementation guidance.

## Component Sources and Attribution

This project uses [Uiverse Galaxy](https://github.com/uiverse-io/galaxy)
as an external reference source.

Uiverse component implementations retain their respective original
licensing terms. When redistributing substantial portions of component
code, preserve the applicable copyright notices and license text.

This project is independently maintained and is not an official Uiverse
product.

## Limitations

-   External component retrieval depends on network access and available
    tools.
-   Not every Uiverse component is compatible with every framework.
-   AI-generated interfaces still require human review and testing.
-   Visual quality evaluation is a guided assessment, not a guarantee of
    perfect design.

## License

This repository is distributed under the MIT License.

See [LICENSE](LICENSE) for details.

## Contributing

Contributions, suggestions, and improvements are welcome.

You can contribute by: - Improving component selection and adaptation
rules. - Adding design quality evaluation criteria. - Improving
framework compatibility. - Reporting incorrect component references. -
Suggesting improvements to the design workflow.

------------------------------------------------------------------------

**Developed by Fortunetry**

GitHub: https://github.com/Fortunetry/uiverse-agent-config
