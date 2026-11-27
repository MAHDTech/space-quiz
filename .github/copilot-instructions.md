# Space Quiz

NEON//ORBIT, a cyberpunk-themed 10-question space exploration quiz. A single file, no dependencies, accessible, and browser-tested.

## Rules

- Keep everything in a single `index.html` (inline `<style>` and `<script>`). No dependencies, no build step, no server. It must keep working when opened from `file://`.
- `package.json` devDependencies (`html-validate`, `vnu-jar`) are validation tooling only. Never load them, or any CDN or framework, from the page.
- Put SVG artwork in `images/` and reference it by path. Don't inline it. Decorative images get `alt=""`.
- Every answer must be reachable by keyboard: real `<button>`s, visible focus rings, and `1`-`4` / `A`-`D` shortcuts that fire only while focus is inside the quiz.
- Never use colour as the only signal. Pair it with text and icons (✓/✗). Keep screen-reader labels and focus management working.
- Honour `prefers-reduced-motion` (the CSS media query and the `reducedMotion` guard in JS). Keep the `forced-colors` styles working.

## Themes

- Respect `prefers-color-scheme` in both themes. The system preference is the default. The sun/moon toggle overrides it via `localStorage` (`neon-orbit-theme`).
- Take colours from the CSS custom properties in `:root` and `:root[data-theme="light"]`. Use `rgba(var(--x-rgb), a)` for tints. Don't hard-code a colour that only works in one theme.
- Light-theme accents are deeper so text keeps WCAG AA (4.5:1) contrast. Check any new colour in both themes.
- Canvas colours (the starfield `PALETTES`) need both a `dark` and a `light` entry. They update on the `themechange` event.

## Before you finish

- Run `npm ci --ignore-scripts` once, then `npm test`. It runs html-validate and the W3C Nu HTML Checker on `index.html` and `images/*.svg`. The checker needs Java 17+, and warnings count as errors.
- Then open `index.html` in a browser and check both themes, a full keyboard-only run, and reduced motion. "Browser-tested" means you actually checked it in a browser. If you can't, say so and list what to check.

## Workflow

- `trunk` is protected. Work on a topic branch and open a pull request into `trunk`. CI must pass, and merges to `trunk` deploy to GitHub Pages.

## How I like code written

- Small functions.
- Early returns.
- No clever one-liners.
- Comments only for what is genuinely surprising.
- Match the existing format: 4-space indent, double quotes, no semicolons in JS, lowercase `<!doctype html>`, self-closing void elements (`<img />`).
