# Startup Launch Kit

Build and launch a real website for your startup on the **Cloudflare Developer Platform**, in under two hours, without installing anything, for free.

The starter site is about **Plovify** ("Plov as a Service"), a fictional startup. Replace it with yours, or keep it and tweak it.

Your prototype is your production: no rewrite, no migration.

You build it in three levels:

| Level | What you get | Cloudflare building blocks |
| --- | --- | --- |
| 1 | A landing page about **your** startup, live on the internet | Workers + static assets, Workers Builds (CI/CD) |
| 2 | A waitlist form that saves emails | Worker API + D1 (SQL database) |
| 3 | An AI assistant that answers visitors' questions about your startup, in their language | Workers AI |

## Start here

👉 **Follow the workbook: [workbook/README.md](workbook/README.md)**

## Deploy buttons

Each button copies one level into a new repository in **your** GitHub account and deploys it to **your** Cloudflare account.

| Level | Button |
| --- | --- |
| Level 1: Landing page | [![Deploy to Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/asazhin-dev/startup-launch-kit/tree/main/level-1) |
| Level 2: + Waitlist (catch-up) | [![Deploy to Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/asazhin-dev/startup-launch-kit/tree/main/level-2) |
| Level 3: + AI assistant (catch-up) | [![Deploy to Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/asazhin-dev/startup-launch-kit/tree/main/level-3) |

In the workshop you click **only the Level 1 button**. The Level 2 and Level 3 buttons are for catching up if you get stuck.

## What is in this repository

```
level-1/     Landing page (static website)
level-2/     Level 1 + waitlist API + D1 database
level-3/     Level 2 + AI assistant (POST /api/ask)
workbook/    Step-by-step guide for attendees
```

Each `level-*` folder is a complete, self-contained project.

## For developers (optional)

You do not need this for the workshop. If you prefer to work locally (Node.js 22+), or in GitHub Codespaces:

```bash
cd level-3
npm install
npm run build
npx wrangler dev      # local preview at http://localhost:8787
npx wrangler deploy   # deploy to your account (asks you to log in)
```

Workers AI always runs on Cloudflare, so the AI assistant needs `npx wrangler login` even during local preview.

## License

MIT. See [LICENSE](LICENSE). You are free to use, change and launch this code as your own startup's site.
