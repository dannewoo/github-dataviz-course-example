# GitHub Pages Starter — Data Visualization Design

A small, complete website you can copy, edit, and publish for free on
GitHub Pages. It is deliberately plain: three files, no build tools, no
frameworks, nothing to install.

**What's in the box**

```
index.html        the page structure and content
css/style.css     the visual design
js/main.js        the interactivity (a click counter + a bar chart)
.gitignore        tells Git to ignore junk files like .DS_Store
.nojekyll         tells GitHub Pages not to preprocess your files
README.md         this file
```

---

## Table of contents

1. [What GitHub Pages is (and how it differs from Glitch)](#1-what-github-pages-is)
2. [Publish your site — the browser-only way](#2-publish-your-site--browser-only)
3. [Publish your site — with GitHub Desktop](#3-publish-your-site--github-desktop)
4. [Your site's address](#4-your-sites-address)
5. [The everyday edit-and-publish loop](#5-the-everyday-edit-and-publish-loop)
6. [Working on your site locally](#6-working-on-your-site-locally)
7. [Rules that will bite you](#7-rules-that-will-bite-you)
8. [Troubleshooting](#8-troubleshooting)
9. [What to try in this project](#9-what-to-try-in-this-project)
10. [Vocabulary](#10-vocabulary)

---

## 1. What GitHub Pages is

GitHub Pages takes a folder of files sitting in a GitHub repository and
serves them on the public web, for free, at a URL like
`https://yourname.github.io/project-name/`.

That's the whole idea. Files in a folder become a website.

### Coming from Glitch

| | Glitch | GitHub Pages |
|---|---|---|
| Where you edit | In the Glitch editor, in your browser | Anywhere — your laptop, VS Code, or GitHub's web editor |
| When it goes live | Instantly, as you type | After you **commit and push** your changes |
| What it can run | HTML/CSS/JS **and** Node.js servers | HTML/CSS/JS **only** — no server-side code |
| Version history | Limited | Every change is saved forever, and you can go back |
| Sleeps when idle | Yes | No — it's always up |

The two changes you'll feel most:

- **Publishing is now a deliberate step.** You edit, then you *commit*
  (save a labeled snapshot), then you *push* (send it to GitHub). Your
  live site updates about 30 seconds later. This is a feature: your
  live site never breaks mid-edit.
- **There is no back end.** No Node, no Express, no databases, no secret
  API keys. Everything runs in the visitor's browser. For this course
  that is all you need — and it means your work will still be online
  years from now.

---

## 2. Publish your site — browser only

No installation, no command line. Good for your first time.

1. **Get a GitHub account** at [github.com](https://github.com) if you
   don't have one. Use a username you won't mind appearing in your
   portfolio URL — it becomes part of your site's address.

2. **Create a repository.** Click the **+** in the top-right of GitHub →
   **New repository**.
   - **Repository name:** `dataviz-starter` (lowercase, no spaces —
     hyphens are fine)
   - **Public** — GitHub Pages requires this on free accounts
   - Check **Add a README file**
   - Click **Create repository**

3. **Upload these files.** On the repository page, click
   **Add file → Upload files**. Drag in `index.html`, the `css` folder,
   and the `js` folder. Scroll down and click **Commit changes**.

   > Dragging the *folders* preserves the `css/` and `js/` structure —
   > that matters, because `index.html` looks for `css/style.css` at
   > exactly that path.

4. **Turn on Pages.** Go to the repository's **Settings** tab →
   **Pages** in the left sidebar.
   - Under **Source**, choose **Deploy from a branch**
   - **Branch:** `main`, folder: `/ (root)`
   - Click **Save**

5. **Wait about a minute**, then reload that Settings → Pages screen.
   A green banner appears with your live URL. Click it.

That's it. Your site is on the internet.

---

## 3. Publish your site — GitHub Desktop

Once you're editing files on your own computer, use
[GitHub Desktop](https://desktop.github.com) (free, Mac and Windows).
It's a visual app — you never have to type a Git command.

1. Install GitHub Desktop and sign in to your GitHub account.
2. **File → New Repository.** Name it, choose where to save it on your
   computer, and create it.
3. Put `index.html`, `css/`, and `js/` inside that new folder using
   Finder or File Explorer.
4. Back in GitHub Desktop, your files appear in the left panel. Type a
   short **Summary** (e.g. "Add starter site") and click
   **Commit to main**.
5. Click **Publish repository** at the top. **Uncheck "Keep this code
   private."**
6. Turn on Pages exactly as in step 4 above.

---

## 4. Your site's address

The URL depends on what you named the repository.

**Project site** — the normal case:

```
Repository:  dataviz-starter
Live URL:    https://YOURNAME.github.io/dataviz-starter/
```

**User site** — one per account, no folder in the URL. Name the
repository exactly `YOURNAME.github.io`:

```
Repository:  janedoe.github.io
Live URL:    https://janedoe.github.io/
```

Use a project site for each assignment. Save the user site for your
portfolio landing page, if you want one.

---

## 5. The everyday edit-and-publish loop

Every change to your live site follows the same three steps.

**In GitHub Desktop:**

1. Edit and save your files in your code editor.
2. In GitHub Desktop, write a short summary of what changed →
   **Commit to main**.
3. Click **Push origin**.

**In the terminal**, if you prefer:

```bash
git add .
git commit -m "Change the chart colors"
git push
```

Then wait about 30 seconds and reload your live URL.

**Write real commit messages.** "Add sorting to the bar chart" is
useful in three weeks. "update" and "asdf" are not. Your commit history
is a record of your process, and for this course it is part of what I
can see of your work.

---

## 6. Working on your site locally

**To preview:** double-click `index.html` and it opens in your browser.
For this project, that works fine.

**But once you load data from a file** — a `.csv` or `.json`, which you
will do in this course — opening the file directly stops working. The
browser blocks `fetch()` requests from `file://` pages for security
reasons. You'll see a CORS error in the console.

The fix is to run a tiny local web server. Two easy options:

**Option A — VS Code Live Server** (recommended)

Install the **Live Server** extension, then right-click `index.html` →
**Open with Live Server**. It also auto-reloads the page every time you
save. Once you have this, use it for everything.

**Option B — Python**

Every Mac has Python 3 already. In Terminal, navigate to your project
folder and run:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000` in your browser. Press `Ctrl+C` in
Terminal to stop it.

---

## 7. Rules that will bite you

These cause almost every "it worked on my computer" problem.

### File names are case-sensitive on the server

Your Mac doesn't care about capitalization. GitHub's servers do.

```html
<!-- If the file is named style.css, this WILL break online -->
<link rel="stylesheet" href="css/Style.css">
```

**Keep every file and folder name lowercase, with hyphens instead of
spaces.** `bar-chart.js`, not `Bar Chart.js`. This one rule prevents
most broken-site emergencies.

### Use relative paths, never absolute ones

```html
<!-- Good: relative to this file -->
<link rel="stylesheet" href="css/style.css">
<img src="images/chart.png">

<!-- Broken: only works on your own computer -->
<link rel="stylesheet" href="/Users/jane/Desktop/site/css/style.css">
```

A leading `/` also causes trouble on project sites, because it means
"the root of the domain" — which is `yourname.github.io`, not your
project folder. Just leave the slash off.

### The homepage must be named `index.html`

Lowercase, exactly that. `Index.html`, `home.html`, and `main.html`
will not be served as your homepage.

### It's a static site

No PHP, no Node, no database, no server-side code, and no secret keys.
Everything in your repository is public and readable by anyone — never
put an API key or a password in it.

### Sizes and limits

Repositories should stay under 1 GB and sites under 1 GB, with a soft
limit of 100 GB of traffic a month. You will not come close. But do
compress large images before committing them — a 12 MB photo makes your
site slow and your repository bloated forever.

---

## 8. Troubleshooting

| What you see | What's usually wrong |
|---|---|
| **404 page** right after setup | It's not ready yet. Wait 2–3 minutes and hard-refresh. |
| **404 that won't go away** | No `index.html` at the top level of the repository, or Pages is pointed at the wrong branch or folder. Recheck Settings → Pages. |
| **Page loads but is unstyled** | Wrong path or wrong capitalization in your `<link>` tag. Open the browser console and look for a red 404 on the CSS file. |
| **Works locally, broken online** | Capitalization, nine times out of ten. Compare the filename in your folder to the one in your HTML, character by character. |
| **Old version still showing** | Browser cache. Hard-refresh: `Cmd+Shift+R` (Mac) or `Ctrl+Shift+R` (Windows). Or check the **Actions** tab — the deploy may still be running. |
| **Nothing interactive works** | A JavaScript error. Right-click → **Inspect** → **Console** tab. Read the first red error and the line number it names. |
| **CORS error loading a data file** | You opened the HTML file directly. Use Live Server — see section 6. |
| **Pushed but nothing changed** | The commit may not have pushed. Check GitHub.com — if your change isn't visible there, it isn't live anywhere. |

**Your two best debugging tools**, in order:

1. **The browser console.** Right-click the page → Inspect → Console.
   Errors appear in red with the file and line number. Read the first
   one; later errors are often just fallout from it.
2. **GitHub.com itself.** Open your repository in a browser and look at
   the files. What you see there is exactly what's being served. If the
   change isn't there, the problem is on your end, not GitHub's.

---

## 9. What to try in this project

Make these edits, push them, and watch your live site change.

**Easy**

- Change the heading text in `index.html`.
- In `css/style.css`, change `--accent` (line 12-ish) to a different
  color and see everything that updates at once.
- Change the numbers in `coffeeData` in `js/main.js` and watch the bar
  chart redraw.

**Medium**

- Add a new day to `coffeeData`. Notice the chart handles it without
  any other change — that's the point of drawing from data.
- Add a fourth `<section class="card">` with your own content.
- Make the bars change color based on their value. In `drawChart()`,
  set `row.querySelector(".bar").style.backgroundColor` conditionally.

**Harder**

- Move `coffeeData` into a separate `data.json` file and load it with
  `fetch()`. Remember: you'll need Live Server to test this locally.
- Add a second chart with a different dataset, reusing `drawChart()` by
  passing it a different container.

---

## 10. Vocabulary

| Term | What it means |
|---|---|
| **Repository (repo)** | A project folder that Git tracks. Your website lives in one. |
| **Commit** | A saved snapshot of your changes, with a message describing them. |
| **Push** | Sending your commits from your computer up to GitHub. |
| **Pull** | Bringing changes from GitHub down to your computer. |
| **Branch** | A parallel version of your project. You'll live on `main`. |
| **`main`** | The default branch. This is what GitHub Pages publishes. |
| **Clone** | Downloading a repository to your computer, with its history. |
| **Fork** | Your own copy of someone else's repository, under your account. |
| **Static site** | A site made only of files sent to the browser as-is. |
| **`.nojekyll`** | An empty file that tells Pages to serve your files untouched. Without it, folders starting with `_` are ignored. |

---

## Reference

- [GitHub Pages documentation](https://docs.github.com/en/pages)
- [GitHub Desktop](https://desktop.github.com)
- [MDN Web Docs](https://developer.mozilla.org) — the reference for HTML, CSS, and JavaScript
