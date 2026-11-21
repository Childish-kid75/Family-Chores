# Family Chores

A tiny website where family members sign in with Google and add chores from their phones.
Hosted free on GitHub Pages. Data lives in Firebase Firestore (free Spark plan).

## How it fits together
- `index.html`: the whole site (HTML, CSS, JavaScript). Runs in the browser.
- `firestore.rules`: the lock. Only the Gmail addresses listed in it can read or write chores.
- Firebase config in `index.html` is NOT a secret. The rules are what protect your data.

## Setup (about 20 minutes)

### 1. Create the Firebase project
1. Go to https://console.firebase.google.com and click **Add project** (skip Google Analytics).
2. **Build > Authentication > Get started > Sign-in method > Google > Enable**, pick a support email, save.
3. **Build > Firestore Database > Create database**. Choose a nearby region (e.g. `europe-west1` or `africa-south1` if offered), start in **production mode**.
4. Open the **Rules** tab, paste the contents of `firestore.rules`, put in your family's real Gmail addresses, click **Publish**.
5. **Project settings (gear icon) > Your apps > Web (</>)**, register an app, and copy the `firebaseConfig` values.
6. Paste them into `index.html` where it says `PASTE_HERE`.

### 2. Put it on GitHub
1. Create a new repository on GitHub (e.g. `family-chores`), public is fine.
2. Upload `index.html`, `firestore.rules` and `README.md` (or use git: `git init`, `git add .`, `git commit -m "first version"`, `git remote add origin <url>`, `git push -u origin main`).
3. Repo **Settings > Pages > Source: Deploy from a branch > main / (root) > Save**.
4. After a minute your site is at `https://YOUR-USERNAME.github.io/family-chores/`.

### 3. Allow the site to sign in
Firebase console > **Authentication > Settings > Authorized domains > Add domain**: `YOUR-USERNAME.github.io`.

### 4. Share
Send the link to your family. They tap **Sign in with Google** (must be an address in the rules file).

## Things to learn from this project
- git: commit, push, and watch GitHub Pages redeploy.
- How a page talks to a database (`onSnapshot` = live updates).
- Security rules: why client-side code alone can't keep data private.

## Ideas for later
- XP points per chore (ties into your habit app).
- Push the chores into Google Calendar automatically.
