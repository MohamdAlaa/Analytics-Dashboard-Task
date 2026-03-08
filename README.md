# Ledgers – Frontend Developer Technical Assignment

This project is a responsive analytics dashboard built with **Vue 3**, **Vite**, **Tailwind CSS**, and **PrimeVue**, based on the provided `task.png` design reference.

## Tech stack

- Vue 3 (Composition API)
- Vite
- Tailwind CSS
- PrimeVue + Chart.js (for charts)

## Getting started

### Prerequisites

- Node.js 18+ and npm

### Installation

```bash
cd "d:\Ledgers task"
npm install
```

### Development server

```bash
npm run dev
```

Then open the printed local URL in your browser (usually `http://localhost:5173`).

## Project structure

- `src/main.js` – Vue app bootstrap, Tailwind and PrimeVue setup.
- `src/App.vue` – Root component wiring the main layout.
- `src/components/layout/*` – Reusable layout components (top navigation, sidebar, layout shell).
- `src/components/dashboard/*` – KPI cards, chart cards, main dashboard, and scenario panels.
- `src/assets/main.css` – Tailwind entrypoint and global styles.
