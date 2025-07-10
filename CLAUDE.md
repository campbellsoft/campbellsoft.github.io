# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Common Commands

- **Development**: `npm run dev` - Start development server
- **Build**: `npm run build` - Create production build  
- **Format**: `npm run format` - Format code with Prettier
- **Type Check**: `npm run check` - Run Astro type checking
- **Preview**: `npm run preview` - Preview production build locally

## Architecture Overview

This is an Astro-based static site generator for a SaaS/marketing website using the Campbell Software Corporation Light theme. The project follows Astro's content collection patterns with React components for interactive elements.

### Key Structure

- **Content Collections**: Defined in `src/content.config.ts` with Zod schemas for type safety
  - `blog/` - Blog posts with frontmatter (title, date, authors, categories, tags)
  - `homepage/` - Homepage sections (banner, features, services, workflow, CTA)
  - `pages/` - Static pages (404, privacy, terms, elements)
  - `contact/`, `pricing/`, `faq/` - Dedicated page collections with structured data

- **Components Architecture**:
  - `layouts/` - Main layout components (Base.astro, Default.astro, PostSingle.astro)
  - `layouts/components/` - Reusable UI components
  - `layouts/partials/` - Layout partials (Header, Footer, Post)
  - `layouts/shortcodes/` - MDX shortcodes (Button, Accordion, Notice, Tabs, Video)

- **Configuration**:
  - `src/config/config.json` - Site settings, metadata, navigation
  - `src/config/menu.json`, `social.json`, `theme.json` - Modular config files
  - Path aliases configured in `tsconfig.json` for clean imports (`@/components/*`, `@/shortcodes/*`)

### Styling & Framework

- **Tailwind CSS** with custom plugins in `src/tailwind-plugin/`
- **Sass** preprocessing for complex styles
- **TailwindCSS v4** with Vite integration

### Content Management

- Content written in Markdown/MDX with frontmatter
- Auto-import configured for shortcodes in `astro.config.mjs`
- Remark plugins for table of contents and collapsible sections
- Draft support across all content types

### Build Process

The site uses Astro's static site generation with React islands for interactive components. Content is type-checked against Zod schemas at build time.