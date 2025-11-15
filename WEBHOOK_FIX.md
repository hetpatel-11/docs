# Fix Mintlify Webhook - Step by Step

## Your Current Settings (Correct):
- Repository: `hetpatel-11/docs` ✅
- Branch: `main` ✅
- Monorepo: OFF (correct since docs.json is in root) ✅

## The Problem:
Webhook isn't triggering on GitHub pushes.

## Fix Steps:

### Step 1: Check GitHub Webhook Status
1. Go to: https://github.com/hetpatel-11/docs/settings/hooks
2. Look for a webhook from Mintlify
3. Check:
   - Status should be **Active** (green)
   - Recent deliveries should show recent pushes
   - If webhook is missing or red → Go to Step 2

### Step 2: Reconnect GitHub App (Force Webhook Recreation)
1. In Mintlify Dashboard → **Settings** → **GitHub App**
2. Click **Disconnect** or **Reconnect**
3. Re-authorize Mintlify to access your repos
4. Make sure `hetpatel-11/docs` is selected
5. This will recreate the webhook

### Step 3: Test Webhook Manually
1. In GitHub → `hetpatel-11/docs` → Settings → Webhooks
2. Find the Mintlify webhook
3. Click on it → **Recent Deliveries** tab
4. Click **Redeliver** on the latest delivery
5. Check if Mintlify receives it (should show in Mintlify deployments)

### Step 4: Verify Webhook Events
The webhook should listen for:
- ✅ Push events
- ✅ Repository events (optional)

If these aren't checked, that's the issue.

### Step 5: Test with a Real Push
1. Make a small change in your docs repo:
   ```bash
   # In your docs repo
   echo "<!-- test -->" >> index.mdx
   git add .
   git commit -m "Test webhook"
   git push origin main
   ```
2. Immediately check GitHub → Webhooks → Recent Deliveries
3. You should see a new delivery within seconds
4. Check Mintlify → Deployments → Should auto-deploy

### Step 6: Check GitHub App Permissions
1. Go to: https://github.com/settings/applications
2. Find **Mintlify** in authorized apps
3. Click **Configure**
4. Make sure it has access to `hetpatel-11/docs`
5. Permissions should include:
   - Repository access
   - Webhook permissions

## Alternative: Disconnect & Reconnect Everything
1. Mintlify → Settings → GitHub App → **Disconnect**
2. Mintlify → Settings → Repository → **Disconnect**
3. Reconnect both from scratch
4. This forces a complete refresh

## If Still Not Working:
The issue might be:
- GitHub webhook rate limiting
- Mintlify service issue
- Repository visibility (if private, check app permissions)

Try Step 2 first (reconnect GitHub app) - that fixes it 90% of the time.

