## Takudzwa Kachingwe 250625 Practical Assignment 2

The page is styled mobile-first. `style.css` holds the base styles for phones, and two hand-written `min-width` media queries (768px and 1024px) add tablet and desktop layouts. Tailwind (CDN) provides utility classes on the nav and the contact form. Layout changes at each breakpoint come from CSS, not from shrinking the desktop design.

### Breakpoints
I tested the page in the browser DevTools device toolbar at three widths:

| Width | Device class | Result |
|-------|--------------|--------|
| ~375px | Mobile | Single-column layout. Nav links wrap and are centred. Hero text and buttons are stacked. About photo sits above its text. Skills and projects are in one column. |
| ~768px | Tablet | Nav moves to the right. Hero dot pattern appears. About photo and text sit side by side. Skills are in 2 columns. Projects are in 2 columns, with the third card full width. |
| ~1280px | Desktop | Same as tablet, except projects are in 3 columns. Content is centred in a 1080px column. |

### Flexbox
- **Nav (Tailwind):** `flex flex-wrap items-center justify-center gap-x-6 gap-y-3 md:justify-end md:gap-x-12`. Links are centred and wrap on mobile, and sit on the right from 768px.
- **Hero:** a column flex container with `justify-content: center` and `gap`. The two hero buttons sit in a `flex-wrap` row with `align-items: center`.
- **About:** the photo and intro text are a column on mobile and a row from 768px (`flex-direction: row; align-items: center`).
- **Project tags and footer:** tags use `flex-wrap` and `gap`; the footer switches to `justify-content: space-between` from 768px.

### Grid
- **Skills:** one column on mobile, `repeat(2, 1fr)` from 768px, with `gap: 1.25rem`.
- **Projects:** one column on mobile, `repeat(2, 1fr)` at 768px (the third card spans the row with `grid-column: 1 / -1`), and `repeat(3, minmax(0, 1fr))` at 1024px.
- **Contact form (Tailwind):** `grid grid-cols-1 gap-x-8 gap-y-8 md:grid-cols-2`, with `md:col-span-2` on the full-width fields.

### Tailwind
- **Nav:** `flex`, `flex-wrap`, `items-center`, `justify-*`, `gap-*` and the `md:` variants above.
- **Contact form:** `grid`, `grid-cols-*`, `gap-*`, `col-span-*`, `justify-self-start`, and `flex flex-col gap-2` on each field group.
- **Mixing Tailwind with my own CSS (intentional):** Tailwind handles layout utilities on those two components. My own CSS handles design tokens, typography, colours, the box model and the Grid sections. Element selectors in `style.css` are prefixed with `body` so Tailwind's preflight reset does not override them.

### Images and text
Images use `max-width: 100%; height: auto`. Headings use `clamp()` so they scale smoothly between breakpoints, and paragraphs use `max-width` in `ch` to keep line lengths readable.

### Code quality and known notes
- HTML validated with the W3C validator.
- Console: No errors; the Tailwind CDN logs a development-only 'not for production' warning, which is expected when using the CDN script.
- No placeholder or Lorem ipsum text is left in the page.
- Markup note: I kept all semantic elements, section IDs and form fields from Assignment 1, and added extra elements to support the new design. The nav now comes before the header, and the photo moved from the header into the About section.
