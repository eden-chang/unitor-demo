# Unitor — UI Prototype

> A clickable, frontend-only prototype of Unitor, a tool that helps university students find compatible teammates for course group projects. It was built for CSC318 (University of Toronto) user testing.

[![Deploy to GitHub Pages](https://github.com/eden-chang/unitor-demo/actions/workflows/deploy.yml/badge.svg)](https://github.com/eden-chang/unitor-demo/actions/workflows/deploy.yml)

**This repo is the design prototype.** The full-stack version, with a FastAPI backend, Supabase Postgres with row-level security, server-side compatibility scoring, and a React frontend wired to the live API, is in **[eden-chang/unitor](https://github.com/eden-chang/unitor)**.

All data here is hard-coded mock data. State is kept in `localStorage`, so the full flow can be clicked through without a backend.

## What you can click through

- **Onboarding**: landing page, role selection (Student or TA/Instructor), sign-up with validation, email verification, and joining a course by code
- **Profile wizard**: skills with proficiency levels, a weekly availability grid, communication preferences, and a bio
- **Discovery board**: student and group cards with compatibility scores, schedule-overlap bars, filters, sort, search, starring, and hiding cards
- **Compatibility detail**: score breakdown, match reasons, and skill complementarity for good, normal, and poor matches
- **Chats**: a 3-panel inbox with group-request cards, accept or decline flows, and simulated auto-replies with a typing indicator
- **My Group**: forming and confirmed states, a confirm dialog, and leaving the group
- **Deadline mode**: an urgent view with recommended teammates as the group-formation deadline nears
- **TA views**: course creation and a course dashboard

Press **Ctrl+D** to toggle the demo bar, which jumps directly to any screen and switches the mock student's status.

## Tech stack

| Area | Technology |
|---|---|
| UI | React 19, TypeScript |
| Build | Vite 7 |
| Styling | Tailwind CSS 4, shadcn/ui (Radix primitives), an OKLCH color-token system |
| Deploy | GitHub Actions → `gh-pages` branch (GitHub Pages) |

## Getting started

Prerequisites: Node.js 20+ and npm.

```bash
npm ci
npm run dev        # http://localhost:5173/unitor-demo/
npm run build      # production build into dist/
npm run preview    # serve the production build locally
```

The Vite `base` is `/unitor-demo/` to match the GitHub Pages path.

## Deployment

Every push to `main` runs [`.github/workflows/deploy.yml`](./.github/workflows/deploy.yml). The workflow builds the app and publishes `dist/` to the `gh-pages` branch with `peaceiris/actions-gh-pages`.

## Project structure

```
unitor-demo/
├── public/profile_images/   # Avatars for the mock students
├── src/
│   ├── App.tsx              # All prototype screens, mock data, and navigation
│   ├── components/ui/       # shadcn/ui primitives
│   ├── lib/utils.ts         # className helper
│   ├── index.css            # Tailwind setup and design tokens
│   └── main.tsx
├── index.html
└── vite.config.ts
```

The whole prototype lives in one `App.tsx` on purpose: it was built for fast iteration during user testing. In the [main Unitor repo](https://github.com/eden-chang/unitor), this file is split into feature components, API hooks, and a real backend.
