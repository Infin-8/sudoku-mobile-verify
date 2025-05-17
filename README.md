# Sudoku Mobile Verification Redirect

This repository contains the verification redirect page for Sudoku Mobile app. When users click on the verification link in their email, they are redirected to this page which then redirects them to the mobile app with the verification parameters.

## Why Is This Needed?

Appwrite requires a publicly accessible URL for email verification, so we need a web page that can:
1. Receive the verification parameters from Appwrite
2. Redirect the user back to the mobile app via deep linking

## Deployment Instructions

### Option 1: Deploy to Netlify (Recommended)

1. Create a free Netlify account at [netlify.com](https://netlify.com)
2. Install the Netlify CLI: `npm install -g netlify-cli`
3. Login to Netlify: `netlify login`
4. Deploy this directory:
   ```bash
   cd /path/to/verification-redirect
   netlify deploy --prod
   ```
5. When prompted, select "Create & configure a new site"
6. Choose your team and name the site (e.g., "sudoku-mobile-verify")
7. The site will be deployed to a URL like `https://sudoku-mobile-verify.netlify.app`

### Option 2: Deploy to GitHub Pages

1. Create a new repository on GitHub named `sudoku-mobile-verify`
2. Push this directory to the repository
3. Enable GitHub Pages in the repository settings
4. Select the branch and folder to deploy

### Option 3: Deploy to Firebase Hosting

1. Install Firebase CLI: `npm install -g firebase-tools`
2. Login to Firebase: `firebase login`
3. Initialize Firebase: `firebase init hosting`
4. Deploy: `firebase deploy --only hosting`

## After Deployment

1. Update the redirect URL in the app:
   - In `app/index.jsx`: Update the `baseUrl` variable with your deployed URL
   - In `components/WarningMessage.jsx`: Update the `redirectUrl` variable with the same URL

2. Test the verification flow:
   - Register a new account in the app
   - Check your email for the verification link
   - Click the link and verify that you're redirected to the app

## Troubleshooting

If users are experiencing "Safari cannot connect to the server" errors:
1. Make sure your redirect URL is publicly accessible
2. Ensure your app has the correct URL scheme registered (`sudokumobile://`)
3. Test the verification flow on both iOS and Android devices

If the redirect doesn't work on specific platforms:
1. Check the console logs in your browser for errors
2. Review the URL parameters to ensure they're being passed correctly
3. Make sure your app manifest has the correct scheme configuration
