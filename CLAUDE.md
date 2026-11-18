# Curvewright

Single-file (`index.html`) data analysis app for school iPads: a Vernier Graphical Analysis stand-in without sensor support. No build step, no dependencies beyond Chart.js 4.5.1 (cdnjs) and IBM Plex (Google Fonts).

## Layout of the script

One IIFE, in this order: math core (linear solver, polynomial/power/exponential/log/reciprocal/sinusoidal fits, FFT, stats, derivative, trapezoid integral, formula compiler) → app state and columns → localStorage autosave (`curvewright.session.v1`) → CSV import/export → data table → modals and file saving → graphs (Chart.js, region band plugin, fit and stats panels, FFT view) → theme refresh → sample data → init.

## Rules to keep

- Everything stays in `index.html`. Colors come from the CSS tokens on `:root`; dark mode is defined through the same tokens (media query plus `[data-theme]`), never by styling components inside a theme block.
- Touch targets are at least 34px, and most are 38 to 40px. The primary target is an iPad in landscape (about 1180 by 820) and portrait (834 wide).
- Column short names (`col.name`) are used as variables in formulas. Names that collide with math functions (`FORMULA_SCOPE`) or `i` and `n` are reserved.
- File saving goes through `offerDownload()`. It uses the Claude artifact `downloads` capability when `window.claude` exists and falls back to a Blob link otherwise, which is the GitHub Pages case.

## Testing

No test suite is in the repo. Earlier checks were Node tests of the math against synthetic data (known line, parabola, exponential, power, log, reciprocal, sine, FFT tone) and headless Playwright runs at iPad sizes. For a quick browser check, route the cdnjs and Google Fonts requests to local files so the test does not need the network, load `index.html`, and confirm the projectile sample shows a quadratic fit near `y = -4.94x² + 5.04x + 1.00` and the oscillation sample's FFT peak reads about 3.125 Hz.

## Copies

This repository is the source of truth. The private Claude artifact (`claude.ai/code/artifact/59a8fa2a-1407-40fc-aabb-18bc92f111d7`) was published earlier from the same code and is not updated by commits here. Republishing it means stripping the doctype/html/head/body wrapper from `index.html` first.
