# GitHub README Stats — Private & Company Repos

## Why stats cards showed 0 / images were broken

1. **`profile/stats.svg` did not exist** — the workflow never created those files (404).
2. **Company org private repos (ICONAF, etc.)** — standard stats cards **cannot** show stars, PRs, or languages from org private repos on a README, even with a PAT, unless the org explicitly authorizes your token.
3. **Your 948 contributions on GitHub profile** are correct — they come from GitHub’s own contribution graph.

## What works for company + private contributions

These read your **public contribution graph** (the same green squares on your profile):

| Widget | Shows private/company commits? |
|--------|-------------------------------|
| **Streak stats** | Yes — if they appear on your profile graph |
| **Activity graph** | Yes — same graph data |
| **Snake animation** | Yes — same graph data |
| Stats / Top languages cards | No for org private repos |

Your README now uses **streak + activity graph + snake** only — no broken local SVG files.

---

## Profile setting (required)

**GitHub → Settings → Profile → Include private contributions on my profile** ✅

---

## Optional: personal private repo stats cards

Only if you want extra cards for **your own** private repos (not ICONAF org):

1. Create PAT (classic) with `repo` + `read:user`
2. Add secret `STATS_PAT` on `devsabirali/devsabirali`
3. Run **Actions → Update README Stats**

For **ICONAF org** private repos, also go to:

**GitHub → Settings → Applications → Authorized OAuth Apps** (or PAT settings) → **Configure SSO** → Authorize token for **ICONAF**

Even then, language breakdown may stay limited.

---

## Push updated README

```powershell
cd D:\Data\prep-h1b\devsabirali
git add README.md github-profile-README.md .github/workflows/snake.yml
git commit -m "Fix streak URL encoding and snake asset path"
git push upstream main
```

## Run snake workflow (required once)

1. Push the updated `snake.yml` to GitHub
2. Go to **https://github.com/devsabirali/devsabirali/actions**
3. Click **Generate Snake** → **Run workflow** → **Run workflow**
4. Wait until the run shows a **green checkmark** (~2 min)
5. Confirm this file exists (should show an SVG, not 404):

   `https://raw.githubusercontent.com/devsabirali/devsabirali/main/assets/contribution-snake.svg`

6. Refresh your profile — snake will appear
