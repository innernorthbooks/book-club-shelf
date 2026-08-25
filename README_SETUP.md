# The Shelf — Book Club App

This is a simple public book-club website using:

- Firebase Hosting — publishes the website
- Cloud Firestore — stores the shared shelf and reading schedule
- Firebase Authentication — only used for the private admin delete controls
- Open Library — searches for books and supplies cover images
- GitHub — keeps a copy of your website files and tracks changes

## Important before you publish

You will need to replace two placeholders:

1. In `index.html`, find `const firebaseConfig = { ... }` and paste in your Firebase Web App configuration.
2. In `index.html`, replace `REPLACE_WITH_YOUR_GOOGLE_EMAIL` with the Google email address you will use for admin sign-in.
3. In `firestore.rules`, replace `REPLACE_WITH_YOUR_GOOGLE_EMAIL` with that same email address.

The Firebase web configuration is normal client-side configuration; do not put passwords or private API keys in it.

## Recommended setup order

1. Create a GitHub account.
2. Create a Firebase account/project.
3. Create a Firestore database.
4. Enable Google sign-in in Firebase Authentication.
5. Register a Web App in Firebase and copy its config into `index.html`.
6. Replace the admin email placeholder in both `index.html` and `firestore.rules`.
7. Install the Firebase CLI.
8. From this folder, run `firebase login`.
9. Run `firebase use --add` and choose your Firebase project.
10. Run `firebase deploy --only hosting,firestore`.
11. Open the Firebase Hosting URL shown after deployment.

## What visitors can do

- View the shelf and schedule.
- Search Open Library for books.
- Add a book to the running shelf without an account.
- Add a book to the reading schedule without an account.

## What only the admin can do

- Sign in with the configured Google account.
- Delete shelf entries.
- Delete schedule entries.

## If you want to change the club name

The easiest place is near the top of `index.html`, in the header:

`<h1>The Shelf</h1>`

You can also change the eyebrow and description immediately around it.
