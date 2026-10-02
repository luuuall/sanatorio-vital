# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Static landing page for Sanatorio Papa Francisco, a medical clinic, built with Astro 5. No JS framework, no integrations, no backend, no tests or linter. All site copy is in Argentine Spanish (voseo); keep that tone when writing or editing content.

## Commands

- `npm run dev`: dev server at `localhost:4321`
- `npm run build`: static build to `dist/`
- `npm run preview`: preview the build locally

## Architecture

- **Content lives in `src/data/site.ts`**, not in page markup. It exports `site` (contact info, address, social links), `horarios`, `stats`, `servicios`, `porQueElegirnos`, `especialidades`, `especialistas`, and `testimonios`. Pages import and render these arrays, so content changes (services, staff, phone numbers, testimonials) almost always mean editing this one file.
- **`src/layouts/Layout.astro`** wraps every page (Header, `<main><slot/></main>`, Footer) and holds the global stylesheet: CSS custom properties (teal `--brand-*` palette, `--accent`, `--ink`, radii, shadows) plus shared utility classes (`.container`, `.section`, `.section-head`/`.eyebrow`/`.section-title`, `.btn` variants, `.grid-2/3/4`). All other styles are Astro-scoped `<style>` blocks inside each component or page; use the tokens and utilities from Layout rather than hardcoding colors or spacing.
- **`src/components/Icon.astro`** is the inline SVG icon system: a `paths` map keyed by name, rendered as a single stroked `<path>`. Icon names referenced in `site.ts` data (e.g. `servicios[].icon`) must exist in that map; unknown names silently fall back to the `plus` icon. New icons are added as 24x24 stroke paths in the map.
- **Pages** (`index`, `servicios`, `equipo`, `contacto`, `gracias`, `404`) follow the same pattern: import Layout, Icon, and data from `site.ts`, then markup with scoped styles. The contact form in `contacto.astro` has no backend; it submits via GET to `/gracias`, a static confirmation page (the query params are not read).
- `astro.config.mjs` only sets `site: 'https://sanatoriovital.com.ar'`.
