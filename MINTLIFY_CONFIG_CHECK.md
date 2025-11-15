# Mintlify Configuration Check

## Critical Settings to Verify

Go to **Mintlify Dashboard → Settings → Repository** and verify:

### ✅ Required Settings:
1. **Repository**: `hetpatel-11/docs`
2. **Branch**: `main`
3. **Root Directory**: **MUST BE EMPTY** (leave blank)
   - ⚠️ If this is set to any value (like `docs/` or `/`), Mintlify won't find your files!

### Why Root Directory Matters:
- Your `docs.json` is in the **root** of the `hetpatel-11/docs` repository
- If Root Directory is set to anything other than empty, Mintlify will look in the wrong place
- This is the #1 reason why live site doesn't match localhost preview

## Verification Steps:

1. **Check Root Directory**:
   - Go to: https://dashboard.mintlify.com → Your Project → Settings → Repository
   - **Root Directory field should be completely empty**
   - If it has any value, clear it and save

2. **Verify Branch**:
   - Should be: `main`
   - Not `master` or any other branch

3. **Trigger Redeploy**:
   - After fixing Root Directory, go to Deployments
   - Click "Redeploy" to rebuild with correct settings

4. **Check Build Logs**:
   - After redeploy, check the deployment logs
   - Should show: "Found docs.json" and successful build
   - If you see "docs.json not found", Root Directory is still wrong

## Local vs Production Mismatch:

If your localhost preview (`mint dev`) shows correct content but production doesn't:
- **99% of the time**: Root Directory is misconfigured
- **1% of the time**: Branch is wrong or files weren't committed

## Quick Test:
After fixing Root Directory, wait 1-2 minutes for deployment, then:
- Hard refresh: `Cmd+Shift+R` (Mac) or `Ctrl+Shift+R` (Windows)
- Should now match your localhost preview

