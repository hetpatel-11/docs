# Fix Mintlify Auto-Deployments

## Issue: Docs not updating automatically

Your dashboard shows "Manual Update" which means automatic deployments from GitHub aren't working.

## Fix Steps:

### 1. Check Repository Settings
In Mintlify Dashboard:
1. Go to **Settings** → **Repository**
2. Verify:
   - **Repository:** `hetpatel-11/docs`
   - **Branch:** `main` (should match your default branch)
   - **Root Directory:** 
     - If `docs.json` is in the root: Leave **empty**
     - If `docs.json` is in a subfolder: Enter the folder name (e.g., `docs/`)

### 2. Reconnect Repository (Force Webhook Refresh)
1. In **Settings** → **Repository**
2. Click **Disconnect**
3. Click **Connect Repository** again
4. Select `hetpatel-11/docs`
5. This will recreate the webhook

### 3. Verify GitHub Webhook
1. Go to: https://github.com/hetpatel-11/docs/settings/hooks
2. You should see a webhook from Mintlify
3. Check:
   - Status: **Active** (green)
   - Events: Should include "Push" events
4. If missing or inactive, reconnect in Mintlify

### 4. Test Webhook
1. Make a small change to any `.mdx` file in your docs repo
2. Commit and push:
   ```bash
   git add .
   git commit -m "Test auto-deploy"
   git push origin main
   ```
3. Check Mintlify Dashboard → **Deployments** within 1-2 minutes
4. Should see a new deployment triggered automatically

### 5. Check Branch Name
Make sure Mintlify is watching the correct branch:
- If your default branch is `main` → Set to `main`
- If it's `master` → Set to `master`
- Settings → Repository → Branch

### 6. Root Directory Issue
If your `docs.json` is in a subfolder:
- **Wrong:** Root Directory empty when docs.json is in `docs/` folder
- **Correct:** Root Directory = `docs/` (the folder containing docs.json)

## Quick Test:
1. Edit any file in `hetpatel-11/docs` repo
2. Push to `main` branch
3. Wait 1-2 minutes
4. Check Mintlify → Deployments
5. Should auto-deploy (not show "Manual Update")

## If Still Not Working:
1. Check GitHub repo permissions:
   - Go to GitHub Settings → Applications → Authorized GitHub Apps
   - Find "Mintlify" → Configure → Make sure it has access to `hetpatel-11/docs`
2. Try disconnecting and reconnecting the entire GitHub app:
   - Mintlify Dashboard → Settings → GitHub App → Disconnect
   - Then reconnect and authorize

