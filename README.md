### Project Architecture

- The project uses a scalable, section-based architecture designed for a multi-page dashboard (40+ screens).

```bash
- `pages/`                     — HTML pages grouped by feature/domain (dashboard, account, auth, system, etc.)
- `assets/`                    — shared static resources
  - `css/base.css`             — reset, design tokens, typography.    global
  - `css/components.css`       — reusable UI components               global buttons / UI
  - `css/sections/`            — layout and styles per section
  - `css/views/`               — page-specific styles
  - `img/`, `icons/`, `fonts/` — static assets
```

- This structure mirrors the Figma layout, avoids style duplication, and is ready for future migration to React/Next.js.
