# Turn on sync across devices (about 10 minutes, free)

GitHub Pages can only host the app's files. It can't store your closet for you, so without sync each browser keeps its own copy. Sync connects the app to a free **Supabase** project: a private database and photo storage that only you can sign in to. Once it's on, you sign in with your email on any phone or computer and see the same closet, and every change saves automatically.

You only do this once.

## 1. Create a Supabase project

1. Go to **https://supabase.com** and sign up (signing in with GitHub is easiest).
2. Click **New project**. Name it `closet`, make up a database password (save it somewhere, but you won't need it for the app), pick the region closest to you, and click **Create new project**.
3. Wait a minute or two while it sets up.

## 2. Create the storage for your closet

1. In the left sidebar, open the **SQL Editor** and click **New query**.
2. Copy everything in the box below, paste it in, and click **Run**. You should see "Success. No rows returned".

```sql
-- Your closet's records (clothes, outfits, pins, journal, settings)
create table if not exists public.closet_records (
  user_id uuid not null default auth.uid() references auth.users(id) on delete cascade,
  store text not null,
  id text not null,
  data jsonb,
  deleted boolean not null default false,
  updated_at timestamptz not null default now(),
  primary key (user_id, store, id)
);
alter table public.closet_records enable row level security;
create policy "closet: read own"   on public.closet_records for select using (auth.uid() = user_id);
create policy "closet: add own"    on public.closet_records for insert with check (auth.uid() = user_id);
create policy "closet: change own" on public.closet_records for update using (auth.uid() = user_id) with check (auth.uid() = user_id);
create policy "closet: delete own" on public.closet_records for delete using (auth.uid() = user_id);

-- Your photos, in a private folder per account
insert into storage.buckets (id, name, public) values ('closet', 'closet', false)
on conflict (id) do nothing;
create policy "closet photos: read own"   on storage.objects for select using (bucket_id = 'closet' and (storage.foldername(name))[1] = auth.uid()::text);
create policy "closet photos: add own"    on storage.objects for insert with check (bucket_id = 'closet' and (storage.foldername(name))[1] = auth.uid()::text);
create policy "closet photos: change own" on storage.objects for update using (bucket_id = 'closet' and (storage.foldername(name))[1] = auth.uid()::text);
create policy "closet photos: delete own" on storage.objects for delete using (bucket_id = 'closet' and (storage.foldername(name))[1] = auth.uid()::text);
```

The "policies" are what keep your closet private: every account can only ever read and change its own records and photos.

## 3. (Optional) Skip the confirmation email

By default Supabase emails a confirmation link when you create an account. That works fine, you just tap the link once. If you'd rather skip it: **Authentication → Sign In / Providers → Email** and turn off **Confirm email**.

## 4. Copy your two keys

Open **Project Settings** (the gear at the bottom of the sidebar), then **API** (it may be called **API Keys** or **Data API**). Copy:

- the **Project URL**, which looks like `https://abcdefgh.supabase.co`
- the **anon public** key (a long code starting with `eyJ`) or the **publishable** key (starting with `sb_publishable_`)

Never use the **service_role** or **secret** key. That one can bypass the privacy rules.

The anon or publishable key is designed to be public. It's safe in your website's code because the policies from step 2 decide what each signed-in person can see.

## 5. Put the keys in the app

Pick one of these:

**A. In the code (recommended, works on every device right away).** In your GitHub repo, open `index.html`, click the pencil icon to edit, and use **Ctrl+F** or **Cmd+F** to find `const CLOUD=`. Paste your two values between the quotes:

```js
const CLOUD={ url:'https://abcdefgh.supabase.co', anonKey:'eyJhbGciOi...' };
```

Click **Commit changes**, wait a minute, and hard-refresh the site (**Cmd+Shift+R** or **Ctrl+Shift+R**).

**B. In the app.** Open **Colors, backup and settings** (or the **⚙** button on a phone), paste both values under **Sync across devices**, and tap **Connect**. This only sets up that one browser, so you'd repeat it on each device. Option A is easier.

## 6. Create your account and bring in your closet

1. The sign-in screen now asks for an **email**. Tap **Create an account**, enter your name, email and a password.
2. Your new account starts empty. Open **Colors, backup and settings** and, under **Sync across devices**, tap **Bring in Ro's closet**. Everything saved in that browser (clothes, photos, likes, pins, journal and what the stylist learned) is copied into your account.
3. On your phone, open the site and sign in with the same email and password. Your closet downloads automatically, photos included.

If your old closet is on a different device, either do step 2 on that device, or use **Download backup** there and **Restore from backup** after signing in. Restoring also syncs.

## Good to know

- **It syncs automatically**: when you make a change, when you switch back to the app, and every minute while it's open. The sidebar (or the settings on a phone) shows **Synced across your devices**, **Saving…** or **Offline**.
- **Offline works.** Changes are saved on the device and sent when you reconnect.
- **Free plan limits:** Supabase's free plan includes about 1 GB of photo storage, roughly 1,500 to 3,000 pieces of clothing at the app's photo sizes. Check supabase.com/pricing for the current limits.
- **Free projects pause after about a week without any activity.** If the app says it can't reach your account after a long break, sign in to supabase.com and click **Restore project**. Your data is kept.
- **Your data stays yours.** Download a backup now and then anyway, as a safe copy.
