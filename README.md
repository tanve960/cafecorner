# Cafe Corner — QR Food Ordering App

A responsive customer menu + live restaurant order dashboard.

## Features
- Browse menu categories
- Add to cart, quantity controls, customer name, table/takeaway and notes
- Orders saved to Cloud Firestore
- Separate staff dashboard at `/?admin=1`
- Live order updates on the restaurant phone
- Staff can accept, prepare, mark ready, complete or cancel orders
- QR code can point to your deployed customer URL

## 1. Create Firebase project
1. Open https://console.firebase.google.com/ and create a project.
2. Add a Web App and copy its Firebase configuration.
3. In `index.html`, replace the placeholder values in `firebaseConfig`.
4. In Firebase Console → Build → Firestore Database, create a database.
5. In Firestore → Rules, paste the contents of `firestore.rules` and publish.
6. In Firebase Console → Authentication → Sign-in method, enable **Email/Password**.
7. In Authentication → Users, add a staff account with an email and password. Use this account on the restaurant phone.

The Firestore rules allow anyone to submit a new order, but only signed-in users can read or update orders. Keep the staff login private. For a commercial launch, add App Check, server-side validation/rate limiting, and staff role authorization (the starter rules allow any authenticated Firebase user to read/update orders).

## 2. Test locally
You can open `index.html` in a browser after adding Firebase config. If browser module restrictions interfere, use VS Code Live Server.

## 3. Publish with GitHub + Vercel
1. Create a GitHub repository named `cafe-corner`.
2. Upload `index.html` and `firestore.rules` (README is optional).
3. In https://vercel.com/ choose **Add New → Project**, import the GitHub repository.
4. Framework preset: **Other**. Build command: leave blank. Output directory: `.` (or leave default if Vercel detects static files).
5. Deploy. Your site will receive a public `https://...vercel.app` URL.

## 4. Make the QR code
Generate a QR code that contains your deployed Vercel URL (the normal customer URL, without `?admin=1`). Print it and place it on each table. You can use a QR generator such as https://www.qrcode-monkey.com/.

## 5. Restaurant phone
Open `https://YOUR-VERCEL-URL.vercel.app/?admin=1`, sign in with the Firebase staff account, and keep the dashboard open. Incoming orders appear automatically.

## Important menu note
Menu names and prices were transcribed from the two uploaded menu images. Please review spelling, size labels and prices before publishing; a few source-image entries are visually ambiguous. The app uses the listed single/half/full options as separate cart items.
