🧠 INSTRUCTIONS FOR CODING AGENT
Goal

Create a minimal static company/dev blog site using:

Astro

Markdown blog posts

Auto-deploy via Cloudflare Pages

Clean single-page layout

Easy future expansion (About, Contact)


1️⃣ Initialize Project
npm create astro@latest mysite


Choose:

Minimal

TypeScript

Install dependencies

Initialize git

Then:

cd mysite
npm install

----------------
STEP ONE IS ALREADY DONE
--------------------------


2️⃣ Clean Structure

Delete unnecessary boilerplate.

Create structure:

src/
  pages/
    index.astro
  content/
    blog/
  layouts/
    BaseLayout.astro

3️⃣ Enable Content Collections

Create:

src/content/config.ts

import { defineCollection, z } from 'astro:content';

const blog = defineCollection({
  type: 'content',
  schema: z.object({
    title: z.string(),
    description: z.string().optional(),
    date: z.date(),
  }),
});

export const collections = { blog };

4️⃣ Create Base Layout

src/layouts/BaseLayout.astro

Minimal clean layout:

Simple HTML5

Responsive

Clean typography

No heavy CSS framework

Use system fonts

Max width ~800px centered

Include:

Header (Company name)

Footer (© Company Name + year)

Keep styling minimal and clean.

5️⃣ Create Index Page

src/pages/index.astro

Must:

Import getCollection from astro:content

Fetch blog posts

Sort by date descending

Render:

Sections:

Hero (Game name + short hook)

About paragraph (short, 3–4 lines)

Latest Posts list (title + date + short description)

Each post should link to its own page.

6️⃣ Generate Blog Post Pages

Create dynamic route:

src/pages/blog/[...slug].astro

Use getStaticPaths() with getCollection('blog').

Render:

Title

Date

Content

Keep clean minimal formatting.

7️⃣ Example Blog Post

Create:

src/content/blog/first-devlog.md

---
title: "First Devlog"
description: "Initial prototype progress."
date: 2026-02-07
---

We started building the core combat loop.

Goals:
- Fast iteration
- Strong mechanical hook
- Early playtesting

8️⃣ Verify Locally
npm run dev


Confirm:

Homepage renders

Blog post works

Links function

Layout clean

9️⃣ Push to GitHub

Create GitHub repo.

Then:

git add .
git commit -m "Initial site"
git push origin main

🔟 Deploy via Cloudflare Pages

In Cloudflare:

Pages → Create Project

Connect GitHub repo

Framework preset: Astro

Build command: npm run build

Output directory: dist

Deploy

1️⃣1️⃣ Connect Domain

In Cloudflare:

Add custom domain

Point to Pages project

Done.

📌 Workflow From Now On

To publish new post:

Write Markdown in:
src/content/blog/

Commit + push

Cloudflare auto-deploys

Publishing = 30 seconds.

Optional (Later)

Add:

/about

/contact

/press

RSS feed

Sitemap

But not now.