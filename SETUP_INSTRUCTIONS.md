# vux06.github.io — Setup Instructions

This is your Quartz site, pre-loaded with your CTF Writeups vault.
Build already verified locally: 27 writeups, 78 images, 0 broken links.

## 1. Create the repo on GitHub

- Go to github.com/new
- Repo name: `vux06.github.io` (must match your GitHub username exactly)
- Public, no README/gitignore/license (we already have files)
- Create repository

## 2. Push this folder to it

Open a terminal in this folder and run:

```bash
git init
git add .
git commit -m "Initial site: Quartz + CTF writeups"
git branch -M main
git remote add origin https://github.com/vux06/vux06.github.io.git
git push -u origin main
```

(Replace `vux06` in the URL if your GitHub username differs.)

## 3. Enable GitHub Pages via Actions

- On GitHub, go to your repo → Settings → Pages
- Under "Build and deployment" → Source → select "GitHub Actions"
- Push to `main` (or go to the "Actions" tab and run "Deploy Quartz site to
  GitHub Pages" manually) — the workflow at `.github/workflows/deploy.yml`
  builds the site and deploys it

## 4. Wait ~2 minutes

Your site will be live at: **https://vux06.github.io**

## Going forward — adding new writeups

1. Drop a new `.md` file into the right folder under `content/`
   (e.g. `content/HTB/HTB Medium/HTB Room - NewBox Medium.md`)
2. Paste in images the same way Obsidian does (`![[image.png]]`) —
   put the actual image file in `content/Assets/`
3. `git add . && git commit -m "add newbox writeup" && git push`
4. Live in ~1-2 minutes, no other steps needed

## Notes

- `content/index.md` is your landing page — edit the bio/links there anytime
- Your `portfolio.html` (if you have one) — drop it in `content/` as a
  standalone file, e.g. `content/portfolio.html`, and link to it from
  index.md as `[Portfolio](/portfolio.html)`
- `quartz.config.ts` — site title, theme colors, etc. Optional to touch.
