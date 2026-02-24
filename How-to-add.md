How to add a blog post
======================

Follow these steps to add a new blog post to this Astro site.

1. Create a new Markdown file in `src/content/blog/`.
   - Example filename: `2026-02-08-my-new-post.md` or `my-new-post.md`

2. Add frontmatter at the top of the file:

```
---
title: "Your Post Title"
description: "Short summary (optional)"
date: 2026-02-08
---
```

3. Write your post in Markdown below the frontmatter.

4. Test locally:

```bash
npm run dev
# open http://localhost:3000
```

5. When ready, commit and push to GitHub:

```powershell
git add src/content/blog/your-post-file.md
git commit -m "Add: Your Post Title"
git push origin main
```

6. Cloudflare Pages (if connected) will auto-deploy after the push.

Notes:
- Use an ISO date in the `date` field (YYYY-MM-DD). The site uses the `blog` collection schema.
- Keep the description short — it appears on the homepage list.
- If you want, I can create the file and open a PR or push it for you.
