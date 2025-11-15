# Docs Deployment Guide

## Option 1: Mintlify Hosting with Custom Domain (Recommended)

### Step 1: Connect GitHub to Mintlify
1. Go to [Mintlify Dashboard](https://dashboard.mintlify.com)
2. Click **Connect Repository**
3. Select your GitHub repo: `auth-agent-front-main`
4. Select the `docs` folder as the root directory

### Step 2: Add Custom Domain
1. In Mintlify Dashboard → Your Project → Settings → Domains
2. Click **Add Custom Domain**
3. Enter: `docs.auth-agent.com`
4. Mintlify will provide DNS records to add

### Step 3: Configure DNS in Cloudflare
1. Go to Cloudflare Dashboard → DNS → Records
2. Add CNAME record:
   ```
   Type: CNAME
   Name: docs
   Target: [provided by Mintlify]
   Proxy status: Proxied (orange cloud)
   ```

### Step 4: Update Redirect
Once DNS propagates (~5 minutes), update the redirect in your main app:

```typescript
// apps/web/src/app/docs/page.tsx
redirect("https://docs.auth-agent.com");
```

**Done!** Your docs will be live at `https://docs.auth-agent.com`

---

## Option 2: Migrate to Cloudflare Pages (Advanced)

If you want everything on Cloudflare, you'll need to migrate from Mintlify to a static site generator:

### Recommended: Docusaurus
- Built by Meta, widely used
- Easy MDX support
- Great SEO
- Can deploy to Cloudflare Pages

### Migration Steps:
1. Install Docusaurus in `docs/` folder
2. Convert MDX files (mostly compatible)
3. Update navigation structure
4. Build static site
5. Deploy to Cloudflare Pages

**Time estimate:** 2-4 hours

---

## Current Setup

Your docs are currently configured for Mintlify:
- `docs.json` - Mintlify configuration
- `.mdx` files - Content files
- Logo and assets in `logo/` and `images/`

The main app redirects `/docs` to `https://docs.auth-agent.com` (currently pointing to Mintlify).

---

## Recommendation

**Use Option 1** - Mintlify hosting is:
- ✅ Free
- ✅ Fast (global CDN)
- ✅ Zero maintenance
- ✅ Automatic deployments from GitHub
- ✅ Built-in search
- ✅ Great developer experience

You can always migrate later if needed.

