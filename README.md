# Takudzwa — Personal Profile & Mini-Portfolio

A one-page, semantic HTML5 profile site built for the Web Technologies (CIS2103) Unit II practical assignment,
featuring an About section, skills list, a small project showcase, and a native-HTML5-validated Contact Me form.

## AI-Assisted Content

The About-section bio was drafted with AI assistance and then critically revised so it genuinely reads like me.
See the full prompt, the AI's raw output, my edited final version, and my reflection in **[PROMPT_LOG.md](./PROMPT_LOG.md)**.

## Accessibility: Peer Review Issue & Fix

1. **Generic alt text** — the profile photo's `alt` attribute just said `"Profile Image"`, which doesn't tell a
   screen-reader user anything meaningful about the image.
   **Fix:** updated the `alt` text to a descriptive `"Headshot photo of Takudzwa smiling at the camera"`.
2. **Low-contrast, color-only button cue** — the original "send" button used inline `style="background-color: blue"`
   with default blue link-colored text elsewhere on the page, which risked inconsistent, borderline contrast against
   the light backgrounds.
   **Fix:** moved styling into `style.css`, standardized the accent color to a darker `#0033cc` (which passes WCAG AA
   contrast against white and the light-gray section backgrounds), and added a visible `:hover`/`:focus` state on
   the button and nav links so interactive elements don't rely on color alone.

Other accessibility measures applied throughout the page:
- Every form input (`text`, `email`, `tel`, `textarea`) has a properly associated `<label for="">`/`id` pair.
- The `<nav>` has an `aria-label="Page sections"` to clarify its purpose for assistive technology.
- Heading levels are properly nested (`h1` → `h2` → `h3`, no skipped levels).

## Structure

- `index.html` — the semantic page markup (`header`, `nav`, `main`, multiple `section`s, an `article`, an `aside`,
  and a `footer`).
- `style.css` — all styling (no inline styles).
- `PROMPT_LOG.md` — the AI prompt, raw output, edited copy, and reflection for Part C.

## Notes

Native HTML5 validation only — no JavaScript is used to validate the Contact Me form (`required`, `type="email"`,
`pattern`, `minlength` attributes handle validation directly in the browser).
