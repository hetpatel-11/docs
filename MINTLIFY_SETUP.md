# Mintlify Setup & Troubleshooting

## Current Setup
- **Docs Repo:** https://github.com/hetpatel-11/docs.git
- **Custom Domain:** docs.auth-agent.com (configured)

## If Mintlify isn't updating:

### Step 1: Verify GitHub Connection
1. Go to [Mintlify Dashboard](https://dashboard.mintlify.com)
2. Click on your project
3. Go to **Settings** → **GitHub App**
4. Make sure the GitHub app is installed and connected
5. Verify it has access to `hetpatel-11/docs` repo

### Step 2: Check Repository Configuration
In Mintlify Dashboard → **Settings** → **Repository**:
- **Repository:** `hetpatel-11/docs`
- **Branch:** `main` (or your default branch)
- **Root Directory:** Leave empty (if docs.json is in root) OR set to the folder containing docs.json

### Step 3: Trigger Manual Deployment
1. In Mintlify Dashboard → **Deployments**
2. Click **Redeploy** or **Trigger Deployment**
3. This will pull the latest from GitHub

### Step 4: Check Deployment Logs
1. Go to **Deployments** tab
2. Click on the latest deployment
3. Check for any errors in the build logs

### Step 5: Verify GitHub Webhook
1. Go to GitHub → `hetpatel-11/docs` repo
2. Settings → Webhooks
3. Check if Mintlify webhook is active
4. If missing, Mintlify should auto-create it when connected

## Common Issues:

### Issue: "Repository not found"
- **Fix:** Reconnect the GitHub app in Mintlify settings

### Issue: "docs.json not found"
- **Fix:** Check Root Directory setting - should be empty or the folder containing docs.json

### Issue: "Build failed"
- **Fix:** Check deployment logs for specific errors
- Common: Missing files, invalid docs.json syntax

### Issue: "Changes not deploying"
- **Fix:** 
  1. Make sure you're pushing to the correct branch (usually `main`)
  2. Check if webhook is active in GitHub
  3. Manually trigger deployment in Mintlify

## Quick Fix Commands:

```bash
# Verify docs.json is valid
cd docs
mintlify dev  # Should start local preview

# Check if files are committed
git status
git log --oneline -5  # Check recent commits
```

## Force Update:
1. In Mintlify Dashboard → Deployments
2. Click **Redeploy** button
3. Wait 1-2 minutes for deployment

