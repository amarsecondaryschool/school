# UPDATE – New design + Phase 2 (read this, it is short)

## What changed
1. **Opening the link in a browser now shows ONLY a "Download App" button.** The real app opens only after it is installed on the phone. (For testing in a browser, add `?app=1` to the end of the link, e.g. `https://tilakpanday2019-wq.github.io/amar-school/?app=1`.)
2. **New design** in the style of your reference screenshots: light background, blue header card with photo, "Additional Information", "Quick Access" cards, blue bottom bar with a round school logo in the middle. The logo, name and icons are Amar Secondary School's own, not the other app's.
   - **Student** (parent login) home: child's photo, class, roll, regd. no., guardian, contact, address, house, blood group, EMIS, then cards: Teachers, Homework, Attendance, Examination, Exam Routine, Account, Library, Calendar, TimeTable, Inbox.
   - **Teacher** home: photo, Teacher ID, assigned classes/subjects, then cards: My Classes, Student Records (read-only, only their own classes), Attendance, Marks Entry, Homework, Class Routine, Notices, Calendar, Staff Leave.
   - **School** (admin) home: totals, then all 19 management cards.
   - The ⋮ menu (top right) has the language switch and Log out.
3. **Phase 2 added:** student and teacher **photos**, student **House** and **EMIS** fields, student **status filter**, **Promote students** to the next class (the ⬆ button on Student Records), and the parent's **Teachers** screen (teachers of their child's class and their subjects).

Cards marked **Soon** are not built yet (attendance, marks, homework, fees, etc.). They are honest placeholders, not fake data.

## How to update (about 10 minutes)
### A. Database – run one more SQL file
Supabase → **SQL Editor** → **New query** → paste the whole of `4_phase2.sql` → **Run**. Run it **once**. (Run it AFTER files 1, 2, 3.) If you see a red error, send me the exact text.

### B. GitHub – replace the files
In your `amar-school` repository, replace these 8 files with the new ones. For each: open the file → pencil icon → select all → delete → paste the new content → **Commit changes**. (For `.png` images use **Add file → Upload files** and drop the new images; they replace the old ones.)
`index.html` (unchanged, skip), **`app.js`**, **`strings.js`**, **`styles.css`**, **`sw.js`**, **`manifest.webmanifest`**, **`icon-192.png`**, **`icon-512.png`**
`config.js` already has your values and is **unchanged**. Do not replace it with a different copy that has `YOUR_...` in it.
Easiest: unzip `amar-school-web.zip` on a computer, then on GitHub use **Add file → Upload files** and drag in `app.js`, `strings.js`, `styles.css`, `sw.js`, `manifest.webmanifest`, `icon-192.png`, `icon-512.png`. Commit.

### C. On the phone
1. If the old app is installed: **uninstall it** (long-press the icon → Uninstall), so the new icon and design are picked up.
2. Open `https://tilakpanday2019-wq.github.io/amar-school/` in **Chrome**.
3. Tap **Download App**. Chrome asks to install → **Install**. If nothing appears, tap ⋮ at the top right of Chrome → **Install app**.
4. Open "Amar School" from the home screen.

## Honest limits
- Android does not allow any website link to install an app with **zero** taps. The Download App button gets it to one tap on "Install". A real downloadable APK file needs a separate tool (PWABuilder) later.
- This code was tested in a browser with a stand-in database, **not** against your real Supabase. The new SQL (`4_phase2.sql`) has **not** been run against a real project. Send me any error you see.
- Photos are stored privately in Supabase Storage (free tier has a storage limit). Each photo is shrunk to about 500 pixels before upload.

## Phase 2 – how to use
- **Student photo / House / EMIS:** School → Student Records → ＋ Add student (or tap a student to edit). Pick a photo in the first field.
- **Teacher photo:** School → Teacher Records → tap a teacher → 📷 Change photo.
- **Promote:** School → Student Records → ⬆ → choose "from" and "to" class → Promote. All ACTIVE students move; sections are matched by name (A→A); roll numbers are cleared so you can set them again.
- **Parent Teachers screen:** works after you assign teachers to classes and link the parent to a student.
