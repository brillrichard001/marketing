# How to Publish & Update This Site 🚀

This is the **BoostHub NG** marketing site. It lives for free on **GitHub Pages**
and stays online 24/7 — even when your computer is off. You never touch a server.

**Live site:** https://brillrichard001.github.io/marketing/

---

## 1. Publish changes (the only 3 commands you need)

Every time you change something and want it live, open a terminal in this folder
(`C:\Users\mrjon\sites\marketing`) and run these three commands:

```powershell
git add .
git commit -m "describe what you changed"
git push
```

That's it. When you `git push`, GitHub automatically rebuilds the site and puts it
live in about **1–2 minutes**. No uploading, no server, no extra steps.

> Tip: Change the message in quotes to describe your edit, e.g.
> `git commit -m "update pricing to 3000"`.

---

## 2. Preview locally before publishing

Want to see your changes on your own PC first, before they go public?

```powershell
npm run dev
```

Then open the address it prints (usually **http://localhost:4321/marketing/**) in
your browser. It auto-refreshes as you edit. Press `Ctrl + C` to stop it.

---

## 3. Where to edit the content

The whole homepage is one file:

```
src\pages\index.astro
```

Open it in any editor (Notepad, VS Code). Inside you'll find plain, readable text:

- The **headline & buttons** are near the top, under `<!-- HERO -->`.
- The **three feature boxes** are under `<!-- FEATURES -->`.
- The **pricing line** (₦2,500) is under `<!-- PRICING / CTA BAND -->`.
- The **WhatsApp number** is set once at the very top (`const whatsapp = ...`)
  and reused everywhere. Change it in that one spot.
- Colors live in the `:root { ... }` block inside `<style>` (`--brand`, `--accent`).

Edit the words between the tags, save, then run the 3 publish commands above.

---

## 4. Add your own custom domain later (optional)

When you buy a domain (e.g. `boosthub.ng`), you can point it at this site for free.

**Step A — tell GitHub your domain.** Create a file named exactly `CNAME` (no
extension) in this folder, containing only your domain:

```
boosthub.ng
```

Commit and push it (the 3 commands).

**Step B — at your domain registrar (where you bought the domain)**, add these DNS
records:

Four **A records** for the bare domain (`@`), all pointing to GitHub:

| Type | Name | Value            |
|------|------|------------------|
| A    | @    | 185.199.108.153  |
| A    | @    | 185.199.109.153  |
| A    | @    | 185.199.110.153  |
| A    | @    | 185.199.111.153  |

One **CNAME record** for `www`:

| Type  | Name | Value                       |
|-------|------|-----------------------------|
| CNAME | www  | brillrichard001.github.io   |

**Step C — in the GitHub repo**, go to **Settings → Pages**, enter your domain, and
tick **Enforce HTTPS** once it's available. DNS can take a few minutes to a few hours
to activate.

> Note: With a custom domain you can later remove the `base: '/marketing'` line in
> `astro.config.mjs` and set `site` to your domain, so the site serves at the root
> (`boosthub.ng/`) instead of `/marketing/`.

---

## Quick reference

| I want to...            | Do this                                   |
|-------------------------|-------------------------------------------|
| Put changes live        | `git add .` → `git commit -m "..."` → `git push` |
| Preview on my PC        | `npm run dev`                             |
| Edit the page           | Open `src\pages\index.astro`              |
| See it live             | https://brillrichard001.github.io/marketing/ |
