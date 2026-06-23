---
quickstart-keeper: v1
git: committed
created: 2026-06-23
---

# QUICKSTART — Acme Shop

> One-line: Next.js storefront with a Stripe checkout. Read this before working; it's the map.

## Stack
- TypeScript, Next.js 14 (App Router), pnpm, Node 20, Postgres (Prisma)

## Layout
- [app/](app/) — routes & server actions
- [components/](components/) — UI components
- [lib/](lib/) — payments, db, auth helpers
- [prisma/](prisma/) — schema & migrations
- [app/api/webhooks/stripe/route.ts](app/api/webhooks/stripe/route.ts) — Stripe webhook entry

## Commands
- Install: `pnpm i`
- Dev: `pnpm dev`   ·   Test: `pnpm test`   ·   E2E: `pnpm test:e2e`
- Build: `pnpm build`   ·   Lint: `pnpm lint`
- DB migrate: `pnpm prisma migrate dev`

## Version & release
- SemVer in `package.json`. Release on git tag `v*` → CI builds and deploys to Vercel.
- Changelog auto-generated from Conventional Commits.

## Gotchas
- Stripe webhook needs the **raw** request body — never add a JSON body parser to that route.
- Env vars live in `.env` (see `.env.example`); `STRIPE_WEBHOOK_SECRET` must match the CLI tunnel.
- `pnpm dev` fails if Postgres isn't up — run `docker compose up -d db` first.

## Deep dives
- [checkout-flow](quickstart/checkout-flow.md) — spans 4 files + webhook ordering, easy to break

<!-- quickstart-keeper: keep this file concise. Prune stale lines. Never store secrets. -->
