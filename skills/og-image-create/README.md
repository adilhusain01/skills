# AI Skill: OG Image Creator

Transform your AI agent into a world-class product designer & frontend engineer.

**OG Image Creator** is an advanced skill template for AI coding agents. It equips your AI with a strict, specialized workflow to automatically generate **pixel-perfect, brand-accurate Open Graph (OG) / Social Card images** based exactly on your project's codebase.

Instead of generic designs, this skill forces the AI to systematically explore your codebase, extract your real design tokens (Tailwind configs, CSS variables), locate your actual logo, and build a production-grade HTML/CSS template.

## Core Features

* **Exhaustive Codebase Discovery**: Deep-scans your frontend code to find exactly how logos are imported and used (`/public` assets, inline SVGs, layout files, etc.).
* **Absolute Brand Fidelity**: Never hallucinates colors or fonts. It extracts exact design tokens from your Tailwind config or global CSS.
* **Production-Grade Templates**: Outputs standalone HTML/CSS files using Tailwind via CDN.
* **Perfect Dimensions**: Automatically targets optimal sizes.

## Installation

Install this specific skill using `skills.sh`:

```bash
npx skills add adilhusain01/skill --skill og-image-create
```

## How to Use

Once installed, simply ask your agent:
> *"Create an OG image for my application."*

The AI will automatically handle codebase discovery, logo extraction, and the final design layout.
