# BookShelf.pk

Pakistan's premier online bookstore — a premium, feature-rich e-commerce experience for books, built better than book-shelf.pk.

## Run & Operate

- `pnpm --filter @workspace/bookshelf run dev` — run the bookshelf frontend (PORT auto-assigned)
- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- Frontend: React 18 + Vite + Tailwind CSS v4 + Framer Motion
- Routing: Wouter
- State: React Context + useReducer
- API: Open Library API (openlibrary.org) — no API key needed
- API Server: Express 5
- DB: PostgreSQL + Drizzle ORM (not used by bookshelf frontend)

## Where things live

- `artifacts/bookshelf/` — main bookshelf web app
  - `src/lib/api.ts` — Open Library API integration
  - `src/lib/context.tsx` — cart, wishlist, auth, panel state
  - `src/components/Navbar.tsx` — navbar with mega menus + icon sidebars
  - `src/components/Hero.tsx` — spatial parallax hero section
  - `src/components/RightPanel.tsx` — cart/search/login/wishlist slide panels
  - `src/components/Chatbot.tsx` — book recommendation chatbot
  - `src/pages/Home.tsx` — full home page
  - `src/pages/BookDetail.tsx` — book detail with reviews + recommendations
- `bookshelf-standalone/` — standalone version for zip export
- `bookshelf-pk.zip` — downloadable standalone project

## Product

- **Spatial parallax hero** adapted from the provided code, featuring book covers and scroll-driven animations
- **Real book data** from Open Library API (1M+ books, real cover images)
- **Right-slide panels** for Cart, Search, Login/Register, Wishlist — opened by clicking navbar icons
- **Mega nav dropdowns** on Books and Categories nav links with enhanced hover animations
- **Book detail pages** — clicking any book opens full detail: cover, price/format selector, reviews, recommendations
- **Working chatbot** — searches Open Library API for book queries, handles store FAQs
- **Full cart** with qty controls, wishlist, auth state
- **Responsive** — works on mobile, tablet, desktop

## User preferences

_Populate as you build — explicit user instructions worth remembering across sessions._

## Gotchas

- Open Library API can be slow (external network); books load async after initial render
- Cover images use `covers.openlibrary.org` — may occasionally 404 for obscure books (fallback to placeholder shown)
- `animation-timeline: scroll()` requires modern Chrome/Edge; Firefox needs `layout.css.scroll-driven-animations.enabled` flag

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
- Standalone zip: `bookshelf-pk.zip` — unzip, `npm i`, `npm run dev`
