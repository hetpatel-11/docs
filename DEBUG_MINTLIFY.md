# Mintlify Debugging Guide

## Problem
Live site at https://docs.auth-agent.com shows Mintlify starter kit instead of Auth Agent documentation.

## Verification Checklist

### ✅ Repository Content (CORRECT)
- Repository: `hetpatel-11/docs`
- Branch: `main` and `master` (both have latest)
- `docs.json` name: "Auth Agent" ✅
- `index.mdx` title: "Auth Agent" ✅
- No starter kit references in any files ✅
- All 19 pages exist and are listed in navigation ✅

### ✅ docs.json Structure (CORRECT)
```json
{
  "$schema": "https://mintlify.com/schema.json",
  "name": "Auth Agent",
  "theme": "mint",
  "navigation": {
    "groups": [ ... 8 groups, 19 pages ... ]
  }
}
```

### ❓ Mintlify Dashboard Configuration (NEEDS VERIFICATION)

**CRITICAL: Check these in Mintlify Dashboard:**

1. **Project Selection**
   - Are you viewing the CORRECT project?
   - Project name should be "Auth Agent" or similar
   - NOT "Mint Starter Kit" or default project

2. **Repository Connection**
   - Go to: Settings → Repository
   - Repository: Must be `hetpatel-11/docs`
   - NOT: `mintlify/starter` or any other repo
   - Branch: `main` (or `master` if configured)
   - Root Directory: Should be EMPTY (not `/docs` or anything else)

3. **Custom Domain**
   - Settings → Deployment → Custom Domain
   - Should be: `docs.auth-agent.com`
   - Make sure it's pointing to the CORRECT project

4. **Deployment Logs**
   - Check the latest deployment log
   - Look for:
     - "Successfully validated docs.json" ✅
     - "Successfully indexed X page(s)" (should be 19, not 1)
     - Repository URL in logs (should be `hetpatel-11/docs`)

## Common Issues

### Issue 1: Wrong Project Selected
**Symptom:** Deployment works but shows starter kit
**Fix:** Check project dropdown in Mintlify dashboard, select correct project

### Issue 2: Wrong Repository Connected
**Symptom:** Deployment shows different content
**Fix:** Settings → Repository → Verify `hetpatel-11/docs`

### Issue 3: Root Directory Misconfigured
**Symptom:** Mintlify can't find files
**Fix:** Settings → Repository → Root Directory should be EMPTY

### Issue 4: Cached Deployment
**Symptom:** Old content persists
**Fix:** Manually trigger redeploy in dashboard

## Action Items

1. **Verify Project in Dashboard**
   - Open Mintlify dashboard
   - Check project selector (top left)
   - Ensure you're viewing Auth Agent project, not starter kit

2. **Check Repository Settings**
   - Settings → Repository
   - Verify: `hetpatel-11/docs`
   - Verify: Branch `main`
   - Verify: Root Directory is EMPTY

3. **Check Deployment Logs**
   - View latest deployment
   - Verify it says "Successfully indexed 19 page(s)"
   - If it says "1 page(s)", navigation structure is wrong

4. **Manual Redeploy**
   - Trigger a manual redeploy
   - Wait for completion
   - Check if content updates

5. **Delete Starter Kit Project (if exists)**
   - If you see a "Mint Starter Kit" project
   - Delete it to avoid confusion
   - Settings → Delete Project

## Current Status

- ✅ Repository has correct content
- ✅ docs.json is correctly formatted
- ✅ All files exist
- ❓ Mintlify dashboard configuration (needs manual verification)
- ❓ Project selection (needs manual verification)

## Next Steps

**YOU MUST CHECK THE MINTLIFY DASHBOARD MANUALLY:**

1. Go to https://dashboard.mintlify.com
2. Check which project you're viewing
3. Verify repository connection
4. Check deployment logs
5. Report back with findings

The code is 100% correct. The issue is in Mintlify's configuration or project selection.

