# URGENT: Mintlify Showing Wrong Docs

## Problem
Mintlify is showing "Mint Starter Kit" instead of "Auth Agent" docs.

## Root Cause
Mintlify is likely connected to the **WRONG REPOSITORY** or has incorrect settings.

## IMMEDIATE FIX STEPS:

### Step 1: Verify Repository Connection
1. Go to: https://dashboard.mintlify.com
2. Select your "Auth Agent" project
3. Go to: **Settings → Repository**
4. **CRITICAL CHECK:**
   - **Repository MUST BE:** `hetpatel-11/docs`
   - **NOT:** `mintlify/starter` or any other repo
   - **NOT:** `auth-agent-front-main` or any other repo

### Step 2: Verify Branch
- **Branch MUST BE:** `main`
- **NOT:** `master` or any other branch

### Step 3: Verify Root Directory
- **Root Directory MUST BE:** **EMPTY** (completely blank)
- Your `docs.json` is in the root of `hetpatel-11/docs`
- If Root Directory has ANY value, Mintlify won't find your files

### Step 4: If Repository is Wrong - RECONNECT
1. In **Settings → Repository**
2. Click **Disconnect**
3. Click **Connect Repository**
4. Search for: `hetpatel-11/docs`
5. Select it
6. **Branch:** `main`
7. **Root Directory:** Leave EMPTY
8. Click **Save**

### Step 5: Force Redeploy
1. Go to **Deployments**
2. Click **Redeploy** (or **Trigger Deployment**)
3. Wait 2-3 minutes
4. Check deployment logs for errors

### Step 6: Verify Deployment Logs
After redeploy, check the logs:
- Should see: "Found docs.json"
- Should see: "Building documentation"
- Should NOT see: "docs.json not found" or "Repository not found"

## Verification Commands (Run Locally):

```bash
cd docs
# Verify correct repo
git remote -v
# Should show: origin https://github.com/hetpatel-11/docs.git

# Verify correct branch
git branch
# Should show: * main

# Verify docs.json name
cat docs.json | grep '"name"'
# Should show: "name": "Auth Agent"

# Verify index.mdx
head -5 index.mdx
# Should show: title: "Auth Agent"
```

## If Still Not Working:

### Option A: Complete Reconnection
1. **Settings → GitHub App → Disconnect**
2. **Settings → GitHub App → Install GitHub App**
3. Re-authorize access to `hetpatel-11/docs`
4. Go back to **Settings → Repository**
5. Connect `hetpatel-11/docs` with branch `main`, root directory empty

### Option B: Check for Multiple Projects
- You might have multiple Mintlify projects
- Make sure you're editing the correct one (the one with domain `docs.auth-agent.com`)

### Option C: Contact Mintlify Support
If nothing works, the issue might be on Mintlify's side. Contact support with:
- Repository: `hetpatel-11/docs`
- Branch: `main`
- Domain: `docs.auth-agent.com`
- Issue: Showing "Mint Starter Kit" instead of "Auth Agent" content

## Current Correct Configuration:
- **Repository:** `hetpatel-11/docs`
- **Branch:** `main`
- **Root Directory:** (empty)
- **docs.json location:** Root of repository
- **Name in docs.json:** "Auth Agent"
- **Index page:** Shows "Welcome to Auth Agent"

