# Open Brain — One-Page CRUD Viewer

A single-file HTML app for browsing and managing thoughts stored in a [Open Brain](https://github.com/crambo70/OpenBrain) Supabase database. Full CRUD. Zero npm. Zero build step. Open in browser.

## Setup

### 1. Enable RLS and add the access policy

In your Supabase project, go to **SQL Editor** and run:

```sql
alter table thoughts enable row level security;

create policy "local viewer full access" on thoughts
  for all to anon
  using (true)
  with check (true);
```

### 2. Get your credentials

In your Supabase dashboard, go to **Settings → API Keys** and copy:
- Your **project URL** (e.g. `https://your-project.supabase.co`)
- Your **publishable (anon) key**

### 3. Open the app

Double-click `index.html` in your file browser — no server required. On first load you'll see a **Connect to Supabase** prompt. Enter your URL and key and hit Connect. Credentials are saved to `localStorage` and you won't be asked again.

## Features

- List all thoughts, newest first, paginated
- Filter by type, topic, person, or free-text content search
- Click any topic chip to instantly filter by it
- Click a thought to open the full edit panel
- Create, edit, and delete thoughts
- Color-coded type badges: observation, task, reference, progress, person note

## Rolling back the RLS policy

If you ever want to remove access:

```sql
drop policy "local viewer full access" on thoughts;
```

## No dependencies

Supabase JS and DOMPurify are loaded from CDN. No npm, no build step, no node_modules.
