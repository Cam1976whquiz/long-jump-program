# Jumps Lab app: setup

This adds the Jumps Lab app to the website you already have. Nothing existing changes:
- GitHub: you ADD one file, `app.html`. Leave `index.html` and `README.md` alone.
- Supabase: the SQL adds new tables that start with `jl_`. Your `exercises` and `lift_logs` tables are untouched.
- Vercel: nothing to set up. It redeploys on its own when you add the file.

When you're done, the app lives at: `https://YOUR-SITE.vercel.app/app.html`

## Step 1: Supabase tables (5 minutes)
1. Open `jumps-app-setup.sql` in Notepad.
2. Find `CHANGE-ME-TEAM-CODE` and replace it with the team code athletes will type once (example: `Demons2027`). Keep the single quotes.
3. Find `coach@example.com` and replace it with the email you'll sign in with as coach. Keep the single quotes.
4. Save the file.
5. Supabase > your project > SQL Editor > New query > paste the whole file > Run. You should see "Success."
6. Table Editor should now show new tables: jl_checkins, jl_coaches, jl_jumps, jl_roster, jl_sets, jl_settings, jl_speed, jl_tests.

## Step 2: Make your coach login (2 minutes)
1. Supabase > Authentication > Users > Add user > Create new user.
2. Email: the SAME email you put in step 1.3. Pick a password. Check "Auto Confirm User" if it's offered.
3. Click Create user.

## Step 3: Add your keys to app.html (2 minutes)
1. Make sure the downloaded file is named exactly `app.html` (not `app (1).html`). Rename it if needed.
2. Right-click `app.html` > Open with > Notepad. Ctrl+F, search SUPABASE CONFIG.
3. Paste the same Project URL and publishable key that are in your index.html, between the quotes:
       const SUPABASE_URL = "https://yourproject.supabase.co";
       const SUPABASE_PUBLISHABLE_KEY = "sb_publishable_xxxxx";
4. Save (Ctrl+S).

## Step 4: Add it to GitHub (2 minutes)
1. Open your existing repository (long-jump-program) on github.com.
2. Add file > Upload files > drag in `app.html` > Commit changes.
3. Check the file list: you should see `index.html`, `README.md` AND `app.html`.
4. Vercel redeploys automatically in about 30 seconds.

## Step 5: Set up the team (10 minutes)
1. Open `https://YOUR-SITE.vercel.app/app.html` on your phone or computer.
2. Tap Coach > sign in with the email and password from step 2.
3. Roster: add each athlete with grade and event group. Use first name + last initial (example: "Avery B").
4. Maxes: enter each athlete's tested weight and pick 3RM, 5RM or 1RM. Weights calculate automatically.
5. Set the current week at the top of the Coach view.
6. Make a QR code of the app link for the weight room wall (any free QR generator works).

## Athletes, first time
1. Scan the QR code or open the link.
2. Type the team code once.
3. Tap their name. The phone remembers them after that.
4. Optional: Add to Home Screen (iPhone: Share > Add to Home Screen; Android: menu > Add to Home screen).

## Quick test
1. As an athlete: check in, save one set, save one jump.
2. As coach: Refresh. The check-in shows in Attendance, the jump in Jump board.
3. Supabase > Table Editor > jl_checkins and jl_sets show the rows. Delete test rows when done.
4. Open your main site (index.html link). It should look and work the same as before.

## Troubleshooting
- "Almost ready" screen: the URL or key in app.html is blank or missing its quotes.
- "That code didn't work": the code doesn't match what's in the SQL (it's case-sensitive). To change it, edit the code in section 1 of the SQL and run only the `create or replace function public.jl_team_ok()` statement again.
- "This account isn't on the coach list": the login email doesn't match the email in jl_coaches. Fix it in Table Editor > jl_coaches.
- Page not found: the GitHub file isn't named exactly `app.html`.
- Didn't save: check the phone's connection and try again.

## Where your data lives
Supabase > Table Editor:
- jl_roster: athletes, groups, maxes
- jl_checkins: attendance (name via athlete_id, date, week, day, group)
- jl_sets: every saved set
- jl_jumps, jl_speed, jl_tests: jumps, sprints and plyo contacts, test results
Each table can be exported as CSV from the Table Editor.

## Undo
- To take the app offline: delete `app.html` from GitHub. Your main site keeps working.
- Removing an athlete in the Coach view hides them but keeps their data.
