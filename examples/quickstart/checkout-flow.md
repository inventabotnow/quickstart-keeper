# Checkout Flow

**What it does:** Takes a cart to a paid order via Stripe Checkout, then fulfills on webhook.
**Start here:** [app/(shop)/cart/actions.ts](../../app/(shop)/cart/actions.ts)

## Flow
1. User clicks "Checkout" → server action `createCheckoutSession()` in
   [`cart/actions.ts`](../../app/(shop)/cart/actions.ts) builds line items from the cart.
2. Redirect to Stripe-hosted Checkout (we never see card data).
3. Stripe calls our webhook → [`api/webhooks/stripe/route.ts`](../../app/api/webhooks/stripe/route.ts)
   verifies the signature against the **raw** body.
4. On `checkout.session.completed` → `fulfillOrder()` in
   [`lib/orders.ts`](../../lib/orders.ts) marks the order paid and emails a receipt.

## Key files
- [`app/(shop)/cart/actions.ts`](../../app/(shop)/cart/actions.ts) — session creation
- [`app/api/webhooks/stripe/route.ts`](../../app/api/webhooks/stripe/route.ts) — webhook + signature check
- [`lib/orders.ts`](../../lib/orders.ts) — fulfillment & idempotency
- [`lib/stripe.ts`](../../lib/stripe.ts) — Stripe client config

## Gotchas
- **Raw body required:** the webhook route must read the raw body for signature verification.
  Adding any JSON body parser silently breaks it with a 400.
- **Idempotency:** Stripe can deliver the same event twice. `fulfillOrder()` no-ops if the order
  is already `paid` — don't remove that guard.
- **Local testing:** run `stripe listen --forward-to localhost:3000/api/webhooks/stripe` and set
  `STRIPE_WEBHOOK_SECRET` to the value it prints.

## How to change it safely
- Touch line-item construction in `createCheckoutSession()`; leave signature verification alone.
- After any change, re-run `pnpm test:e2e checkout` and replay a `checkout.session.completed`
  event with `stripe trigger checkout.session.completed`.
