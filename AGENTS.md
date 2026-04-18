# Agents Guide

Astro 6 minimal starter (TypeScript strict). See [README.md](README.md) for full project overview.

## Commands

| Command           | Purpose                                      |
| ----------------- | -------------------------------------------- |
| `npm run dev`     | Dev server at `http://localhost:4321`        |
| `npm run build`   | Build to `./dist/`                           |
| `npm run preview` | Preview production build                     |
| `npx astro check` | Type-check `.astro` files                    |

## Project Structure

```
src/pages/       # File-based routing — each .astro or .md file = a route
src/components/  # Reusable Astro/UI-framework components (create as needed)
src/layouts/     # Layout components (create as needed)
public/          # Static assets served at root URL
```

## Key Conventions

- **Pages**: `.astro` files in `src/pages/` are auto-routed by filename.
- **Components**: Place in `src/components/`; no directory exists yet — create it when adding the first component.
- **Styles**: Scoped styles go in `<style>` blocks inside `.astro` files. Global styles belong in a file imported in a layout.
- **TypeScript**: Strict mode enabled via `astro/tsconfigs/strict`. Avoid `any`; prefer Astro's built-in types.
- **Static assets**: Put images and other static files in `public/`; reference them with a root-relative path (e.g., `/favicon.svg`).

## Adding Integrations

Use the Astro CLI to add official integrations (React, Tailwind, etc.):

```sh
npx astro add <integration>
```

This automatically updates `astro.config.mjs` and installs required packages.
