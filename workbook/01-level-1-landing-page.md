# Level 1: Your landing page

**Goal:** put a landing page about your startup on the internet, at your own address.

## What you'll build

A complete startup website. The starter site is about a fictional startup, **Plovify** ("Plov as a Service"): replace it with yours, or keep it and tweak it. It has a navigation bar with a kazan logo, a big headline with buttons, an illustration in your brand colour, key numbers, features with icons, a menu, a "How it works" section, an FAQ and a blog with two sample posts. It works on phones and switches to dark mode automatically. You personalise it by changing a few lines of text. It is served from Cloudflare's global network, so it loads fast in Tashkent, Almaty or London. Every change you save on GitHub goes live automatically in about a minute.

## Building blocks

- **Workers static assets:** Cloudflare stores your website files (HTML, CSS, images) and serves them from data centers close to each visitor.
- **Workers Builds (CI/CD):** when you save a change in GitHub, Cloudflare rebuilds and republishes your site for you.
- **Astro:** a popular tool that turns simple files (a settings file and Markdown blog posts) into a fast website. You only edit one file: `src/config.ts`.

## Steps

### Part A: Deploy the starter site (about 7 minutes)

We do Part A together at the very start of the workshop. While your site builds, the presenter explains how Cloudflare works. Part B comes after the theory.

