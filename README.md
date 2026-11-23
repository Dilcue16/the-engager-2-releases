**Download:** open [Releases](https://github.com/Dilcue16/the-engager-2-releases/releases/latest) and get **TheEngager2-Setup.exe** and double-click it (one-click install; if Windows says 'Windows protected your PC', click More info, then Run anyway) - or **TheEngager2-portable.zip** and follow *Safe download: step by step* below.

# How to Use The Engager 2

This is a step-by-step guide for team members. Read **[DISCLAIMER.md](DISCLAIMER.md)** first: automating Facebook can put your account at risk.

## What the app does

You paste one or more PRO3 LCS Google Form links. For each form, the app:
1. reads the Facebook posts listed in the form
2. **likes**, **comments on** and **shares** each post from your own Facebook account, with your approval
3. takes a screenshot of each completed action as proof
4. optionally attaches the screenshots to the form and submits it, again with your approval

**The app is free.** It needs no paid service or API key, and no AI.

Every action is checked on the page. If Facebook doesn't show it, it is not counted as done. A post is never liked, commented on or shared twice.

---

## Easiest: the portable version (nothing to install)

### Safe download: step by step

1. **Get the fingerprint first, from the team chat.** The maintainer posts each release's SHA-256 fingerprint there. It is a second, separate place from GitHub: if someone tampered with GitHub, the chat copy still exposes it.
2. **Download only from the official download page:** https://github.com/Dilcue16/the-engager-2-releases/releases/latest (no GitHub account needed). Download **TheEngager2-portable.zip**. Never use a copy forwarded by Messenger, email, Drive or USB.
3. **Check and unzip it with one line (about 1 minute).** In File Explorer, open the Downloads folder, type `powershell` in the address bar and press Enter. Paste the line from the release notes and press Enter. It checks the fingerprint (**GENUINE** / **NOT GENUINE**), unblocks the ZIP, unzips it to your user folder (`C:\Users\<you>\TheEngager2`) and opens that folder. Also make sure the fingerprint in that line is the same as the team-chat one. If it says NOT GENUINE, delete the ZIP and tell the maintainer.
4. **Don't use right-click → Extract All.** With this many files it can take an hour or more.
5. **Keep the folder local.** Do **not** move it to OneDrive, Google Drive, a cloud-synced Desktop/Documents, a USB stick or Program Files: it will hold your Facebook and Google sign-ins.
6. **Keep the ZIP** (rename it, e.g. `TheEngager2-v1.2.0.zip`) until the next version works, so you can go back if needed.
7. Open the folder and double-click **Start The Engager 2.bat**. The first time, it asks you to sign in to Facebook and Google (close that browser window when done) and adds a **The Engager 2** shortcut to your Desktop; from then on, just use the shortcut.
8. Each start: The app opens in your browser through a **private link** that works only for that window; if you ever see "Open the dashboard from the app", close the tab and start the .bat again. Keep the black window open while you work; close it to stop the app.
9. Continue with **Part 2, step 2** below.

**Protect the PC:** keep Windows Security (Defender) on and never add an exclusion for the app folder; turn on **BitLocker** (Settings → Privacy & security → Device encryption / BitLocker, free on Windows 11 Pro); use 2-step verification on Facebook, Google and GitHub. On a shared PC, use the dashboard's **Erase** and sign out of Facebook when you finish.

If Windows says **"Windows protected your PC"**, click **More info → Run anyway**. Python and its browser are already inside the folder, and nothing is installed on the PC. To move to another PC, copy the whole folder, but **first delete `app\data\browser-profile` from the copy**: it holds your live Facebook and Google sign-ins, which must never travel on a USB stick or a shared drive. Then run **Sign in.bat** on the new PC. The update button works the same way (see Part 3).

**Signing in later:** click **Sign in** at the top of the app (or **Sign in.bat**). One window opens with Facebook and Google: sign in to YOUR accounts, finish any security check yourself, then CLOSE that window. The app notices it closed and shows ✓ next to each account. New users see a **Get started** checklist (Sign in → Your details → Test run) until all three are done. Some Google Forms only accept people signed in to Google: if a run stops with "Google sign-in required", click **Sign in**, sign in to Google, close the window, then run the Test again.

**Use ONE copy of the app.** Every copy has its own sign-ins, details and history, so a second copy looks like "the app forgot my sign-in". To avoid that:
1. Unzip once to a fixed place, e.g. `C:\Users\<you>\TheEngager2`, not inside Downloads (Downloads and temporary folders get cleaned up).
2. Update only with the green **Update now** bar. Downloading the ZIP again makes a NEW copy, signed out, with empty details.
3. Start it from the **The Engager 2** shortcut on your Desktop.
4. Sign in only with the app's **Sign in** button, never in your everyday Chrome: the app has its own browser.

The top of the app shows **This copy: … · version · Facebook: …**. If another copy is found on the PC, or the app runs from Downloads, an orange note says where, and how to move it once. The app never moves or deletes a copy itself.

---

## Part 2: Each time you use it

### 1. Start the dashboard
Open PowerShell in the app folder and run:
```powershell
.venv\Scripts\activate
python -m taskpilot dashboard
```
Your browser opens **http://127.0.0.1:8765**. Keep the PowerShell window open while you use the app.

### 2. Fill in Your details (first time only)
Under **Your details**, enter your **Rank**, **Full name** (LAST, FIRST M.I.), **Unit / PPO** and **Sub-unit**, then click **Save details**.

These are the answers typed into the form, so check them carefully. They are stored encrypted on your PC.

The **Facebook profile link** field is optional. If you leave it blank, the app remembers the account you use on your first run. After that, it stops if a different Facebook account is signed in.

### 3. Set up a new run
In **New run**:

| Field | What to enter |
|---|---|
| **Google Form links** | The form links, one per line |
| **Comment** | The comment to post on each post |
| **Hashtags** | Your hashtags, for example `#tag1 #tag2`. They are added to the end of the comment. |
| **Like / Comment / Share** | Tick the actions you want |

Options:
- **Test only**: opens the posts and finds the buttons, but clicks nothing. **Use this on your first run** to make sure everything works.
- **Approve each form at once**: gives you one approval card per form, instead of one card per post.
- **Auto-upload & submit**: after the posts are done, attaches the screenshots to the form and submits it. You approve both steps.
- **Erase upload folder after submit**: deletes the screenshot folder once the form is submitted and verified. The original screenshots stay in `evidence/`.

Click **Start run**.

### 4. Pre-flight check
Before anything is clicked, the app checks that:
- your own Facebook account is signed in
- Your details are filled in
- every post opens

If any check fails, the run **stops and nothing is done**. The **Activity** log tells you why.

### 5. Approve the actions
Cards appear under **Approvals**. Read each card, then click **Approve** or **Reject**. Nothing happens without your approval.

### 6. Watch the results
- **Run details** and **Activity** show each step as it happens. **Clear log** empties the log. Your history of completed actions is kept, so duplicate protection still works.
- Results mean the following:
  - **completed**: verified on the post
  - **duplicate**: already done before, so it was skipped
  - **unverified** or **failed**: check the post by hand
- **Upload folders** lists the screenshots saved for each form.
  - Use **Open folder** to upload them yourself if you didn't use Auto-upload.
  - Use **Delete** or **Delete all** when you're finished.

### 7. Finish
Close the browser tab, then press **Ctrl + C** in PowerShell to stop the app.

---

## Part 3: Updating the app

The app checks for a new version by itself when the dashboard opens. When one is available, a
green bar appears at the top: click **Update now**. The app restarts by itself, and the dashboard
page reloads. (You can also click **Check for updates** in the **App updates** card.) No GitHub
account or sign-in is needed, and it works even while the app's browser window is open.

- **On v1.2.6 or older?** Those versions look for updates in a place other users cannot reach.
  Download the newest **TheEngager2-portable.zip** once from the download page, unzip it, and copy
  your old `app\data` folder into the new one. After that, updates are one click.

- **Kept:** your settings (`config.yaml`), your details, `data/`, `evidence/`, `reports/` and
  upload folders are never changed.
- **Backed up:** files that get replaced are saved first in `data/update/backup-….zip`.
- **Signed:** an update is installed only if it matches its fingerprint **and** carries the
  maintainer's signature. If the app says an update is "not signed", don't install anything by
  hand; tell the maintainer.
- **Installed with git clone?** The update uses `git pull`. If you changed the code yourself,
  the app won't update. Update it with git instead.
- You can't update while a run is in progress.
- **Older copy without the App updates card?** Download the ZIP once more (from the Releases page) and
  unzip it over your old folder. Your settings and data are kept. After that, use the button.

## Tips and common problems

| Problem | What to do |
|---|---|
| "running scripts is disabled" when you activate | Run `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned` once, then try again. |
| "Facebook is not signed in" | Run `python -m taskpilot login` again and sign in. |
| "signed in to a DIFFERENT account" | Sign out, then sign in to your own account. If you changed accounts on purpose, update **Facebook profile link** in Your details. |
| A form question is "unrecognised" | The form words the question differently. Add its exact wording to that detail's **question titles** box under Your details, then Save. |
| "Fill in Your details first" | Fill in all of Your details and click **Save details**. |
| A post "cannot be used" | The post was deleted or is private to you. Remove it, or tell the form owner. |
| A security check, CAPTCHA or "You're temporarily blocked" | **Stop.** Solve it yourself on Facebook and wait 24 to 48 hours before you run again. The app never bypasses these. |
| An action shows as **unverified** | Open the post and check it yourself. Never report it as done unless you can see it. |
| The dashboard says "Connecting…" | Make sure the PowerShell window is still running, then refresh the page. |

**Getting updates:** in the app folder, run `git pull`. If you downloaded a ZIP, download the latest version and copy your `data/` folder into it.

**Good practice:**
- Use only your own real account.
- Keep each run small, and space your runs out.
- Always check the form before it is submitted.
