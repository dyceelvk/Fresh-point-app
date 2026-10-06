# Backend launch checklist

The app currently runs as a static/PWA frontend. The Supabase migration in `supabase/migrations/001_initial.sql` provides the production data model for profiles, menu items, orders, order items, status events, payment status, and role-ready accounts.

## Apply the migration

1. Create a Supabase project.
2. Enable Email and Google providers under Authentication.
3. Add the values from `.env.example` to the frontend environment.
4. Run the SQL migration in the Supabase SQL editor, or use `supabase db push`.
5. Seed `menu_items` from the menu currently shown in `index.html`.
6. Configure Google OAuth redirect URLs for local and production domains.

## Production work still required

- Replace localStorage auth/cart with Supabase client calls.
- Create server-side order creation using a transaction and validation.
- Never trust prices sent by the browser; calculate totals from `menu_items`.
- Add a protected staff/admin dashboard for menu and order status changes.
- Add payment provider webhooks and verify signatures server-side.
- Add push notifications and delivery tracking only after the core order flow is live.
