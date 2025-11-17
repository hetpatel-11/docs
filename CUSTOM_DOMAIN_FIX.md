# Custom Domain Fix - Showing Starter Kit

## Problem
- ✅ `authagent.mintlify.app` works (shows Auth Agent docs)
- ❌ `docs.auth-agent.com` shows starter kit

## Root Cause
The custom domain `docs.auth-agent.com` is connected to a **different Mintlify project** (likely the starter kit project), not your Auth Agent project.

## Solution

### Step 1: Check Current Custom Domain
1. Go to Mintlify Dashboard
2. Select the **"authagent"** project (the one that works on `authagent.mintlify.app`)
3. Go to **Settings → Deployment → Custom Domain**
4. Check what domain is configured

### Step 2: Disconnect Custom Domain from Wrong Project
1. If you see `docs.auth-agent.com` connected to a **different project** (starter kit):
   - Go to that project
   - **Settings → Deployment → Custom Domain**
   - **Disconnect** or **Remove** the custom domain

### Step 3: Connect Custom Domain to Correct Project
1. Go back to your **"authagent"** project (the working one)
2. **Settings → Deployment → Custom Domain**
3. Add `docs.auth-agent.com`
4. Follow DNS setup instructions if needed
5. Save

### Step 4: Verify DNS (if needed)
If you need to update DNS:
- Add a CNAME record: `docs.auth-agent.com` → `authagent.mintlify.app`
- Or follow Mintlify's specific DNS instructions

### Step 5: Wait for Propagation
- DNS changes can take a few minutes to propagate
- Mintlify will verify the domain connection
- Once verified, both domains will show the same content

## Verification

After fixing:
- ✅ `authagent.mintlify.app` → Auth Agent docs
- ✅ `docs.auth-agent.com` → Auth Agent docs (same content)

## Why This Happens

Mintlify allows multiple projects, and each can have custom domains. If:
- Project A (starter kit) has `docs.auth-agent.com`
- Project B (authagent) has `authagent.mintlify.app`

Then the custom domain will show Project A's content, even though Project B is correct.

## Quick Fix Checklist

1. ✅ Identify which project has `authagent.mintlify.app` working (this is your correct project)
2. ✅ Go to that project's Settings → Deployment → Custom Domain
3. ✅ Add/connect `docs.auth-agent.com` to this project
4. ✅ Remove `docs.auth-agent.com` from any other projects
5. ✅ Wait for DNS propagation (if DNS changed)

The repository is 100% correct. This is purely a Mintlify project/domain configuration issue.



















