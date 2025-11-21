# Repository Guidelines

## Project Structure & Module Organization
- `src/` holds React code; `App.jsx` wires random verse display and routes to `components/GameScreen.jsx` (quiz). Styles live in `App.css` and `index.css`.
- Data lives in `public/`: `letras/` (verse JSONs with `index.json`), album covers `1.jpg-28.jpg`, and `temas.json` for theme tokens. Additional album metadata sits in `src/assets/albums.json`.
- Public assets are loaded by URL (no import), so keep filenames stable to avoid broken fetches.

## Build, Test, and Development Commands
- `npm install` — install dependencies.
- `npm run dev` — start Vite dev server (default http://localhost:5173) with hot reload.
- `npm run build` — production bundle with Vite.
- `npm run preview` — serve the production build locally to sanity-check assets and routes.
- `npm run lint` — ESLint (React + hooks + refresh) for code quality.

## Coding Style & Naming Conventions
- JavaScript/JSX (ESM). Prefer functional components with hooks; keep state colocated and side effects inside `useEffect`.
- Indent with 2 spaces; favor double quotes to match existing files. Use camelCase for variables/functions and PascalCase for components.
- Keep fetch paths absolute (`/letras/...`, `/temas.json`) to match Vite’s public dir behavior. When adding assets, update `public/letras/index.json` consistently.
- Use inline comments only for non-obvious logic (e.g., preload strategy, theming application).

## Testing Guidelines
- No automated tests yet; rely on manual QA. Minimum check: `npm run lint`, then run `npm run dev` and verify verse rotation, theme swap, quiz flow, and favicon updates for several albums.
- If adding tests, prefer React Testing Library and place specs under `src/__tests__/` mirroring component names.

## Commit & Pull Request Guidelines
- Commit messages are short, present-tense, and often in Portuguese (e.g., “dicas adicionadas”). Stay concise and descriptive.
- For PRs, include: summary of changes, rationale, manual test notes (browsers/devices), and screenshots/gifs for UI updates. Link issues when available.
- Keep PRs scoped (feature or fix per PR). Run `npm run lint` before opening.

## Data & Asset Changes
- Validate new verse files: structure `{ "album": "<name>", "versos": ["..."] }`, filename listed in `letras/index.json`, album name matching `src/assets/albums.json`.
- Optimize new images before adding; keep numbering contiguous (1-28) or document any gaps. Do not store secrets or API keys; this app is entirely static.
