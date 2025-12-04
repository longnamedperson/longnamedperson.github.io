# Repository Guidelines

## Project Structure
- Home grid and data live in `src/pages/index.astro`; individual project pages (`canopee.astro`, `kinetra.astro`, `ferska.astro`, `resonance.astro`, `thoka.astro`, `photography.astro`) share the same global styles.
- Reusable UI components are in `src/components` (logo tile, loading overlay, project tile). Add new shared pieces here.
- Design tokens, typography, and the palette live in `src/styles/global.css`; extend variables instead of hardcoding values.
- Static assets belong in `public/images/...` and are referenced as `/images/<file>`.
- Project tiles come from the `projects` array in `index.astro` with fields `image`, `alt`, `title`, `year`, `location`, `description`, `link`; keep upcoming items’ year/location empty and omit meta for photography.

## Development Workflow
- Install dependencies: `npm install` (locked by `package-lock.json`).
- Start dev server: `npm run dev` (`http://localhost:4321`).
- Production build: `npm run build` → `dist/`.
- Preview the built site locally: `npm run preview`.
- Optional validation: `npm run astro check` before committing to catch template/type issues.

## Styling & Naming
- Palette is limited to `#f7f7f7` (background), `#1f1f1f` (text), `#d22128` (accent); do not introduce extra tints.
- Typography uses All Round Gothic for headings and body; keep letter spacing/weights from `global.css`.
- Use 4-space indentation for `.astro` and `.css`; keep filenames lowercase with underscores for multiword components (e.g., `project_tile.astro`).
- Prefer CSS for layout/animation; keep inline scripts minimal and scoped to the component.
- Links inherit text colour with accent hover; avoid default underlines unless intentionally added.

## Interaction & QA
- Theme toggle should fade logo text, animate the logo-tile background between light/dark, and update the icon with no border.
- Loader must show only on first visit per sessionStorage flag and then dismiss cleanly so the site is usable.
- Project detail panel opens from any tile; Escape, backdrop, and the close button should dismiss it. Photography tiles should not show year/location.
- Confirm the desktop 3×3 grid stays full-height and the mobile vertical list remains readable; images should cover tiles without distortion.
- Ensure project title links keep the same styling as non-linked titles and maintain sufficient contrast in both themes.

## Commits & PRs
- Write imperative, scoped commit messages (e.g., `Refine theme toggle timing`).
- PRs should include a short summary, screenshots/GIFs for visual changes, and manual QA notes (browsers, modes, mobile/desktop).
- Call out new assets (`public/images/...`) or config changes (`astro.config.mjs`, `tsconfig.json`) in descriptions.
