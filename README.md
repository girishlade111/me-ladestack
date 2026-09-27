# me-ladestack

A customizable personal link page (Linktree-style) — build your own "link in bio" page with an editable profile, sortable link list, and switchable themes, all in the browser. Profile, links, and theme are saved to localStorage, so no account or backend is needed.

## What it does

- **Personal link page** — one public-facing page showing your avatar, name, bio, and a list of links
- **Inline editor** — add, edit, reorder, and delete links without leaving the page
- **Profile customization** — avatar, display name, tagline, verified badge, profile form
- **Theme switcher** — multiple visual themes for the link page
- **Link actions** — copy link, share, per-link context actions
- **Toasts & dialogs** — friendly UX feedback via Radix-based toasts and confirmation dialogs
- 100% client-side; data persists in the browser's localStorage

## Features

- Linktree-like link tree with edit/view mode toggle
- Link management: add / edit / delete with URL validation
- Profile editor (name, bio, avatar)
- Theme settings with live preview
- Verified badge component, card-flip animation
- Responsive, mobile-first design
- Static-site friendly — builds to plain HTML/CSS/JS (`output: 'export'`)

## Tech stack

- **Next.js 15** (App Router, static export)
- **React 19**, **TypeScript 5**
- **Tailwind CSS 3**
- **shadcn/ui** (Radix primitives), `lucide-react` icons
- React hooks for state; `localStorage` for persistence

## Quick start

```bash
# install dependencies
npm install          # or: pnpm install

# run the dev server
npm run dev          # open http://localhost:3000

# production build (static export to ./out)
npm run build
```

Serve the static export with any static host:

```bash
npx serve out
```

## Project structure

```
app/                 # Next.js App Router (layout, page, global styles)
components/
  link-tree.tsx          # main link-page component
  link-tree/             # edit-view, header, profile/theme forms
  link-item.tsx          # link row + actions
  link-item/             # view-mode, edit-mode, delete-confirmation, utils
  verified-badge.tsx     # verified badge
  ui/                    # shadcn/ui primitives
hooks/
  use-links.tsx          # link list state management
  use-profile.tsx        # profile state
  use-theme-settings.tsx # theme state (localStorage persisted)
  use-toast.ts           # toast helper
lib/utils.ts         # cn() class helper
public/              # static assets
next.config.mjs      # output: 'export', unoptimized images
```

## Environment variables

None — no backend, no secrets.

## Deployment notes

- Statically exported (`out/`), so it can be hosted on **GitHub Pages**, **Vercel**, **Netlify**, or any static file host.
- `next.config.mjs` sets `basePath: '/me-ladestack'` for the GitHub Pages subpath deployment. For root-domain deploys (Vercel/custom domain), remove the `basePath` line and rebuild.

---

Built by Girish Lade — [ladestack.in](https://ladestack.in)
