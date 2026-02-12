<h1 align="center">🔖 Smart Bookmark App</h1>

<p align="center">
  A minimal full-stack bookmark manager built with <b>Next.js 14</b> and <b>Supabase</b>.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Next.js-14-black?style=for-the-badge&logo=nextdotjs" />
  <img src="https://img.shields.io/badge/Supabase-Auth%20%7C%20DB%20%7C%20Realtime-3ecf8e?style=for-the-badge&logo=supabase" />
  <img src="https://img.shields.io/badge/TailwindCSS-38bdf8?style=for-the-badge&logo=tailwindcss" />
  <img src="https://img.shields.io/badge/Vercel-Deployed-black?style=for-the-badge&logo=vercel" />
</p>

---

## 🌐 Live Demo

🔗 **https://smart-bookmark-app-one.vercel.app/**  
> Test using any Google account

---

## ✨ Features

✔ Google OAuth login (no email/password)  
✔ Add bookmarks (Title + URL)  
✔ Delete your own bookmarks  
✔ Private per user (Row Level Security enabled)  
✔ Real-time updates across multiple tabs  
✔ Fully deployed on Vercel  

---

## 🏗 Tech Stack

| Technology | Usage |
|------------|--------|
| Next.js 14 (App Router) | Frontend & Routing |
| Supabase Auth | Google OAuth |
| Supabase Database | PostgreSQL |
| Row Level Security | User data isolation |
| Supabase Realtime | Live updates |
| Tailwind CSS | UI Styling |
| Vercel | Deployment |

---

## 🔐 Security Implementation

Row Level Security (RLS) is enabled on the `bookmarks` table.

Policies ensure:

- Users can only view their own bookmarks  
- Users can only insert bookmarks with their own `user_id`  
- Users can only delete their own bookmarks  

This guarantees strict user-level data isolation.

---

## ⚡ Realtime Functionality

The app subscribes to Supabase Realtime events:

- Listens to INSERT events
- Listens to DELETE events
- Updates UI instantly without refresh

If two tabs are open and a bookmark is added in one, it automatically appears in the other.

---

## 🗄 Database Schema

```sql
create table bookmarks (
  id uuid primary key default gen_random_uuid(),
  title text not null,
  url text not null,
  user_id uuid references auth.users(id),
  created_at timestamp default now()
);

```

---

## 🧠 Challenges Faced

### 1️⃣ Google OAuth Redirect Mismatch  
Resolved by correctly configuring:
- Google Cloud Console OAuth credentials  
- Supabase Auth redirect URLs  
- Localhost and Production URLs  

### 2️⃣ Row Level Security Policies  
Carefully implemented policies using `auth.uid()` to maintain strict user isolation.

### 3️⃣ Production Environment Variables  
Configured Supabase keys securely in Vercel dashboard.

---

## ▶ Run Locally

```bash
git clone https://github.com/Rachit141/smart-bookmark-app.git
cd smart-bookmark-app
npm install
npm run dev
```

---

## 📌 Notes

This project was built as part of a Full-Stack Micro Challenge.  
Focus was on correctness, security (RLS), and clean architecture using App Router.
