# Break Board

Staff break tracker. Staff tap Start break, pick a type or a custom time, and a live timer counts up. Admins sign in to see reports, the break log, CSV download and staff setup.

Hosted on GitHub Pages. Data is stored in Firebase (free plan). Staff need no account.

## Setup (about 15 minutes)

### 1. Create the Firebase project
1. Open https://console.firebase.google.com and sign in with Google.
2. **Create a project** (or **Add project**), name it `break-board`, turn Google Analytics off, then **Create**.

### 2. Create the database
1. In the left menu choose **Build → Firestore Database → Create database**.
2. Pick a location near you (for India: `asia-south1`), choose **production mode**, then **Enable**.

### 3. Publish the rules
1. In Firestore, open the **Rules** tab.
2. Delete everything there and paste the contents of `firestore.rules`.
3. Replace `YOUR_ADMIN_EMAIL@example.com` with your admin email, in lowercase. Add more admins like `['a@x.com','b@x.com']`.
4. Tap **Publish**.

### 4. Create the admin login
1. Choose **Build → Authentication → Get started**.
2. Under **Sign-in method**, enable **Email/Password**, then **Save**.
3. Open the **Users** tab, tap **Add user**, and enter the same admin email and a strong password.
4. Under **Settings → Authorized domains**, add `mytabonepluse-cyber.github.io`.

### 5. Connect the app
1. Tap the gear next to **Project Overview → Project settings**.
2. Under **Your apps**, tap the web icon `</>`, name it `break-board`, and register it (skip Hosting).
3. Copy `apiKey`, `authDomain`, `projectId` and `appId` from the settings shown.
4. In this GitHub repo, open `config.js`, tap the pencil, paste the four values between the quotes, and **Commit changes**.

### 6. Use it
Open https://mytabonepluse-cyber.github.io/break-board/ . Tap **Admin login**, sign in, open **Setup**, and add your staff. Share the same link with staff.

## Who can do what
- **Everyone with the link:** see staff names and who is on break, start and end breaks.
- **Admins (signed in):** also see the Report, the break log, CSV download and Setup.
- The break log is protected by the rules: only admins can read it.
- There is no staff login. Anyone with the link can start or end anyone's break, so share it only with your team.
