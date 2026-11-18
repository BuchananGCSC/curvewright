# Curvewright

A browser-based data analysis tool for iPad (Safari or Chrome) that covers the core of Vernier Graphical Analysis without sensor support. One file, no build step, no install, and nothing you enter leaves the browser.

## What it does

- Data table with typed entry, CSV import (paste or file) and CSV export
- Calculated columns: formulas (`x^2 + 2*sin(t)`), numeric derivative, and trapezoid integral
- Multiple graphs, each with its own X and Y columns
- Region selection by typing X min/max or by tapping two points on the chart; statistics and fits use only that region
- Curve fits: linear, quadratic, cubic, power, exponential, natural log, reciprocal, sinusoidal, and an automatic best-R² mode
- Statistics: n, mean, median, standard deviation, min, max, range
- FFT spectrum view per graph (Hann window or none), with a button that sends the peak frequency to the sinusoidal fit
- Save a graph as a PNG
- Light and dark themes; autosaves to the browser's local storage
- Two built-in sample datasets (projectile motion, two-tone signal)

## Run it

Open `index.html` in any modern browser. It loads Chart.js from cdnjs and the IBM Plex fonts from Google Fonts, so it needs an internet connection the first time.

## Host it on GitHub Pages

1. Push this repository to GitHub.
2. In the repository, open **Settings > Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, branch `main`, folder `/ (root)`, and save.
4. After a minute the site is at `https://<your-username>.github.io/<repository-name>/`.

GitHub Pages on a free account requires a public repository.

## Notes

- FFT assumes evenly spaced X values. The graph warns when spacing is uneven but does not resample.
- There is one shared data table; there are no separate runs or data-set tabs.
- Automatic fit mode tries a sinusoidal fit only after a peak frequency has been sent over from the FFT view, because a blind sine fit on multi-cycle data often fails to converge.
- Autosave is per browser and per device. Use Export CSV to keep data permanently.
