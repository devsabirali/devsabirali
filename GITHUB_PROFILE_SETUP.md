# Private Contributions in README Stats

Your GitHub **profile** shows ~948 contributions because you enabled **Include private contributions on my profile**.

Third-party README cards (`github-profile-summary-cards`, paused `github-readme-stats.vercel.app`) only read **public** API data — they cannot see private commits without your token.

## What shows private vs public

| Widget | Private contributions |
|--------|------------------------|
| GitHub profile green graph | Yes (with profile setting ON) |
| Streak stats (`streak-stats.demolab.com`) | Uses visible contribution graph |
| Snake animation | Uses visible contribution graph |
| Old summary-cards / public vercel stats | No — public only |
| **GitHub Action + PAT** (`grs.yml`) | Yes — personal private repos |

**Org private repos (ICONAF):** Commits count on your profile graph if GitHub attributes them to you, but language/stars/PR stats may still be limited by org permissions even with a PAT.

---

## One-time setup (required for stats cards)

### 1. Create a Personal Access Token (Classic)

Log in as **devsabirali** → **Settings → Developer settings → Personal access tokens → Tokens (classic) → Generate new token**

Scopes:
- `read:user`
- `repo` (needed for private repo stats)

Copy the token.

### 2. Add token as repo secret

Open **https://github.com/devsabirali/devsabirali** → **Settings → Secrets and variables → Actions → New repository secret**

| Name | Value |
|------|--------|
| `STATS_PAT` | your token |

### 3. Push workflow and run it

Push `.github/workflows/grs.yml` to `main`, then:

**Actions → Update README Stats → Run workflow**

Wait ~1 minute. This creates:
- `profile/stats.svg`
- `profile/top-langs.svg`

Your README embeds these files — they update daily and include private data.

### 4. Also run snake workflow

**Actions → Generate Snake → Run workflow**

---

## Push commands

```powershell
cd D:\Data\prep-h1b\devsabirali
git add .
git commit -m "Use GitHub Action for private stats cards"
git push upstream main
```
