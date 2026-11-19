# Long Jump Strength Program website: setup steps

Files:
- `index.html`: the website (the only file the site needs)
- `supabase-setup.sql`: sets up the database (run once in Supabase; don't upload to GitHub)
- `README.md`: these instructions

## Before you start
1. Delete old attempts: Vercel project > Settings > Delete Project. GitHub repository > Settings > Delete this repository.
2. Clear old `index` files out of your Downloads folder.
3. Windows: in File Explorer turn on View > Show > File name extensions.
4. After downloading, the page file must be named exactly `index.html` (not `index (1).html`, not `index.html.txt`). Rename it if needed.

## Supabase
If Table Editor already shows `exercises` and `lift_logs`, skip to step 9 (running the SQL again duplicates the workouts).
5. Log in at supabase.com and open the project (or New project).
6. Open `supabase-setup.sql` in Notepad. Replace CHANGE-ME-TEAM-CODE with your team code (keep the quotes). Save.
7. Supabase > SQL Editor > New query > paste the whole file > Run.
8. Table Editor should show `exercises` (46 rows) and `lift_logs` (empty).
9. Click Connect at the top of the project. Copy the Project URL and the publishable key (starts with `sb_publishable_`). Never use a key starting with `sb_secret_`.

## Add Supabase to the page
10. Right-click `index.html` > Open with > Notepad. Ctrl+F, search SUPABASE CONFIG.
11. Paste between the quotes:
        const SUPABASE_URL = "https://yourproject.supabase.co";
        const SUPABASE_PUBLISHABLE_KEY = "sb_publishable_xxxxx";
12. Save (Ctrl+S). Make sure the file is still named `index.html`.

## GitHub
13. github.com > + > New repository > name `long-jump-program` > Public > Create repository.
14. Click "uploading an existing file". Drag in `index.html` and `README.md` (NOT the SQL file). Commit changes.
15. The file list must say exactly `index.html`. If not: click the file > pencil icon > fix the name > Commit changes.

## Vercel
16. vercel.com > Add New > Project > Import `long-jump-program`.
17. Framework Preset: Other. Change nothing else. Deploy.
18. Continue to Dashboard > click Visit. Use that link.

## Test
19. Workouts and "Watch demo video" links show.
20. Log a lift with test initials and the team code > "Lift saved."
21. Supabase > Table Editor > lift_logs shows the entry. Delete it.

## Troubleshooting
- Page not found: the GitHub file isn't named exactly `index.html` (step 15).
- No "Log a lift" section: URL or key in step 11 is mistyped or missing quotes.
- "Lift not saved": team code doesn't match step 6.

## Changing things later
- Workouts: edit rows in Supabase's `exercises` table; the site updates on refresh.
- Page text/design: edit `index.html` on GitHub; Vercel redeploys automatically.
- Athlete logs: Supabase > Table Editor > lift_logs (export as CSV from there).
