# Rubans D2C — Task Tracker

A simple weekly task tracker for the D2C team, organized into 8 buckets:
Meta, Google, Catalog & Pricing BAU, CRO, Offers/Sale, Retention (WhatsApp),
Returns & Logistics, and P&L Margin Analysis.

Tasks are assigned for a given week, can carry a description and a reference
URL, and get ticked off as they're completed. Both you and your manager get
full edit access via a single shared password.

## Stack

- **Next.js** (App Router) — frontend + API routes
- **Vercel Postgres** — data storage
- **Vercel** — hosting

## 1. Push this to GitHub

```bash
cd d2c-tracker
git remote add origin https://github.com/<your-username>/d2c-tracker.git
git push -u origin main
```

(Create an empty repo on GitHub first — don't initialize it with a README,
since this project already has one.)

## 2. Deploy to Vercel

1. Go to vercel.com/new and import the GitHub repo.
2. Keep the default build settings (Next.js is auto-detected).
3. Before the first deploy, add one environment variable:
   - `APP_PASSWORD` — the shared password you and your manager will use to log in.
4. Click **Deploy**.

## 3. Attach Vercel Postgres

1. In your Vercel project, go to the **Storage** tab.
2. Click **Create Database** -> choose **Postgres**.
3. Follow the prompts to create it and connect it to this project.
   Vercel will automatically add the required `POSTGRES_*` environment
   variables to your project — no manual copying needed.
4. Redeploy the project once (Deployments tab -> ... -> Redeploy) so the new
   env vars are picked up.

The database table is created automatically the first time the app loads
data — no manual migration needed.

## 4. Share it

Send your manager the Vercel URL (e.g. https://d2c-tracker.vercel.app)
and the `APP_PASSWORD` you set. He logs in with the same password and has
full edit access — same as you.

## Using it day to day

- **Add tasks**: click "+ Add task" under any bucket, pick the week (default
  next week for planning ahead by Thu/Fri).
- **Tick complete**: click the circle next to a task.
- **Edit**: click a task's title, or the "Edit" button on hover.
- **Filter**: switch weeks or buckets from the dropdowns at the top.
- **Progress bar**: shows % complete for the selected week at a glance —
  useful for your manager's weekly check-in.

## Local development

```bash
npm install
# create .env.local with:
# APP_PASSWORD=your-local-password
# (Postgres env vars are only needed once deployed / linked via `vercel env pull`)
npm run dev
```
