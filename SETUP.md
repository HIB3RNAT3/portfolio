# One-time setup

Everything code-side is done. Firestore, Storage, Hosting, and Authentication
are enabled in the console — the only thing left is logging the CLI in,
which needs your Google account so it can't be automated for you.

## Log in to the Firebase CLI

```
npx firebase-tools login
```

This opens a browser window for you to approve. Once it's done, come back and
the deploy commands below will work without asking you to log in again.

## Deploy

```
npx firebase-tools deploy --only firestore:rules,storage   # push security rules
npx firebase-tools deploy --only hosting                    # push the site
```

Or all at once: `npx firebase-tools deploy`.

Live site after deploy: whatever URL Firebase Hosting prints (something like
`https://godgabe.web.app`).

## How admin editing works

Click the small ⚿ button in the bottom-right corner of the site and sign in
with the Google account for **huntergodward@gmail.com**. An orange bar appears
at the top; click any text to edit it, use **+ Add project** / **Remove
project** on the cards, then **Save changes**. Anyone signing in with a
different Google account is automatically signed back out — only that one
email can write to Firestore (enforced in `firestore.rules`, not just in the
page).

Contact form submissions land in the `messages` collection in Firestore —
visible to you in the console, not publicly readable.
