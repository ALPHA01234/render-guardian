# Render Guardian

A lightweight dashboard and scheduled HTTP checker for your deployed Render projects.

## Setup

1. Open [sites.txt](./sites.txt).
2. Add one full deployed URL per line, for example `https://your-project.onrender.com`.
3. Commit the changes.
4. Open the **Actions** tab and select **Keep Render services awake**.
5. Choose **Run workflow** once. Scheduled checks then run every 10 minutes.
6. Enable GitHub Pages in **Settings → Pages**, selecting **Deploy from a branch**, branch `main`, folder `/ (root)`. Your dashboard will be published at `https://alpha01234.github.io/render-guardian/`.

The dashboard reads `status.json`, which the workflow updates after each run. It refreshes the display every minute.

## Important limitations

- This is best-effort, not a 24/7 uptime guarantee. GitHub Actions scheduled workflows can be delayed and may be disabled after prolonged repository inactivity.
- A request every 10 minutes may reduce Render free-service cold starts, but it does not override Render's free-plan limits or guarantee the service never sleeps.
- A successful HTTP response only confirms that the URL returned a successful response; it does not test the full application.
- If a service must be reliably available at all times, use an always-on hosting plan.
- Only add websites you own or are authorized to monitor. Avoid very frequent checks.

## Configuration

Edit `sites.txt` to add or remove URLs. One URL per line; lines beginning with `#` are comments. The workflow has a manual trigger for immediate checks.
