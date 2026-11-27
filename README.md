# NEON//ORBIT · Space Exploration Quiz

A cyberpunk-themed, accessible 10-question space exploration quiz in a single `index.html`.
No build step, no server, no dependencies.

## Run it

Open `index.html` in any modern browser, or visit the published site at
<https://mahdtech.github.io/space-quiz/>.

## Development

Changes go through pull requests into `trunk`.

- **CI** (`.github/workflows/ci.yml`) runs on every pull request and validates
  `index.html` and the SVGs with [html-validate](https://html-validate.org/)
  and the W3C [Nu HTML Checker](https://validator.github.io/validator/).
- **Deploy** (`.github/workflows/pages.yml`) runs on every push to `trunk`,
  repeats the same checks, then publishes `index.html` and `images/` to
  GitHub Pages.

To run the checks locally (requires Node.js 24 and Java 17+):

```sh
npm ci --ignore-scripts
npm test
```

The validators are dev tooling only; the quiz itself has no dependencies.

## Features

- 10 questions on spaceflight history, shuffled each run, each with a short fact
- Segmented progress bar, live score counter and a results screen with an answer log
- Animated feedback: a rocket or UFO flyby for correct answers, an exploding rocket for wrong ones
- Light/dark theme toggle that follows the system preference by default
- Keyboard play (`1`–`4` / `A`–`D`), screen reader labels, visible focus rings,
  WCAG AA contrast, and support for reduced motion and forced colours

## Structure

```text
index.html          # markup, styles and script
images/             # SVG artwork (rocket, flame, UFO, explosion, sun, moon)
.github/workflows/  # CI validation and GitHub Pages deployment
.htmlvalidate.json  # html-validate rules
```
