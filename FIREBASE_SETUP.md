# Firebase Setup Guide for IBM Bob Projects

## Step 1: Create Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Add project" or "Create a project"
3. Enter project name: `ibm-bob-projects` (or any name you prefer)
4. Click "Continue"
5. Disable Google Analytics (not needed) or keep it enabled
6. Click "Create project"
7. Wait for project creation, then click "Continue"

## Step 2: Create Realtime Database

1. In the left sidebar, click "Build" → "Realtime Database"
2. Click "Create Database"
3. Select location: Choose closest to you (e.g., `us-central1`)
4. Click "Next"
5. **Security Rules**: Select "Start in test mode" (we'll secure it later)
6. Click "Enable"

## Step 3: Get Firebase Configuration

1. Click the gear icon (⚙️) next to "Project Overview" in the left sidebar
2. Click "Project settings"
3. Scroll down to "Your apps" section
4. Click the web icon `</>` to add a web app
5. Enter app nickname: `IBM Bob Projects`
6. **DO NOT** check "Also set up Firebase Hosting"
7. Click "Register app"
8. Copy the `firebaseConfig` object - you'll need these values:
   ```javascript
   const firebaseConfig = {
     apiKey: "AIza...",
     authDomain: "your-project.firebaseapp.com",
     databaseURL: "https://your-project.firebaseio.com",
     projectId: "your-project",
     storageBucket: "your-project.appspot.com",
     messagingSenderId: "123456789",
     appId: "1:123456789:web:abc123"
   };
   ```
9. Click "Continue to console"

## Step 4: Set Up Security Rules (Important!)

1. Go back to "Realtime Database" in the left sidebar
2. Click the "Rules" tab
3. Replace the rules with:
   ```json
   {
     "rules": {
       "links": {
         ".read": true,
         ".write": "auth != null"
       }
     }
   }
   ```
4. Click "Publish"

This allows:
- ✅ Anyone can READ links (view mode)
- ✅ Only authenticated users can WRITE (admin mode)

## Step 5: Enable Authentication

1. In the left sidebar, click "Build" → "Authentication"
2. Click "Get started"
3. Click on "Email/Password" provider
4. Enable the first toggle (Email/Password)
5. Click "Save"

## Step 6: Create Admin User

1. Still in Authentication, click the "Users" tab
2. Click "Add user"
3. Enter your email and password (this will be your admin login)
4. Click "Add user"

## Step 7: Update index.html

Open `index.html` and find the Firebase configuration section (around line 420).
Replace the placeholder values with your actual Firebase config:

```javascript
const firebaseConfig = {
    apiKey: "YOUR_API_KEY_HERE",
    authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
    databaseURL: "https://YOUR_PROJECT_ID.firebaseio.com",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_PROJECT_ID.appspot.com",
    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
    appId: "YOUR_APP_ID"
};
```

## Step 8: Deploy and Test

1. Commit and push the updated `index.html` to GitHub
2. Wait 1-2 minutes for GitHub Pages to deploy
3. Visit your site
4. Triple-click the title to enter admin mode
5. Enter your email and password (from Step 6)
6. Try adding/removing links - should work perfectly!

## Troubleshooting

**Issue: "Permission denied"**
- Check that Security Rules are published correctly
- Make sure you're logged in with the admin account

**Issue: "Firebase not defined"**
- Check that you have internet connection (Firebase loads from CDN)
- Check browser console for errors

**Issue: Can't login**
- Verify email/password are correct
- Check that Email/Password authentication is enabled

## Security Notes

- Your Firebase config (API key, etc.) is safe to expose publicly
- The security rules control who can read/write data
- Only authenticated users can modify links
- Anyone can view links (read-only)

## Need Help?

If you encounter issues:
1. Check the browser console (F12) for error messages
2. Verify all Firebase services are enabled
3. Double-check the configuration values