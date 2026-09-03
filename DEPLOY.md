# Deploying this portfolio

**The site is live at <https://manasajayappa.github.io>**

Repo: `manasajayappa/manasajayappa.github.io` · Branch: `main` · Folder: `/ (root)`

Working folder on this Mac:

```bash
cd ~/Desktop/Portfolio/manasajayappa.github.io
```

The initial setup (account, repo, push, Pages) is done. Steps 1-5 below are kept
for reference only. Day-to-day, you only need "Making changes later".

---

## Step 0 — One-time housekeeping (done)

**Tell git who you are** (only needed once per machine):

```bash
git config --global user.name "Manasa J"
git config --global user.email "manasa.jayappa@gmail.com"
```

Use the same email as your GitHub account so your commits are attributed to you.

---

## Step 1 — Create a GitHub account (done)

If you don't have one: <https://github.com/signup>

Your username becomes part of your site's address, so pick something you'd put on a résumé — `manasaj`, not `mj-2026-test`.

---

## Step 2 — Choose your repository name (this decides your URL) (done)

| Repo name | Your site URL | Notes |
|---|---|---|
| `<username>.github.io` | `https://<username>.github.io` | **Recommended.** Clean, short, résumé-ready. One per account. |
| `portfolio` | `https://<username>.github.io/portfolio/` | Fine, but longer. Use if you want `<username>.github.io` for something else later. |

If your username were `manasaj`, the recommended repo name is exactly `manasaj.github.io` and your site lands at `https://manasaj.github.io`.

---

## Step 3 — Create the empty repository on GitHub (done)

1. Go to <https://github.com/new>
2. **Repository name:** the name you chose in Step 2
3. **Visibility:** **Public**
   GitHub Pages requires a public repo on the free plan. The repo being public only means people can read the site's source code — which is HTML for a portfolio you *want* people to see.
4. **Do NOT** check "Add a README file", "Add .gitignore", or "Choose a license".
   Your folder already has these. Adding them here creates a conflicting first commit.
5. Click **Create repository**

Leave that page open — it shows the URL you need next.

---

## Step 4 — Connect your folder and push (done)

Replace `<username>` and `<repo>` with your real values:

```bash
git remote add origin https://github.com/<username>/<repo>.git
git branch -M main
git push -u origin main
```

### Authenticating

Git will ask for a username and password. **Your GitHub account password will not work** — GitHub requires a token. Two ways:

**Option A — GitHub CLI (easiest if you have Homebrew)**

```bash
brew install gh
gh auth login
```

Choose *GitHub.com* → *HTTPS* → *Login with a web browser*, follow the prompts, then run the `git push` above. It just works from then on.

**Option B — Personal Access Token (no install)**

1. Go to <https://github.com/settings/tokens>
2. **Generate new token → Generate new token (classic)**
3. Note: `portfolio`; Expiration: 90 days or longer
4. Check the **`repo`** scope
5. Generate, then **copy the token** — you cannot view it again
6. Run `git push -u origin main`; enter your **username**, and paste the **token** as the password

macOS stores it in Keychain, so you'll only do this once.

---

## Step 5 — Turn on GitHub Pages (done)

1. On your repo page, click **Settings** (top right)
2. Left sidebar → **Pages** (under "Code and automation")
3. **Source:** *Deploy from a branch*
4. **Branch:** `main` · **Folder:** `/ (root)`
5. Click **Save**

Wait about a minute. Refresh the page — a green banner appears with your live URL.

---

## Step 6 — Check your live site (done)

Visit your URL and click through all three tabs: Home, Experience, Starbucks Case Study.

If you see a plain unstyled page, the CSS didn't load — check that `assets/css/style.css` was pushed (`git ls-files` should list it).

If you get a 404, wait two more minutes; the first build is the slowest.

---

## Step 7 (optional) — Use your own domain name

The `github.io` URL is free and permanent. If you'd rather have something like `manasaj.com`:

1. Buy the domain (Namecheap, Cloudflare, Porkbun — roughly $10–15/year)
2. Repo **Settings → Pages → Custom domain** → enter your domain → **Save**
3. At your domain registrar, add these DNS records:

   | Type | Name | Value |
   |---|---|---|
   | A | `@` | `185.199.108.153` |
   | A | `@` | `185.199.109.153` |
   | A | `@` | `185.199.110.153` |
   | A | `@` | `185.199.111.153` |
   | CNAME | `www` | `<username>.github.io` |

4. Back on the Pages settings, tick **Enforce HTTPS** once it becomes available (can take up to 24 hours)

DNS changes can take a few hours to take effect.

---

## Making changes later

Every push updates the live site automatically, usually within a minute.

```bash
cd ~/Desktop/Portfolio/manasajayappa.github.io
git add .
git commit -m "Describe what changed"
git push
```

To preview locally before pushing:

```bash
python3 -m http.server 8000
# open http://localhost:8000 — Control-C to stop
```

---

## Still to fill in

- [ ] Replace `YOUR-LINKEDIN` with your real handle — it appears in `index.html`, `experience.html`, and `case-studies/starbucks-mood-drinks.html`
- [ ] Export your résumé to PDF and swap it for the `.docx` in `assets/files/` — PDFs open in the browser instead of downloading

Find them with:

```bash
grep -rn "YOUR-LINKEDIN" --include="*.html" .
```
