# Setup Guide — make everything render 100%

Everything in `README.md` (typing text, stats cards, streak, trophies,
capsule banners, skill icons) is pulled live from public, free services
(shields.io, capsule-render, github-readme-stats, skillicons.dev, komarev).
Those need **no setup** — they just work once the README is on GitHub,
because GitHub fetches the images fresh every time someone opens your
profile.

The **only** piece that needs a one-time setup is the animated snake at
the bottom of the README. Here's exactly how to turn it on:

## 1. Create (or confirm) the special profile repo
The animation — and the whole "profile README" feature — only works in a
repo that has **the exact same name as your GitHub username**:

```
https://github.com/DineshM2006/DineshM2006
```

If it doesn't exist yet, create a new **public** repository named
`DineshM2006` (must match your username exactly, case-insensitive), and
check "Add a README file" when creating it.

## 2. Add the files from this download
Copy these two files into that repo, keeping the same folder structure:

```
DineshM2006/
├── README.md
└── .github/
    └── workflows/
        └── snake.yml
```

You can do this by dragging both files/folders into the GitHub web
uploader ("Add file → Upload files"), or via git:

```bash
git clone https://github.com/DineshM2006/DineshM2006.git
cd DineshM2006
# copy README.md and .github/ folder in here
git add .
git commit -m "Add profile README + snake animation workflow"
git push
```

## 3. Turn on Actions permissions (required once)
1. Go to your repo → **Settings → Actions → General**
2. Under "Workflow permissions", select **Read and write permissions**
3. Click **Save**

Without this, the workflow can't push the generated SVG to the `output`
branch and the snake image will look broken/empty.

## 4. Run the workflow the first time
1. Go to the **Actions** tab in the repo
2. Click **Generate Snake Animation** in the left sidebar
3. Click **Run workflow → Run workflow**
4. Wait ~30–60 seconds. It will create a new branch called `output` with
   the generated `github-contribution-grid-snake.svg` — this is the file
   the README already points to, so no further edits are needed.

After that, it re-runs automatically every day (via the `cron` schedule)
to keep the snake showing your latest contributions, and also re-runs
every time you push to `main`.

## 5. Double-check
Open `https://github.com/DineshM2006` in an incognito window — everything,
including the snake, should now load. If the snake row still looks empty:
- Re-check step 3 (write permissions is the #1 cause)
- Re-check the repo name matches your username exactly
- Look at the Actions tab for a red ❌ run and open its logs for the error

That's it — once this one-time setup is done, the whole README is fully
live and self-updating, no maintenance needed.
