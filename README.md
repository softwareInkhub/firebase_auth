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
4. In `index.html`, replace the placeholders in `firebaseConfig` with your project's values:

```js
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT_ID.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID",
};
```

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
- Some browsers or extensions can block third-party scripts or cookies; try an incognito window or a different browser.

## 4) Deploy
Host the files on any static hosting (e.g., Firebase Hosting, Vercel, Netlify, GitHub Pages). Make sure the deployed domain is added to Authorized domains. 