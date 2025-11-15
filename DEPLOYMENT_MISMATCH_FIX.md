# Fix: Editor Shows Correct Files But Live Site Shows Starter Kit

## Problem
- ✅ Mintlify Editor shows your Auth Agent files correctly
- ✅ Files are in the repository
- ❌ Live site (docs.auth-agent.com) still shows starter kit

## Root Cause
The **deployment** is not using the latest files or is cached. The editor and deployment can be out of sync.

## Solution Steps

### Step 1: Verify Deployment Branch
In Mintlify Dashboard → **Settings → Repository**:
- **Branch:** Must match the branch you're editing
- If editor shows `main`, deployment must use `main`
- If editor shows `master`, deployment must use `master`

### Step 2: Force Fresh Deployment
1. Go to **Deployments** tab
2. Click **"Redeploy"** or **"Trigger Deployment"**
3. **IMPORTANT:** Wait for it to complete (2-3 minutes)
4. Check deployment logs

### Step 3: Check Deployment Logs
After redeploy, check logs should show:
- ✅ "Cloning repository hetpatel-11/docs"
- ✅ "Found mint.json" or "Found docs.json"
- ✅ "Building with name: Auth Agent"
- ✅ "Deployment successful"

If logs show:
- ❌ "Mint Starter Kit" → Wrong project selected
- ❌ "docs.json not found" → Root Directory is wrong
- ❌ Wrong repository → Repository setting is incorrect

### Step 4: Clear Browser Cache
After deployment completes:
- Hard refresh: `Cmd+Shift+R` (Mac) or `Ctrl+Shift+R` (Windows)
- Or use incognito/private window
- Visit: `docs.auth-agent.com`

### Step 5: Verify Root Directory
**Settings → Repository → Root Directory:**
- **MUST BE EMPTY** (completely blank)
- If it has ANY value, Mintlify looks in wrong folder
- Your `mint.json` is in the root, so this must be empty

## Why This Happens

1. **Editor vs Deployment Mismatch:**
   - Editor shows files from one branch
   - Deployment uses a different branch
   - Solution: Match branches

2. **Cached Deployment:**
   - Old deployment is cached
   - Solution: Force redeploy

3. **Root Directory Wrong:**
   - Deployment can't find `mint.json`
   - Falls back to starter kit
   - Solution: Set Root Directory to empty

## Quick Checklist

- [ ] Editor branch matches deployment branch
- [ ] Root Directory is EMPTY
- [ ] Force redeploy triggered
- [ ] Deployment logs show "Auth Agent" not "Starter Kit"
- [ ] Browser cache cleared
- [ ] Hard refresh performed

## Current Status

✅ Files are correct in repository
✅ Editor shows correct files
✅ Latest commit pushed: `de411fb`

**Action Required:** Force redeploy in Mintlify dashboard and verify deployment logs.

