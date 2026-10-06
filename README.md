# SkyPulse

**SkyPulse** is a polished, fully static weather dashboard designed for GitHub Pages. It combines live weather, dynamic condition-based themes, geolocation, a 24-hour chart, saved cities, astronomy, historical lookup, shareable URLs, and a quote of the day — without a backend.

## Features

- Search any city by name using Open-Meteo geocoding
- One-click browser geolocation with `navigator.geolocation.getCurrentPosition()`
- Last searched city automatically restored from `localStorage`
- Dynamic themes for clear, rain, snow, clouds/fog, thunderstorms, and night
- Lightweight CSS rain, snow, cloud, sun, and lightning animation
- Celsius/Fahrenheit and km/h/mph switching without re-fetching data
- Custom animated SVG weather icons
- 24-hour Chart.js temperature chart
- 7-day forecast
- Up to six saved cities in a favorites sidebar
- Shareable `?city=Tokyo` URLs
- Sunrise/sunset visualization
- Lightweight locally calculated moon phase + illumination
- Historical weather lookup with a date picker
- Quote of the day plus a random-quote refresh button
- Responsive mobile/desktop layout
- `prefers-reduced-motion` support

## Project structure

```text
skypulse/
├── index.html
├── styles.css
├── app.js
├── .nojekyll
├── README.md
└── assets/
    └── favicon.svg
```

## Run locally with Node.js

Node is only used as a local static server:

```bash
npx serve .
```

or:

```bash
npx http-server .
```

Then open the URL printed in the terminal.

No code changes are required because all local paths are relative.

## APIs and libraries

- Open-Meteo Forecast API
- Open-Meteo Geocoding API
- Open-Meteo Historical Weather API
- DriveBird Quotes API
- OpenStreetMap tiles
- Chart.js 4.4.7

The core app requires no API keys. The quote feature fails gracefully, so a temporary quote-service outage does not break current weather.

## Performance notes

This version includes a performance pass specifically for smooth scrolling and map interaction:

- Removed large-area backdrop blur from dashboard cards.
- Converted cloud movement from layout-changing `left` animation to GPU-friendly transforms.
- Reduced weather particle counts.
- Uses `content-visibility` for heavy off-screen sections.
- Disables scroll-wheel map zoom so the map does not fight normal page scrolling.
- Caches favorite-city weather for 10 minutes so switching °C/°F does not trigger new API requests.
- Shortened Chart.js animation duration.
