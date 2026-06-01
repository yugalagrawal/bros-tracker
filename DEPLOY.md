# Bro's Tracker — Deployment Guide

## Step 1: Firebase Setup (Database)

1. Go to https://console.firebase.google.com
2. Click **"Add project"** → name it `bros-tracker` → Continue
3. Disable Google Analytics (not needed) → **Create project**
4. In the left sidebar → **Build → Realtime Database**
5. Click **"Create Database"** → choose any region → **"Start in test mode"** → Enable
6. Go to **Project Settings** (gear icon, top left) → **Your apps** → click `</>` (Web)
7. Register app name: `bros-tracker` → **Register app**
8. Copy the `firebaseConfig` object shown

9. Open `index.html` and find this section near the top of the `<script>`:

```js
const FIREBASE_CONFIG = {
  apiKey:            "YOUR_API_KEY",
  authDomain:        "YOUR_PROJECT.firebaseapp.com",
  databaseURL:       "https://YOUR_PROJECT-default-rtdb.firebaseio.com",
  ...
};
```

Replace all the placeholder values with your actual Firebase config.

10. **Lock down the database rules** (important!):
    - Firebase Console → Realtime Database → **Rules** tab
    - Replace with:
```json
{
  "rules": {
    "brosTracker": {
      ".read": true,
      ".write": true
    }
  }
}
```
    - Click **Publish**

---

## Step 2: GitHub Pages (Free Hosting)

1. Go to https://github.com → Sign in (or create account)
2. Click **"New repository"** → name: `bros-tracker` → Public → **Create repository**
3. Upload `index.html` (drag & drop on the repo page)
4. Commit the file
5. Go to **Settings → Pages** (left sidebar)
6. Under **"Branch"** → select `main` → `/ (root)` → **Save**
7. Wait ~60 seconds → your URL will be:
   `https://YOUR_GITHUB_USERNAME.github.io/bros-tracker`

---

## Done! Share the URL with Vikas and Dushyant.

All 3 of you will see the **same live data** — leaderboard, logs, approvals, everything syncs in real-time.

---

## Free Tier Limits (Firebase Spark Plan)
- Storage: 1 GB (you'll use ~1 MB)
- Downloads: 10 GB/month (you'll use ~10 MB)
- Connections: 100 simultaneous (you have 3 users)

**Verdict: Free forever for this use case.**
