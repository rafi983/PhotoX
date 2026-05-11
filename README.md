# PhotoX Vue

A fully converted **Vue 3** version of the original PhotoX HTML template.

This project migrates the static HTML/CSS/jQuery template into a Vue single-page application, while preserving the original visual style and interactions.

## Overview

PhotoX Vue includes:

- Full landing page sections (header, mission, collection, gallery, customers, pricing, contact, footer)
- Vue-based dynamic interactions (no jQuery)
- Scoped component styling in `App.vue`
- Static assets served through Vue's `public` directory
- Bootstrap and Font Awesome loaded via CDN in `public/index.html`

## Tech Stack

- `Vue 3` (Vue CLI)
- `JavaScript` (Options API)
- `Bootstrap 4` (CDN)
- `Font Awesome 5` (CDN)

## Project Structure

```text
photoxvue/
├─ public/
│  ├─ index.html
│  └─ images/                # all template images
├─ src/
│  ├─ App.vue                # main page template, styles, behavior
│  └─ main.js                # app entry point
├─ package.json
└─ vue.config.js
```

## Getting Started

### 1) Install dependencies

```bash
npm install
```

### 2) Run development server

```bash
npm run serve
```

Open the local URL shown in terminal (usually `http://localhost:8080`).

### 3) Build for production

```bash
npm run build
```

### 4) Lint

```bash
npm run lint
```

## Available Scripts

- `npm run serve` → Starts dev server with hot reload
- `npm run build` → Creates optimized production build
- `npm run lint` → Runs ESLint checks

## Implemented Vue Behaviors

The original jQuery logic has been converted to Vue state/methods:

- Mobile menu toggle state
- Sticky/compact navbar on scroll
- Scroll-triggered animations for mission and pricing sections
- Gallery category filtering (`all`, `new`, `free`, `pro`)
- Customer testimonial switcher

## Asset Handling (Important)

All images are expected in:

`public/images`

The app resolves image paths with:

`process.env.BASE_URL + 'images/<name>'`

This keeps assets working in both local dev and production builds.

## Styling Notes

- Main styles are inside `src/App.vue` under `<style scoped>`
- Global body font is applied with `:global(body)`
- Background images (header/contact/pricing) are applied through Vue-bound style objects for reliable path resolution

## Customization Guide

You can quickly customize content from `src/App.vue`:

- Navigation links: `navItems`
- Mission blocks: `missionCards`
- Collection cards: `collection`
- Gallery items: `gallery`
- Customer testimonials: `customers`
- Pricing plans: `pricingPlans`

## Troubleshooting

### Images are not showing

Check the following:

1. Images exist in `public/images`
2. Filenames match exactly (case-sensitive in some environments)
3. URLs are built through the `asset()` helper in `App.vue`

### Styles/icons look broken

Make sure CDN links in `public/index.html` are reachable:

- Bootstrap CSS
- Font Awesome script
- Google Fonts (Montserrat)

## License

This repository currently does not define a license file.
