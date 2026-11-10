# 🎨 AI UI Design System & Agent Rules (Uiverse Powered)

An open-source design system directive and ruleset designed to connect AI coding assistants (such as **OpenCode**, **Cursor**, **Claude Code**, and **GitHub Copilot**) directly to component patterns from external libraries—specifically the official [Uiverse Galaxy](https://github.com/uiverse-io/galaxy) repository.

By placing or referencing `DESIGN.md` in your project, your AI agents will automatically generate UI components adhering to distinct visual styles without rebuilding standard CSS primitives from scratch.

---

## 🚀 Supported Design Styles

This ruleset guides AI agents to write components in the following popular UI design aesthetics:

* 🟨 **Neobrutalism:** Bold solid borders, high-contrast colors, and hard offset shadows.
* 🧊 **Glassmorphism:** Frosted glass visual effects using translucency and backdrop blurs.
* 🧼 **Neumorphism (Soft UI):** Subtle dual inner/outer shadows creating extruded or debossed surfaces.
* 🧸 **Claymorphism:** 3D bubble-like elements with pastel colors and soft inner lighting.
* 👾 **Retro / 8-Bit & 16-Bit UI:** Pixelated borders, crisp zero-radius edges, monospace pixel fonts, and nostalgic arcade styling.
* 📐 **Modern Minimalist / Flat 2.0:** Subtle shadows, clean spacing, and modern responsive typography.

---

## 🛠️ How to Use

### Method 1: Local Copy (Recommended)
Copy the `DESIGN.md` file from this repository into the **root folder** of your web project.

1. Download or copy `DESIGN.md`.
2. Place it at `./DESIGN.md` in your project root.
3. Prompt your AI Agent:
   > *"Read DESIGN.md and create a glassmorphic login card component."*

### Method 2: Direct GitHub Raw URL Reference
If you don't want to copy the file manually, reference the raw URL directly in your AI agent prompts:

```text
Read the design rules from https://raw.githubusercontent.com/<YOUR-USERNAME>/<YOUR-REPO-NAME>/main/DESIGN.md and create an 8-bit arcade start button using React and Tailwind CSS.
```

### Method 3: System Prompt / Rules Integration
* **Cursor:** Add the contents of `DESIGN.md` or a link to it inside your `.cursorrules` file.
* **OpenCode:** Reference this repository URL or local path in your `.opencoderules` configuration.

---

## 🤝 Attribution & Credits

* **Uiverse.io:** Component references and design structures are inspired by and linked to the open-source community library at [uiverse-io/galaxy](https://github.com/uiverse-io/galaxy).
* All component designs retrieved via these rules remain under the original licensing of their respective Uiverse contributors.

---

## 📄 License

This repository and the `DESIGN.md` ruleset are licensed under the [MIT License](LICENSE). Feel free to use, modify, share, and contribute!
