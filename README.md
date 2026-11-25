# Break Board

Staff break tracker with a personal login for every staff member.

- **Staff** sign in with their own username and PIN, see only their own card, start and end their own breaks, and can change their PIN.
- **Admin** signs in with email and password and sees every staff member: live board, per-person report, full break log, CSV download, and Setup (add or remove staff, break types).

Hosted on GitHub Pages. Data is stored in Firebase (free plan).

## Update an existing setup (3 steps)

### 1. Publish the new rules
1. Firebase → **Build → Firestore Database → Rules**.
2. Delete everything and paste the contents of `firestore.rules` (the admin email `mytabonepluse@gmail.com` is already filled in).
3. Tap **Publish**.

### 2. Replace the files on GitHub
In the repository `staff-login`: delete the old `index.html` and `README.md`, then **Add file → Upload files** and upload the new `index.html`, `README.md` and `firestore.rules`. Keep your existing `config.js`. Wait one minute, then reload the site.

### 3. Add your staff
Sign in as admin → **Setup → Staff logins**. For each person enter name, username (for example `priya`) and a PIN of 6 or more characters, then tap **Add**. To add many at once, use **Add many staff at once** and paste one line per person: `Name, username, PIN`. Tell each person their username and PIN. The old test staff "Habeen" can be removed there.

## Daily use
- Staff open the link, sign in, tap **Start break**, choose a type, and tap **End break** when done.
- Admin signs in and uses **Board** (who is on break now), **Report** (dates, per person totals, over-time, CSV) and **Setup**.

## Forgot a PIN
Firebase → **Authentication → Users** → delete that user. Then in **Setup** add the person again with the same username and a new PIN.

## Notes
- Staff usernames are stored as `username@breakboard.example.com`. These are not real mailboxes.
- Rules guarantee a staff member can read and write only their own breaks. The admin email in the rules is the only admin.
- For a first-time setup from scratch, create the Firebase project, Firestore and Email/Password sign-in, add the admin user, then copy the web app settings into `config.js`.

## New in this version
- **Dark teal theme.** A Theme button (top right) switches Dark, Light and Auto. Each phone remembers its own choice.
- **Break limits.** In Setup, set "Max/day" for each break type (0 = no limit) and "Most staff on break at once". The admin board warns when too many are out together.
- **Reminders.** Staff get a popup 2 minutes before their break ends, and admin and staff get an over-time popup.
- **Forgot to end?** Breaks more than 60 minutes over their limit are flagged.
- **Edit a break.** In Report, tap Edit on a finished break to fix its start and end times.
- **Report chart.** Bars per person (red = over time) and a "Needs attention" line.
- **Add many staff.** Up to 100 per paste. There is no limit on total staff.

Remember to publish the updated `firestore.rules` (it now lets the admin edit a break).
