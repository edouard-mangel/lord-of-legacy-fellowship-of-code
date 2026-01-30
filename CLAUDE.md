# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Slidev presentation titled "Le Seigneur du Legacy" - a technical talk that uses Lord of the Rings metaphors to explain software architecture concepts, technical debt, and legacy code management. The presentation is built using Slidev, a Vue-based presentation framework.

## Key Commands

### Development
```bash
pnpm install          # Install dependencies
pnpm dev              # Start dev server (opens at http://localhost:3030)
```

### Build & Export
```bash
pnpm build            # Build for production (outputs to dist/)
pnpm export           # Export slides to PDF or other formats
```

## Architecture

### Content Structure
- **slides.md** - Main presentation content in Markdown format with YAML frontmatter
  - Uses Slidev's extended Markdown syntax with special directives (`---` for slide separators)
  - Theme: `bricks` (from `@slidev/theme-bricks`)
  - Slides use special layouts (`intro`, `image-right`, `end`, etc.)
  - Supports Vue components and interactive elements via `<v-click>` and `<v-clicks>`

### Components
- **components/Counter.vue** - Interactive Vue component example
  - Can be used directly in slides.md
  - Uses Vue 3 Composition API with TypeScript
  - Styled with UnoCSS utility classes (inline)

### Snippets
- **snippets/external.ts** - External code snippets that can be imported into slides
  - Use `#region snippet` / `#endregion snippet` to define exportable code blocks
  - Can be referenced in slides for code examples

### Pages
- **pages/imported-slides.md** - Additional slide pages (optional organization pattern)

## Slidev-Specific Patterns

### Slide Layouts
Slides can use various layouts via frontmatter:
- `layout: intro` - Introduction slides
- `layout: image-right` - Split layout with image on right
- `layout: end` - Ending slides

### Interactive Elements
- `<v-click>` - Single click-triggered reveal
- `<v-clicks>` - Multiple click-triggered reveals for lists

### Theme Configuration
The presentation uses the `bricks` theme with customizations in the frontmatter:
- MDC syntax enabled for enhanced Markdown
- Slide transitions: `slide-left`
- Drawing persistence disabled
- Duration: 45min

## Deployment

The project is configured for deployment on both Netlify and Vercel:
- Build command: `npm run build`
- Output directory: `dist`
- Node version: 20 (Netlify)

Both platforms redirect all routes to `/index.html` for SPA routing.

## Development Notes

- All slides are written in `slides.md` using Markdown with YAML frontmatter
- The presentation content is in French and uses technical humor to explain complex concepts
- When editing slides, maintain the `---` separator pattern and preserve layout frontmatter
- Vue components can be embedded directly in Markdown slides
- The theme provides custom styling - avoid inline CSS unless necessary
