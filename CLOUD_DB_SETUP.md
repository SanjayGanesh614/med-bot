# ☁️ Setting Up a Cloud Database for Persistent User Data

Since Streamlit Cloud resets your files (like SQLite) every time the app sleeps, you need a persistent database for user accounts to work.

## 1. Get a Free Database
We recommend **Neon** or **Supabase** (both have free tiers).

### Option A: Neon.tech (Fastest)
1. Go to [Neon.tech](https://neon.tech) and Sign Up.
2. Create a new "Project".
3. Copy the **Connection String** that looks like: 
   `postgres://user:password@ep-something.us-east-1.aws.neon.tech/neondb?sslmode=require`

### Option B: Supabase
1. Go to [Supabase.com](https://supabase.com) and Sign Up.
2. Create a "New Project".
3. Go to **Project Settings** -> **Database**.
4. Scroll down to "Connection String" -> "URI".
5. Copy the string.

## 2. Add to Streamlit Secrets
1. Go to your app on [Streamlit Cloud](https://share.streamlit.io).
2. Click "Manage App" (the 3 dots on the right).
3. Click **Settings** -> **Secrets**.
4. Paste the following into the text box, replacing the URL with the one you copied:

```toml
[database]
url = "postgres://your_user:your_password@your_host/your_db"
```

OR simply:

```toml
DATABASE_URL = "postgres://your_user:your_password@your_host/your_db"
```

5. Click **Save**.

## 3. Reboot Your App
Streamlit will automatically restart. The app will detect the secret and connect to the Cloud Database instead of the local file. Your user accounts will now remain saved forever!
