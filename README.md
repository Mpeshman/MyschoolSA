# Imfundo School — Deployment Guide

This repository contains a static site for Imfundo School (index.html, imfundo-school.html, and placeholders).

Goal: deploy to Vercel and point the custom domain `imfundoyakusasa.co.za` (GoDaddy DNS).

Prerequisites
- A GitHub account and a new repository (private or public).
- A Vercel account (you can sign in with GitHub).
- Access to your GoDaddy domain control panel for imfundoyakusasa.co.za.

Quick steps

1. Create a GitHub repository

On your machine (in the site folder), run:

```bash
cd "C:/Users/ACQ5UGW/OneDrive - Deere & Co/Desktop/Mfundoyakusasa"
git init
git add .
git commit -m "Initial Imfundo School site"
# create a repo on GitHub (use the web UI) then add the remote below
git remote add origin git@github.com:YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

If you prefer HTTPS use `https://github.com/YOUR_USERNAME/YOUR_REPO.git`.

2. Import to Vercel

- Sign in to Vercel and choose "Import Project" → select the GitHub repository you just pushed.
- Set framework to "Other" (static) if asked; build step is not required.
- Click Deploy — Vercel will build and publish the site to a vercel.app domain.

3. Add your custom domain in Vercel

- In your Vercel project, go to Settings → Domains → Add.
- Enter `imfundoyakusasa.co.za` and `www.imfundoyakusasa.co.za`.
- Vercel will show DNS records to add / verify. Use the entries below.

DNS records to add in GoDaddy (recommended minimal setup)

- For the root (apex) domain `imfundoyakusasa.co.za` add an A record:

  - Host: @
  - Points to: 76.76.21.21
  - TTL: 1 hour (or default)

- For the `www` subdomain add a CNAME:

  - Host: www
  - Points to: cname.vercel-dns.com
  - TTL: 1 hour (or default)

Alternatively you can change nameservers to Vercel's nameservers (Vercel will show them) and manage DNS there.

4. Verify and enable HTTPS

- After DNS changes propagate (a few minutes to a couple hours), Vercel will verify ownership and provision SSL automatically.
- In Vercel dashboard make sure the domain shows as verified and `https` is enabled.

Notes and troubleshooting
- DNS propagation may take time; use `dig` or an online DNS checker to confirm the A and CNAME records.
- If you prefer Netlify or Azure Static Web Apps, I can provide equivalent steps.
- If you want, I can prepare the GitHub repo contents and give exact commands to run locally.

If you want me to prepare the Git commands or a small deploy script, tell me your GitHub repo name (or I can show the exact commands to run locally). If you'd like Azure instead, I can prepare Azure Static Web Apps instructions.
