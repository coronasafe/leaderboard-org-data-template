# Template repository for Leaderboard Data Repo

Visit [Open Healthcare Network's Leaderboard Deployment](https://contributors.ohc.network/) deployed from [`coronasafe/leaderboard-data` repository](https://github.com/coronasafe/leaderboard-data).

## ⚙️ Configuring Scraper

The scraper scripts fetches data every 24 hours. The scraper workflow needs to run at an interval of 24 hours.

To change what time the scraper workflow runs, update the schedule cron value of the action:

```yml
# .github/workflows/scraper.yml
on:
  schedule:
    - cron: 0 0 * * *
```

### 🔑 Actions Secrets and Variables

**Secrets:**

| Name               | Description                                                      |
|--------------------|------------------------------------------------------------------|
| `SLACK_API_TOKEN`  | Optional; Required for scraping EOD messages for slack           |
| `GIT_ACCESS_TOKEN` | Personal Access Token; Needs write permissions to the data repo. |

**Variables:**

| Name                | Description                                                    |
|---------------------|----------------------------------------------------------------|
| `LEADERBOARD_REPO`  | Optional; Specify to use a fork of the leaderboard app repo.   |
| `SLACK_EOD_CHANNEL` | Optional; The channel ID to use for scanning for EOD messages. |

## 🚀 Deploying Leaderboard

> [!NOTE]
> To populate the flat data repository with historical data, run the [pullHistoricalGitHubActivities.js](https://github.com/coronasafe/leaderboard/blob/main/scripts/pullHistoricalGitHubActivities.js) script on the flat data repository.
> ```bash
> GITHUB_ORG=<ORG_NAME> GITHUB_TOKEN=<GITHUB_PAT> node scripts/pullHistoricalGitHubActivities.js
> ```

### Environment Variables

**`GITHUB_PAT`**
Some pages like [releases](https://contributors.ohc.network/releases), [projects](https://contributors.ohc.network/projects), etc. are server side rendered on-demand or pre-rendered during build time by calling GitHub's APIs and these calls requires authentication.
Create a Personal Access Token ([docs](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic)) with the following scopes **`repo`, `read:org`, `read:project`, `read:user`**.

### ⚙️ Deploy Configurations

The above deploy button uses the following configurations.

Root Directory: `leaderboard`
Build Command: `pnpm build`
Install Command: `./pre-deploy.sh && pnpm install`

## 🎨 Personalizing Leaderboard Deployment

Leaderboard can be personalized by editing the contents in `config` directory.

**Theme and Colors**
Leaderboard has support for light and dark mode. To edit the theme colors, update the [`theme.css`](https://github.com/coronasafe/leaderboard-org-data-template/blob/main/config/theme.css) file.

**Logo**
To change the favicon and logo, replace the files present in the [`config/assets`](https://github.com/coronasafe/leaderboard-org-data-template/tree/main/config/assets) directory with the desired ones.
