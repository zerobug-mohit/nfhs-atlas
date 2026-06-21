# NFHS Atlas

[![View live dashboard](https://img.shields.io/badge/View%20live%20dashboard-2563eb?style=for-the-badge&logo=github&logoColor=white)](https://zerobug-mohit.github.io/nfhs-atlas/)

An offline-capable dashboard for exploring India's National Family Health Survey
data (NFHS-4, NFHS-5 and NFHS-6) across 640 districts and 37 states/UTs and 131
indicators. Built with [Vite](https://vitejs.dev/) and [D3](https://d3js.org/),
with PowerPoint and Excel export of any view.

## Repository structure

```
.
├── index.html              # app shell / markup
├── src/
│   ├── main.js             # entry: loads libraries + data, then the app
│   ├── app.js              # all dashboard logic (map, compare, change, profile, exports)
│   └── styles.css          # design system + component styles
├── public/data/            # survey + geometry data, served as static files
│   ├── nfhs_data.json      # indicators, districts, states, national values
│   ├── districts.json      # district GeoJSON (640 features)
│   └── states.json         # state/UT GeoJSON
├── vite.config.js
└── .github/workflows/deploy.yml   # CI: build + deploy to GitHub Pages
```

The data is loaded at runtime with `fetch`, so the JavaScript bundle stays small
and the JSON files are cached separately by the browser.

## Run locally

Requires Node.js 18+ (20 recommended).

```bash
npm install      # install dependencies
npm run dev      # start the dev server (http://localhost:5173)
npm run build    # production build into dist/
npm run preview  # preview the production build locally
```

## Notes on the data

NFHS-4/5 state and national figures are unweighted means of district values;
NFHS-6 figures are the official IIPS factsheet estimates (population-weighted,
state/UT and national only — no district series; Manipur was not surveyed in
2023–24). Δ 5→6 compares official figures on both ends; Δ 4→6 mixes bases and is
labelled accordingly. Ladakh shares 2011-census geometry with Jammu & Kashmir.

## License

Data © NFHS Factsheets, published by IIPS.
