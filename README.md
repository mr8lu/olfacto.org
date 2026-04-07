# Olfacto | Sensory Data Infrastructure

A high-fidelity, Bauhaus × Material Design 3 (M3) landing page for Olfacto.org. This project serves as the parent holding company site for the Nez sensory mapping ecosystem.

## Features
- **Dynamic Theming:** Automatically switches between Light and Dark mode based on system preferences.
- **Interactive Visualization:** A mathematically accurate 5-axis radar graph that morphs to represent live sensory data mapping.
- **Waitlist Integration:** Direct connection to Firebase Cloud Firestore for secure email capture.
- **Enterprise Security:** Protected by Firebase App Check and reCAPTCHA Enterprise to prevent bot spam.
- **Optimized SEO:** Full Open Graph (Instagram/LinkedIn) and Twitter Card support.

## Tech Stack
- **Frontend:** Vanilla HTML5, CSS3 (Modern Flex/Grid), and ES6+ JavaScript.
- **Backend-as-a-Service:** Firebase Firestore.
- **Security:** Firebase App Check + reCAPTCHA Enterprise.

---

## 🛠 Setup & Configuration

### 1. Firebase Credentials
Open `index.html` and locate the `firebaseConfig` object at the bottom of the file. Replace the placeholders with your actual keys from the **Firebase Console > Project Settings**:
```javascript
const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "olfacto-org.firebaseapp.com",
    projectId: "olfacto-org",
    storageBucket: "olfacto-org.firebasestorage.app",
    messagingSenderId: "...",
    appId: "...",
    measurementId: "..."
};
```

### 2. reCAPTCHA Site Key
Locate the `recaptchaSiteKey` variable in `index.html` and ensure your reCAPTCHA Enterprise Site Key is present:
```javascript
const recaptchaSiteKey = "6Lex5qssAAAAAA9y_ahpdadsSKjplb9Pd-FuaGCF";
```

### 3. Firestore Security Rules
In your Firebase Console, navigate to **Firestore > Rules** and publish the following to allow secure submissions:
```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /waitlist/{document=**} {
      allow create: if true;
      allow read, update, delete: if false;
    }
  }
}
```

---

## 🚀 Deployment to GitHub Pages

1. **Create a Repository:** Create a new repository on GitHub (e.g., `olfacto-org`).
2. **Push Code:**
   ```bash
   git init
   git add .
   git commit -m "Initial launch"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/olfacto-org.git
   git push -u origin main
   ```
3. **Enable Pages (via GitHub Actions):**
   - Go to your repo on GitHub.
   - Click **Settings** > **Pages**.
   - Under **Build and deployment**, change the **Source** dropdown to **GitHub Actions**.
   - The included `.github/workflows/deploy.yml` will now automatically deploy your site every time you push to `main`!

Your site will be live at `https://YOUR_USERNAME.github.io/olfacto-org/` within minutes.

## 🎨 Branding Note
- **Favicon:** The branded favicon is located at `/favicon.svg`.
- **Social Preview:** To update the social share image, replace `/og-image.png` with a 1200x630px screenshot of the site.
