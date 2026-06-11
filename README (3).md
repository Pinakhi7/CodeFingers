# CodeFingers ⌨️

A typing practice app for programmers — type real code snippets with a live keyboard hand guide.

## Features

- 🎯 Real code snippets (Python, JavaScript, and more)
- 🖐️ Live finger guide overlay on keyboard (Typing Jungle style)
- 📊 WPM, Accuracy, Errors, Time stats
- 🏆 Result screen with missed-character heatmap
- 👤 User registration & progress tracking
- 🔑 Owner admin panel
- 🌙 Dark theme with finger-color keyboard

---

## 📁 Project Structure

```
codefingers/
├── index.html            # Entire app (single HTML file)
├── config.js             # ⚠️ YOUR private credentials (gitignored)
├── config.example.js     # Safe template — copy to config.js
├── firebase.json         # Firebase Hosting config
├── .firebaserc           # Firebase project alias
├── .gitignore            # config.js is excluded here
├── README.md
└── .github/
    └── workflows/
        └── firebase-deploy.yml  # Auto-deploy on git push
```

---

## 🔐 First-Time Setup (Important!)

**Before running the app**, set up your owner credentials:

```bash
# 1. Copy the example config
cp config.example.js config.js

# 2. Edit config.js with your real email and name
#    (This file is gitignored — safe, never pushed to GitHub)
```

`config.js` contents:
```js
const CF_OWNER_EMAIL = 'your-email@example.com';
const CF_OWNER_NAME  = 'Your Name';
```

> ⚠️ **`config.js` is in `.gitignore` — it will never be pushed to GitHub.**
> Always keep your real credentials in `config.js`, never in `index.html`.

---

## 🚀 Deploy to Firebase Hosting

### 1. Install Firebase CLI
```bash
npm install -g firebase-tools
```

### 2. Login
```bash
firebase login
```

### 3. Create a Firebase project
Go to [console.firebase.google.com](https://console.firebase.google.com) → **Add Project** → copy your **Project ID**.

### 4. Set your project ID
Edit `.firebaserc`:
```json
{
  "projects": {
    "default": "your-actual-project-id"
  }
}
```

### 5. Deploy
```bash
firebase deploy
```

✅ Live at `https://YOUR_PROJECT_ID.web.app`

> ⚠️ **Important:** When deploying, `config.js` must exist locally — Firebase will upload it.
> It's only excluded from **git**, not from **firebase deploy**.

---

## 🐙 Push to GitHub

```bash
git init
git add .
git commit -m "Initial commit — CodeFingers"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/codefingers.git
git push -u origin main
```

> `config.js` will NOT be pushed — it's in `.gitignore`. ✅

---

## 🔄 Auto-Deploy on Git Push (GitHub Actions)

The included `.github/workflows/firebase-deploy.yml` auto-deploys to Firebase every time you push to `main`.

**Setup:**
1. Go to your GitHub repo → **Settings** → **Secrets and variables** → **Actions**
2. Add secret: `FIREBASE_SERVICE_ACCOUNT` (get this from Firebase Console → Project Settings → Service Accounts → Generate new private key)
3. Edit `firebase-deploy.yml` — replace `YOUR_FIREBASE_PROJECT_ID` with your real project ID
4. Push to `main` → auto-deploys ✅

> ⚠️ With GitHub Actions, `config.js` is not in the repo.
> Use a GitHub Secret for owner credentials and inject at build time, OR
> keep using Firebase CLI deploy locally (recommended for simplicity).

---

## 💻 Local Development

No build step — single HTML file:

```bash
# Just open in browser
open index.html

# Or serve locally (avoids CORS issues)
npx serve .
```

---

## 👑 Admin Panel

1. Open the app → **Sign In**
2. Enter your owner email (from `config.js`)
3. First login → set your owner password
4. Admin panel: manage snippets, view session logs, manage users


