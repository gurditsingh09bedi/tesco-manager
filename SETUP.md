# Yeading Tesco Mobile Deals Board — GitHub setup (one-time, ~10 minutes)

Data for this board lives in a file called `deals.json` inside your own GitHub repo.
When your manager adds or removes a deal, it makes a real commit to that file —
you'll see it in the repo's commit history like any other change.

## Step 1 — create the repo (2 min)

1. Go to https://github.com/new
2. Name it anything, e.g. `yeading-tesco-deals`
3. Set it to **Public** (GitHub Pages free tier needs a public repo)
4. Click **Create repository**
5. On the new repo page, use **uploading an existing file** and upload all three
   files from this folder: `index.html`, `deals.json`, `.nojekyll`

## Step 2 — turn on GitHub Pages (1 min)

1. In the repo, go to **Settings → Pages**
2. Under "Build and deployment", set **Source** to **Deploy from a branch**
3. Branch: **main**, folder: **/ (root)** → **Save**
4. After ~1 minute your link is live at:
   ```
   https://YOUR_USERNAME.github.io/YOUR_REPO/
   ```

## Step 3 — connect the page to your repo (1 min)

1. Open `index.html` in a text editor
2. Find these two lines near the bottom of the file:
   ```js
   const GH_OWNER  = "PASTE_YOUR_GITHUB_USERNAME";
   const GH_REPO   = "PASTE_YOUR_REPO_NAME";
   ```
3. Fill in your actual GitHub username and repo name, e.g.:
   ```js
   const GH_OWNER  = "gurditsingh09bedi";
   const GH_REPO   = "yeading-tesco-deals";
   ```
4. Re-upload this updated `index.html` to the same repo (overwriting the old one).

## Step 4 — get your manager a personal access token (3 min)

This is what lets the manager save changes. Only she needs one — regular colleagues
just view the board, no login needed for that.

1. Go to https://github.com/settings/personal-access-tokens/new
2. Token name: e.g. "Yeading deals board"
3. Expiration: whatever you're comfortable with (e.g. 90 days, then make a new one)
4. Repository access: **Only select repositories** → pick this one repo
5. Under **Permissions → Repository permissions**, set **Contents** to **Read and write**
6. Click **Generate token**, copy it (starts with `github_pat_...`)
7. Give this token to your manager. She pastes it once into **Manager login** on the
   site (tick "Remember on this device" so she doesn't need to paste it every time).

## How it works day to day

- **Anyone** who opens the link just sees the current deals — no login, updates
  automatically every 60 seconds.
- **Manager** clicks "Manager login" (top right), pastes her token once, then can
  add or remove deals any time. Each change is a real GitHub commit.
- Tapping any deal card opens a popup with full details and a **"Reach on WhatsApp"**
  button that opens a chat to 07456 610065 with the deal pre-filled in the message.

## Honest notes on security

- The token only has write access to this one repo (if you scoped it as above) —
  not your whole GitHub account.
- The token lives only in the manager's own browser (localStorage), never in the
  public site code. Regular colleagues viewing the board never see or need it.
- If the token ever leaks, revoke it instantly at
  https://github.com/settings/personal-access-tokens and issue a new one.
