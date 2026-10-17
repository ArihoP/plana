# Turn on sign-in and sync for PLANA

PLANA stores each person's bookings, deliveries and pose photos in their own account, so they appear on every device after signing in. This uses Firebase, which is free for this amount of use. Do these steps once.

## 1. Create the Firebase project
1. Go to https://console.firebase.google.com and sign in with your Google account.
2. Choose **Create a project**, name it `plana`, and finish the steps. You can switch Google Analytics off.

## 2. Turn on email sign-in
1. In the left menu choose **Build**, then **Authentication**, then **Get started**.
2. Under **Sign-in method**, choose **Email/Password**, switch on the first toggle, and press **Save**.
3. Open the **Settings** tab, then **Authorized domains**, then **Add domain**. Type your Vercel address without `https://`, for example `plana-ug.vercel.app`, and add it.

## 3. Create the database
1. In the left menu choose **Build**, then **Firestore Database**, then **Create database**.
2. Pick the location closest to you and choose **Start in production mode**.
3. Open the **Rules** tab, delete what is there, paste in the contents of the `firestore.rules` file from this folder, and press **Publish**.

## 4. Copy the settings into PLANA
1. Press the gear icon next to **Project Overview**, then **Project settings**.
2. Under **Your apps**, press the web icon `</>`, name the app `plana`, and register it. Skip hosting.
3. You will see a block of settings. Copy the four values `apiKey`, `authDomain`, `projectId` and `appId`.
4. On GitHub, open `firebase-config.js` in your Plana repo, press the pencil icon, paste each value between its quotes, and commit.
5. Vercel redeploys on its own. Open PLANA, create an account with your email, and you are in.

These settings are not secret. The rules in step 3 are what keep each person's data private.

## Notes
- Anyone with the link can create an account, and each account only ever sees its own data.
- Bookings saved on a phone before you signed in can be added to your account. PLANA offers this after your first sign-in.
- Pose photos are saved inside your account. Each photo is shrunk to keep it small.
