# The Shelf — browser-only setup

This version is designed so you do **not** need to install Node.js, Git, the Firebase CLI, or use a command line.

It uses:

- **GitHub Pages** — hosts the website
- **Firebase Firestore** — stores the shared book-club data
- **Firebase Authentication** — only for the private admin controls
- **Open Library** — searches for books and supplies covers

## Files

- `index.html` — the complete website
- `firestore.rules` — the database security rules (paste these into Firebase's Rules screen)
- `firebase.json` — not required for GitHub Pages; included for completeness if you later choose Firebase Hosting
- `.gitignore` — optional housekeeping

## Browser-only setup

### 1. Create a GitHub repository

On GitHub, create a **public** repository, e.g. `the-shelf-book-club`.

Upload `index.html` to the top level of the repository. You can also upload this README and the other files if you want, but only `index.html` needs to be published.

### 2. Turn on GitHub Pages

In the repository, open **Settings → Pages**.

Under **Build and deployment**:

- Source: **Deploy from a branch**
- Branch: **main**
- Folder: **/(root)**
- Click **Save**

GitHub will give you a site address similar to:
`https://YOUR-USERNAME.github.io/the-shelf-book-club/`

### 3. Create a Firebase project

Open https://console.firebase.google.com/ and create a new project.

Then register a **Web app** from Project Overview (the `</>` icon).

Firebase will show a `firebaseConfig` object.

### 4. Put the Firebase config into index.html

On GitHub, open `index.html`, click the edit/pencil button, and find:

`const firebaseConfig = { ... }`

Replace the placeholder values with the values from your Firebase Web App configuration.

### 5. Enable Firestore

Firebase Console → **Build → Firestore Database → Create database**.

### 6. Add the security rules

Firebase Console → **Firestore Database → Rules**.

Replace the rules there with the contents of `firestore.rules`.

Before publishing the rules, replace:

`REPLACE_WITH_YOUR_GOOGLE_EMAIL`

with the Google email address you will use as the administrator.

Click **Publish**.

### 7. Enable Google sign-in

Firebase Console → **Authentication → Sign-in method → Google → Enable → Save**.

### 8. Add your GitHub Pages domain to Firebase Authentication

Firebase Console → **Authentication → Settings → Authorized domains**.

Add:

`YOUR-USERNAME.github.io`

Do not add the `/the-shelf-book-club` part; Firebase wants the domain only.

### 9. Put your admin email into index.html

In `index.html`, find:

`const ADMIN_EMAIL = 'REPLACE_WITH_YOUR_GOOGLE_EMAIL';`

Replace it with the same Google email used in the Firestore rules.

Commit the change to GitHub.

### 10. Wait for GitHub Pages to publish

Open the GitHub Pages URL. The first deployment can take several minutes.

## What visitors can do

- View the shelf and schedule
- Search Open Library
- Add a book to the running shelf without an account
- Add a book to the reading schedule without an account

## What the admin can do

- Sign in with the configured Google account
- Delete shelf entries
- Delete schedule entries

## Important security note

The Firebase web configuration is intentionally present in the browser code. It is not a password. The important protection is the Firestore security rules.

Do not put passwords, service-account credentials, or Firebase Admin SDK private keys into `index.html` or GitHub.