1. Log in to https://dash.cloudflare.com in your browser.
2. Ctrl+click (Cmd+click on Mac) the **Deploy to Cloudflare** button below. It opens in a new tab, so this workbook stays open:

   [![Deploy to Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/asazhin-dev/startup-launch-kit/tree/main/level-1)

3. If Cloudflare asks you to choose an account, choose your account.
4. Under **Git account**, click **New GitHub connection**.

   <p>
     <img src="images/01/00-new-github-connection.png" width="480"
          alt="Cloudflare setup page: under Git account, click New GitHub connection">
   </p>

   A GitHub page opens asking to install **Cloudflare Workers and Pages** on your account.
   Keep **All repositories** selected and click **Install & Authorize**.
   GitHub then sends you back to Cloudflare automatically.

   <p>
     <img src="images/01/01-github-install-authorize.png" width="480"
          alt="GitHub asks to install Cloudflare Workers and Pages: click Install & Authorize">
   </p>

   This lets Cloudflare create your repository and rebuild your site when you change it.
   You can limit access to specific repositories later in **GitHub → Settings → Applications**.

5. The setup page shows several fields. Fill them in like this:

   | Field | What to do |
   | --- | --- |
   | **Git account** | Choose your own GitHub account (the one you just connected). |
   | **Create private Git repository** | Ticked or unticked, both work. Ticked keeps your code private. |
   | **Project name** | Keep `startup-launch-kit`. It is used for both your repository and your Worker. Change it only if you see a message that the name is already taken (for example, use `startup-launch-kit-2`). |
   | **Build command**, **Deploy command**, **Preview command** | Leave them exactly as they are. |
   | **Enable Preview builds** | Leave it as it is. |
   | **Protect with Cloudflare Access** | Leave it **off**. If it is on, visitors must log in to see your site. |
   | Other settings (if shown) | Keep the suggested settings. |

   > [!WARNING]
   > If you **do** change the Project name, write it down now. You will need it in Level 2.
   
   <img src="images/01/02-worker-setup-window.png" width="480"
    alt="Cloudflare 'Set up your application' page: keep Project name startup-launch-kit and the default commands, then click Deploy">

6. Click **Deploy**.
7. Wait 1–3 minutes. You will see the build progress. Do not close the tab.
   ![Deployment progress screen with build steps](images/01/03-deployment-progress.png)

8. When it finishes, click **Visit** button at the right upper corner to access your site.
   ![Visit Button to Access Website](images/01/04-visit-site.png)

9. You should see a complete website for the fictional startup **Plovify**, with the headline **"Plov as a Service"**. Scroll down to see the features, menu, FAQ and footer, and click **Blog** in the top menu.
   ![The Plovify starter site: kazan logo and top menu, orange "Get in touch" button, headline "Plov as a Service", steaming kazan illustration on the right, numbers strip, feature cards with icons](images/01/05-site-plovify.png)

10. Copy that address from your browser's address bar and keep it somewhere. This is **your live URL**.
    It looks like `https://startup-launch-kit.<your-account>.workers.dev`. The middle part comes from your Cloudflare account (usually your account name).
    > [!TIP]
    > **How to find your live URL later.** In the Cloudflare dashboard, open **Workers & Pages** in the left menu (or type "Workers" in the search bar at the top), click your Worker `startup-launch-kit`. Your `.workers.dev` address is shown on the Worker's overview page. 
    > ![Workers URL on the Overview Page](images/01/06-workers-url-overview.png)

### Part B: Make it about YOUR startup (about 18 minutes)

11. Open your repo on GitHub: go to `https://github.com/<your-github-username>/startup-launch-kit` (use your repo name if you changed it).
12. Click the folder `src`, then click the file `config.ts`.
13. Click the **pencil icon** (✏️ "Edit this file") at the top right of the file.
    
    ![GitHub file view of src/config.ts with the pencil icon highlighted](images/01/07-github-src-configts.png)

14. At the top of the file you see a block called **EDIT: basics**. It looks like this:

    📄 `src/config.ts`
    ```ts
    name: "Plovify",
    tagline: "Plov as a Service",
    description:
      "Plovify brings hot, fresh plov to every table, from a family dinner to a wedding for 800 guests. ...",
    ```

    Change the text **between the double quotes** `"..."` for `name`, `tagline` and `description` to your startup. Keep the quotes and the commas. For example:

    ```ts
    name: "Your Startup Name",
    tagline: "What you do, in one short sentence.",
    description:
      "One or two sentences: the problem you solve and who it is for.",
    ```

    No startup idea yet? Keep Plovify and just change a word or two, for example the tagline.

15. **Building your own startup?** A few lines below, set the switch to `false`:

    ```ts
    showPlovifyExamples: false,
    ```

    This hides all Plovify sample content (menu, numbers, plov FAQ, the two sample blog posts and the "Plovify is fictional" footer) and uses neutral texts with **your** startup's name instead, for example "Join the Your Startup Name waitlist" and "Ask Your Startup Name". Keeping Plovify? Leave it `true`.
16. Optional, in the same block:

    - **Brand colour:** change `accentColor` to a hex code, for example `"#2563eb"` (blue) or `"#16a34a"` (green). Keep the `#` and the quotes.
    - **Contact email:** change `contactEmail` to your email.
    - **Leave everything else as it is for now.** The **OPTIONAL: more sections** block (features, menu, steps, numbers, FAQ) is empty on purpose. You can add your own items after the workshop; the comments in the file show how.
    - **Do not change** `enableWaitlist` or `enableAssistant`. Leave them `false`; you turn them on in Levels 2 and 3.

> [!NOTE]
> **Rules so you don't break the file:**
>
> - Keep every double quote `"` and every comma `,` at the end of the line.
> - If your text needs quotes, use single quotes inside: `"Plov 'on demand'"`.
> - Apostrophes are fine, so Uzbek text like `"O'zbekiston"` works.
> - Type your text directly in the GitHub editor. Text pasted from Word, Google Docs or a phone may contain "curly" quotes `“ ”` that break the build. If you paste, retype the outer quotes `"` in the editor.

17. Click the green **Commit changes...** button at the top right.
    ![Github Commit Changes](images/01/08-commit-changes.png)

18. In the pop-up, keep **Commit directly to the `main` branch** selected and click **Commit changes**.
    <img src="images/01/09-commit-to-main.png" width="480"
          alt="Github Commit to Main">

19. Wait about 1 minute. On your repo's main page, next to the latest commit message, you will see a small **yellow dot** (building). It turns into a **green check ✓** when your site is live, or a **red ✗** if the build failed.

    ![GitHub repo page showing the green check next to the latest commit](images/01/10-commit-passed.png)

20. When you see the green check, open your live URL and refresh the page (Ctrl+F5 on Windows, Cmd+Shift+R on Mac). You should see your startup's name in the top menu, your tagline as the big headline, and your description below it. The illustration shows your name too. If you set `showPlovifyExamples: false`, the menu, numbers and FAQ are gone and the blog says "Our first post is coming soon." If you changed `accentColor`, the buttons and highlights now use your colour.

    ![Personalised site with a custom name, headline and a blue accent colour](images/01/11-personalized-site.png)

> [!NOTE]
> **How to see the build log.** In the Cloudflare dashboard: **Workers & Pages** → your Worker → **Deployments** tab → click the latest build → **Build**.
> ![See Worker Build Logs](images/01/12-worker-build-logs.png)
> A red ✗ means something went wrong: see [Troubleshooting](troubleshooting.md#build-failed).

## Checkpoint ✅

Paste your live URL in the webinar chat, for example:

`Level 1 done: https://startup-launch-kit.<your-cf-account>.workers.dev`

## What just happened

You published a real website on Cloudflare's global network, connected to GitHub so every change goes live automatically.

<details>
<summary><b>How it works, and how it compares to AWS</b></summary>
<br>

Cloudflare ran `npm run build`: Astro turned your settings in `config.ts` and the Markdown blog posts into ready-made static pages (home, blog, one page per post, 404). Then `wrangler deploy` uploaded the files to Cloudflare's network. Your site now runs in 330+ cities in 125+ countries. There is no server for you to manage, and static file requests are free and unlimited on the free plan.

**On AWS** you'd typically use Amplify Hosting or S3 + CloudFront, choose a region, and add a payment card at sign-up (required even on the AWS Free plan, which closes after 6 months).

**In production:** connect your own domain (for example a `.uz` domain); HTTPS and DDoS protection are already on. Your prototype is your production: no rewrite, no migration.

</details>

## Stuck?

- First check [Troubleshooting](troubleshooting.md).
- If the Deploy button flow fails completely, ask a helper in the webinar chat. Most problems are an unverified email or the GitHub connection.
- You can continue to Level 2 even if your text is not perfect yet; you can edit `src/config.ts` any time.

## Bonus for fast finishers: publish your first blog post (about 3 minutes, optional)

Only do this if you are done and waiting. It is **not** needed for Level 2.

1. In your repo on GitHub, click the folder `src`, then `content`, then `blog`. You see the two Plovify sample posts (they are hidden on your site if `showPlovifyExamples` is `false`; your own post always shows).
2. Click **Add file** → **Create new file**.
3. Check that the path above the file-name box shows `src/content/blog/`. In the file name box, type exactly: `my-first-post.md`
   (If the path is different, delete what is in the name box and type the full path instead: `src/content/blog/my-first-post.md`.)
4. Paste this text and change the parts you like (keep the three `---` lines and the quotes):

   ```markdown
   ---
   title: "Hello from our team"
   description: "A short introduction to who we are and what we are working on."
   pubDate: 2026-01-31
   author: "Your Name"
   ---

   Hi, we are the team behind our startup. We are building something to make life easier for our customers, and this blog is where we will share our progress.

   Follow along, join the waitlist, and tell us what you think. We read every message.
   ```

   `2026-01-31` is only an example: set `pubDate` to today's date (format YYYY-MM-DD). The newest date appears first on the blog.
5. Click **Commit changes...** → **Commit directly to the `main` branch** → **Commit changes**.
6. Wait for the **green check ✓**, then open your live URL with `/blog` at the end (for example `https://startup-launch-kit.<your-cf-account>.workers.dev/blog`). Your post is in the list. Click it to read it.

Red ✗? See [Troubleshooting: blog post errors](troubleshooting.md#blog-post-errors).

---

Next: [Level 2: Waitlist and database →](02-level-2-waitlist.md)
