🔖 Smart Bookmark App

A minimal full-stack bookmark manager built with Next.js (App Router) and Supabase.

Users can sign in using Google OAuth, create private bookmarks, and see real-time updates across multiple tabs.

🌐 Live Demo

👉 https://smart-bookmark-app.vercel.app

(Test using any Google account)

🧠 Features

🔐 Google OAuth authentication (no email/password)

➕ Add bookmarks (Title + URL)

❌ Delete your own bookmarks

🔒 Bookmarks are private per user (RLS enforced)

⚡ Real-time updates across tabs

🚀 Deployed on Vercel

🛠 Tech Stack

Next.js 14 (App Router)

Supabase

Authentication

PostgreSQL

Row Level Security (RLS)

Realtime subscriptions

Tailwind CSS

Vercel (Deployment)

🔐 Security Implementation

Row Level Security (RLS) is enabled on the bookmarks table.

Policies ensure:

Users can only view their own bookmarks

Users can only insert bookmarks with their own user_id

Users can only delete their own bookmarks

This guarantees strict user-level data isolation.

⚡ Realtime Logic

Supabase Realtime is used to:

Listen to INSERT events

Listen to DELETE events

Update UI instantly without refresh

If two tabs are open and a bookmark is added in one, it appears automatically in the other.

🗄 Database Schema
bookmarks
---------
id          uuid (primary key)
title       text
url         text
user_id     uuid
created_at  timestamp

🧩 Challenges Faced
1. Google OAuth Redirect Mismatch

Initially faced redirect_uri_mismatch errors due to incorrect configuration between:

Google Cloud Console

Supabase Auth settings

Localhost & Vercel domains

Resolved by aligning all authorized redirect URLs correctly.

2. Row Level Security Setup

Ensuring proper RLS policies while maintaining realtime functionality required careful policy design using auth.uid().

3. Production Environment Variables

Had to configure environment variables correctly in Vercel for authentication to work in production.

🏃 Local Setup
git clone https://github.com/Rachit141/smart-bookmark-app.git
cd smart-bookmark-app
npm install


Create .env.local:

NEXT_PUBLIC_SUPABASE_URL=your_project_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_anon_key


Run:

npm run dev

🚀 Deployment

Deployed using Vercel with production environment variables configured securely in dashboard settings.

👤 Author

Rachit Jain
GitHub: https://github.com/Rachit141
