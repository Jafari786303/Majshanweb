# Majshan Web Studio

A Firebase web-development order platform for customers, developers, and admins.

## Main Features
- English landing page for customers and developers.
- Registration as `customer` or `developer`; configured admin emails become `admin`.
- Google authentication is available from registration only after name, email, phone, location, and role are filled.
- Customers create website project requests.
- Developers see only pending open requests, can accept one, then other developers no longer see it.
- Customers see only their own projects.
- Developers see their accepted projects.
- Admin can view users/projects and can also work like a developer.
- Project statuses: `pending`, `accepted`, `done`, `closed`.
- Customer/developer project chat supports text plus uploaded image, video, audio, and document attachments directly in Firestore with a small-file limit.

## Firebase Project
Project configuration is set to `majshanweb-e99cd` in `auth.js`, `dashboard.js`, and `.firebaserc`.

Enable these Firebase products:
- Authentication: Email/Password and Google provider.
- Firestore Database: deploy or paste `firestore.rules` into Firestore Rules.
- Firebase Hosting: deploy this folder as a static site.

Required Firebase Console settings:
- Authentication -> Sign-in method: enable Email/Password.
- Authentication -> Sign-in method: enable Google.
- Authentication -> Settings -> Authorized domains: add your final Hosting/custom domain if it is not already listed.
- Firestore Database: create the database in production mode, then publish the included rules.

Admin accounts are hard-coded in both the app and Firestore rules:
- `mhmd1212@gmail.com`
- `mhmdhaffi42@gmail.com`

Change the admin email list in both `auth.js`/`dashboard.js` and `firestore.rules` if different admins are needed.

## Data Model
- `users/{uid}`: profile and role.
- `projects/{projectId}`: customer website request, accepted developer, status, and chat ID.
- `chats/{chatId}`: project chat metadata and participants.
- `chats/{chatId}/messages/{msgId}`: text messages and optional attachment metadata.
- Chat attachments are saved as small Firestore data URLs inside message documents.

## Run Locally
Serve this folder as static files, for example:

```bash
npx serve /home/deathmaster/Desktop/al-madeena-tajweed-center
```

## Deploy
From this folder:

```bash
firebase login
firebase deploy
```

If you only want to publish rules first:

```bash
firebase deploy --only firestore:rules
```

If you only want to publish hosting:

```bash
firebase deploy --only hosting
```
