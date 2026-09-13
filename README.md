# Minimal Hugo + PaperMod Blog

## Local dev

```bash
git clone --recurse-submodules <your-repo-url>
cd <repo>
hugo server
```

If you forgot `--recurse-submodules`:

```bash
git submodule update --init --recursive
```

## Deploy on Cloudflare Pages

1. Push this repo to GitHub or GitLab.
2. In the Cloudflare dashboard go to **Workers & Pages → Create → Pages → Connect Git**.
3. Select the repo and branch.
4. Build settings:
   - **Build command:** `hugo --gc --minify`
   - **Build output directory:** `public`
5. Deploy. Every push to the branch rebuilds automatically.

## Structure

```
content/
  about.md          → /about/
  posts/*.md        → homepage list + individual post pages
layouts/
  index.html        → homepage: list of posts, nothing else
hugo.toml           → site config + PaperMod theme settings
```

## Edit your about page

Open `content/about.md` — three sentences: who you are, what you're working on, how to reach you.

## Add a post

Drop a new `.md` file in `content/posts/`. It appears on the homepage automatically.
