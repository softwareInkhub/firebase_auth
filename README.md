# Firebase Phone OTP Auth (Single Page)

A minimal, single-page web UI for Firebase Phone Number authentication with OTP using the Firebase Web SDK (v9 modular) and invisible reCAPTCHA.

## Features
- Enter phone number in E.164 format (e.g., +15551234567)
- Send OTP via Firebase `signInWithPhoneNumber`
- Enter OTP and verify
- Basic signed-in state with Sign out

## 1) Firebase Setup
1. Create or open a Firebase project in the Firebase Console.
2. Go to Authentication → Sign-in method → Enable "Phone".
3. Go to Project Settings → General → Your apps → Web app → Copy the SDK configuration.
4. Configure your environment file (recommended):
   - Copy `env.example.js` to `env.local.js`
   - Fill in your Firebase SDK config inside `env.local.js`
   - `env.local.js` is git-ignored and loaded automatically by `index.html`

   Alternatively, you can paste the config directly into `index.html` as a fallback, but avoid committing credentials.

5. In Authentication → Settings → Authorized domains, add your local dev domain (e.g., `localhost`), and any domain you will host on.
6. Optionally, add test phone numbers under Authentication → Sign-in method → Phone (helpful during development).

## 2) Run Locally
This page uses the Firebase CDN and can be served as a static file. Avoid opening via `file://` because reCAPTCHA may not work.

- Quick serve with Node.js:

```bash
npx serve -l 5173
```

Then open `http://localhost:5173` in your browser.

Alternatively, use any static server or IDE Live Server.

## 3) Notes & Troubleshooting
- Always include country code (e.g., `+1`, `+91`).
- reCAPTCHA is configured as "invisible" and will auto-trigger when you send the OTP.
- If reCAPTCHA expires, the UI will prompt you to try again.
- Ensure your domain is listed under Authorized domains in Firebase Authentication settings.
- If you see `auth/requests-from-referer-...-are-blocked`, allow your local origin (e.g., `http://localhost:5173/*`) in Google Cloud Console → APIs & Services → Credentials → your API key → HTTP referrers.
- Some browsers or extensions can block third-party scripts or cookies; try an incognito window or a different browser.

## 4) Deploy
Host the files on any static hosting (e.g., Firebase Hosting, Vercel, Netlify, GitHub Pages). Make sure the deployed domain is added to Authorized domains. 