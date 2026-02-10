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
  - Theme: `seriph`
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

### Code Block Animations

#### Line Highlighting with Clicks
Highlight specific lines on successive clicks by adding `{lineRanges}` after the language identifier:
```markdown
```ts {*|1|2-5|all}
// click 1: show all, click 2: highlight line 1, click 3: highlight lines 2-5
```
```
- `*` = show all lines (no highlight)
- `1|3-5` = highlight line 1 first, then lines 3-5 on next click
- `{at:N}` = synchronize with a specific click number (useful for parallel code blocks)
- `{lines: true}` = show line numbers

#### Synchronized Code Blocks
Use `{at:N}` with the same value on multiple code blocks to animate them in sync:
```markdown
```js {1|2}{at:1}
input code
```
```js {1|2}{at:1}
output code
```
```

#### Shiki Magic Move (Code Transformations)
Animate between different code states with smooth transitions — ideal for showing refactoring steps:
````markdown
````md magic-move {lines: true}
```ts
// Step 1: before refactoring
```
```ts
// Step 2: after refactoring
```
````
````
- Wrap multiple code blocks inside `````md magic-move`
- Each inner code block is one animation step
- Non-code text between blocks is ignored (can be used for comments)
- Options: `{at:N, lines: true}` for click synchronization and line numbers
- Can combine with line highlighting: `{*|1|2-5}` inside magic-move steps

### Theme Configuration
The presentation uses the `seriph` theme with customizations in the frontmatter:
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
