---
name: og-image-create
description: Generate pixel-perfect, brand-accurate Open Graph (OG) / Social Card images by analyzing the codebase for design tokens and logos.
---

# og-image-create

Transform any AI agent with codebase access into a **world-class senior product designer + frontend engineer** specialized in Open Graph (OG) / Social Card images.

**Goal**: Perform a **complete, systematic, and deep analysis** of the entire frontend codebase **first**, locate the exact logo (or logomark/icon) being actively used, extract design tokens, then output a **self-contained, production-grade HTML/CSS template**.

## When to use

Use this skill when the user asks to generate, design, or create an Open Graph (OG) image, Twitter card, or social preview card for their application, or when they need to extract branding/design tokens to produce a social image template.

## Core Philosophy

- **Brand fidelity is absolute** — never invent or hallucinate logos, colors, or fonts.
- **Scannability first**.
- **Always analyze exhaustively before designing**.
- **Logo accuracy is mandatory** — the generated OG must use the **actual logo** (or icon) the application uses.

## Mandatory Step-by-Step Agent Workflow

### Phase 0: Exhaustive Codebase Discovery (Do this FIRST — before any design)

**Systematically explore the project. Spend significant effort on logo detection.**

#### 1. Static Asset Search

- Deep scan of `/public/` and all subfolders (`images/`, `assets/`, `logos/`, `icons/`, etc.).
- Common names: `logo*`, `logomark*`, `brand*`, `icon*`, `favicon*`.

#### 2. Code Usage Search (Most Important)

Search across the entire codebase for how the logo is **actually implemented**:

- **Look in layout files first**:
  - Next.js: `app/layout.tsx`, `app/(root)/layout.tsx`
  - Vite/React: `src/App.tsx`, `src/main.tsx`, `src/layouts/*`
  - Vue: `App.vue`, layout components

- **Search for logo-related code patterns**:
  - `<img src=`, `Image src=`, `:src=`, `src=`
  - Imports: `import logo from`, `import Logo from`, `import { Logo }`
  - Components: `<Logo`, `<Logomark`, `<BrandIcon`, `<AppLogo`
  - Next.js: `<Image src={logo}` or `src="/logo..."`
  - Any file containing `header`, `navbar`, `nav`, `footer`

- **Handle different scenarios**:
  - SVG imported as React component (`import { Logo } from './Logo'`)
  - Icon from library (Lucide, Heroicons, Tabler, Radix, etc.) — note which icon is used as brand mark
  - CSS background-image with logo
  - Inline SVG logo

- **Record**:
  - Exact file path of the logo component/asset
  - The real `src` value or import path
  - Light vs dark variants
  - Whether it's a full logo or logomark/icon

#### 3. Extract Design Tokens

- Colors, typography, shadows, radii, gradients from `tailwind.config.*`, CSS variables, theme files.

**Logo Discovery Rule**:

- Prioritize the logo that appears in the main header/navigation.
- If multiple options exist, prefer the primary/full logo (then logomark).
- If only an icon from a library is used, replicate its style or note it clearly.
- **Never proceed without attempting to find the real logo**. If truly not found, state it explicitly.

### Phase 1: Logo Referencing in HTML (Strict Rule)

**When a logo/asset is found:**

1. **Best**: Convert the actual logo file (SVG/PNG) to **base64** and embed it directly:

   ```html
   <img
     src="data:image/svg+xml;base64,BASE64_STRING_HERE"
     class="h-14 w-auto"
     alt="Company Logo"
   />
   ```

2. **Good alternative**: Use public URL with correct path:

   ```html
   <img
     src="https://yourdomain.com/logo-white.svg"
     class="h-14 w-auto"
     alt="Company Logo"
   />
   ```

3. **For icon-only brands**: Re-create the icon using inline SVG or Tailwind + proper styling to match the library icon used.

**Always document at the top of your response**:

> Logo used: `/public/logo-white.svg` (embedded as base64)
> Source found in: `app/components/Header.tsx`

**If no logo found**: Use clean, bold typography with the product name and clearly state:

> “No logo asset found after full search. Using text-based branding.”

### Phase 2: Content Strategy & Hierarchy

- Logo (real one) at top-left (preferred)
- Product name (if different)
- Strong headline (max 2 lines)
- Supporting subtitle (1 line)
- Visual hook + footer branding

### Phase 3: Dimensions & Technical Specs

- Primary: **1200 × 630 px**
- Twitter/X: **1200 × 675 px** or **1200 × 600 px**
- PNG target: <500 KB ideal

### Phase 4: Industry-Grade Design Principles

- Generous padding & safe zones
- High contrast
- Exact brand colors & fonts
- Premium but clean effects (glassmorphism, shadows, gradients only if on-brand)

### HTML Implementation Guidelines

- Tailwind via CDN + custom config matching the project
- CSS variables for colors
- Detailed comments in code
- Self-contained as much as possible

**Example Structure**:

```html
<div
  id="og"
  class="w-[1200px] h-[630px] relative overflow-hidden bg-gradient-to-br from-zinc-950 to-black flex items-center"
>
  <!-- Background Pattern -->
  <div class="absolute inset-0 opacity-10 ..."></div>

  <!-- Real Logo (base64 or public path) -->
  <img
    src="data:image/svg+xml;base64,..."
    class="absolute top-12 left-12 h-16 w-auto"
    alt="Company Logo"
  />

  <!-- Content -->
  <div class="max-w-[620px] pl-16">
    <h1
      class="text-[86px] leading-[0.95] font-bold tracking-tighter text-white"
    >
      Headline Goes Here
    </h1>
    <p class="mt-6 text-4xl text-white/90">Supporting benefit or tagline</p>
  </div>

  <!-- Visual / Mockup -->
  <div class="absolute right-12 bottom-12 w-[500px] ..."></div>

  <!-- Footer -->
  <div class="absolute bottom-10 left-12 text-white/70 text-xl font-medium">
    yourdomain.com
  </div>
</div>
```

## Agent Output Requirements

1. Full standalone `og-preview.html`
2. **Logo documentation** at the very top of response
3. Usage instructions (screenshot method)
4. Optimization advice
5. 2–3 variants when useful
6. OG meta tags

**Final Agent Mantra**:
**Search deeply for the real logo first. Use the actual asset (base64 preferred). Maintain perfect brand fidelity. Ensure thumbnail readability. Deliver emotional impact.**
