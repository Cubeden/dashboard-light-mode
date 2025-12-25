### CSS architecture

Styles are organized by responsibility:

- `assets/css/base.css` — global base styles (html, body, typography, resets).
- `assets/css/layout.css` — layout primitives and page structure (containers, grids, wrappers).
- `assets/css/components.css` — reusable UI components (cards, buttons, forms).
- `pages/**/**.css` — page/section-specific styles, scoped to a single page or feature.

This structure avoids duplication, scales well for multi-page layouts, and is ready for migration to Vite or any bundler.

---

### The order should be as follows:

```html
<link rel="stylesheet" href="../../assets/css/base.css" />
<link rel="stylesheet" href="../../assets/css/layout.css" />
<link rel="stylesheet" href="../../assets/css/components.css" />

<link rel="stylesheet" href="../authentication/sign.authentication.css" />
<link rel="stylesheet" href="page.error.css" />
```

- Why:
  - `base.css` is the foundation (fonts, body/html, basic typography). It should come first.
  - `sign.authentication.css` is a more specific layer (section/page).
  - `page.error.css` is the most specific (a specific page) and should come last to override everything above it.

---

### CSS isolation via root page class (Variant A)

Non-original pages (404, maintenance, coming-soon, sign-in, sign-up) use **shared global CSS**, where classes like `header`, `footer`, `container` are reused.  
To avoid conflicts, styles are scoped using a **root page class** instead of renaming HTML.

### Idea

Add one root class to the page and scope all styles through it.

**Namespaces:**

- `xauth` — sign-in / sign-up
- `xerror` — 404 / maintenance
- `xsoon` — coming-soon

### Example

## CSS isolation via root page class (Variant A)

Non-original pages (404, maintenance, coming-soon, sign-in, sign-up) use **shared global CSS**, where classes like `header`, `footer`, `container` are reused.  
To avoid conflicts, styles are scoped using a **root page class** instead of renaming HTML.

### Idea

Add one root class to the page and scope all styles through it.

**Namespaces:**

- `xauth` — sign-in / sign-up
- `xerror` — 404 / maintenance
- `xsoon` — coming-soon

### Example

```html
<body class="xauth">
	<header class="header">...</header>
	<footer class="footer">...</footer>
</body>
```

```css
.xauth .header {
	/* auth header only */
}
.xauth .footer {
	/* auth footer only */
}

.xerror .footer {
	/* error pages */
}
.xsoon .header {
	/* coming-soon */
}
```
