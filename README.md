# Template repository for Leaderboard Data Repo

## Configuring Scraper

The scraper scripts fetches data every 24 hours. The scraper workflow needs to run at an interval of 24 hours.

To change what time the scraper workflow runs, update the schedule cron value of the action:

```yml
# .github/workflows/scraper.yml
on:
  schedule:
    - cron: 0 0 * * *
```

## Deploying Leaderboard

TLDR; just click deploy...

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fcoronasafe%2Fleaderboard-data%2Ftree%2Fmain%2Fleaderboard&env=GITHUB_PAT&project-name=leaderboard&repository-name=leaderboard-data&demo-title=Open%20Healthcare%20Network%20-%20Leaderboard&demo-description=Leaderboard%20collects%20data%20from%20GitHub%20and%20Slack%20to%20show%20off%20the%20work%20of%20our%20open%20source%20contributors&demo-url=https%3A%2F%2Fcontributors.ohc.network&demo-image=https%3A%2F%2Fgithub.com%2Fcoronasafe%2Fleaderboard%2Fassets%2F25143503%2F6352a4cf-4b8b-4f80-b45c-6af323ee502e)

### env vars

#### `GITHUB_PAT`

Some pages like [releases](https://contributors.ohc.network/releases), [projects](https://contributors.ohc.network/projects), etc. are server sidered on-demand or pre-rendered during build time by calling GitHub's APIs and this requires authentication.

Refer how to [create a personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic).

The following scopes are required:

- `repo`
- `read:org`
- `read:project`
- `read:user`

### Deploy Configurations

The above deploy button uses these configurations.

Root Directory: `leaderboard`
Build Command: `pnpm build`
Install Command: `./pre-deploy.sh && pnpm install`

## Personalizing Leaderboard Deployment

TODO
