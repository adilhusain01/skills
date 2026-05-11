<div align="center">
  <h1>AI Skill: OG Image Creator</h1>
  <p><strong>Transform your AI agent into a world-class product designer & frontend engineer.</strong></p>
</div>

---

## Overview

**OG Image Creator** is an advanced skill template for AI coding agents (like GitHub Copilot, Cursor, etc.). It equips your AI with a strict, specialized workflow to automatically generate **pixel-perfect, brand-accurate Open Graph (OG) / Social Card images** based exactly on your project's codebase.

Instead of generic, hallucinated designs, this skill forces the AI to systematically explore your codebase, extract your real design tokens (Tailwind configs, CSS variables), locate your actual logo, and build a production-grade, self-contained HTML/CSS template.

## Core Features

* **Exhaustive Codebase Discovery**: Deep-scans your frontend code to find exactly how logos are imported and used (`/public` assets, inline SVGs, layout files, etc.).
* **Absolute Brand Fidelity**: Never hallucinates colors or fonts. It extracts exact design tokens from your Tailwind config or global CSS.
* **Production-Grade Templates**: Outputs standalone HTML/CSS files using Tailwind via CDN, ready to be immediately converted to an image.
* **Perfect Dimensions**: Automatically targets optimal sizes (e.g., 1200×630 for primary OG, 1200×675 for Twitter).

## How It Works

Once installed, simply ask your agent:
> *"Create an OG image for my application."*

The AI will then execute a mandatory 5-phase workflow:
1. **Phase 0:** Exhaustive codebase discovery (finding logos and tokens).
2. **Phase 1:** Strict logo referencing (embedding the true logo via base64 or public URL).
3. **Phase 2:** Content strategy & architectural hierarchy.
4. **Phase 3 & 4:** Sizing, spacing, and application of premium design principles.

## Installation & Usage

Install this skill directly from this repository using `skills.sh`:

```bash
npx skills add adilhusain01/og-image
```

Once added, the agent will automatically reference the rules in your workspace whenever you ask for an OG image!

---
<div align="center">
  <i>Empower your AI to design with <b>context</b> and <b>fidelity</b>.</i>
</div>
