# Custom Domain Setup - Fix Starter Kit Issue

## Current Status
- ✅ `authagent.mintlify.app` → Shows Auth Agent docs (CORRECT)
- ❌ `docs.auth-agent.com` → Shows starter kit (WRONG PROJECT)

## Solution: Connect Custom Domain to Correct Project

### Step 1: Go to Correct Project
1. Open Mintlify Dashboard: https://dashboard.mintlify.com
2. **Select the "authagent" project** (the one where `authagent.mintlify.app` works)
3. This is your CORRECT project with Auth Agent content

### Step 2: Check Current Custom Domain
1. In the "authagent" project, go to: **Settings → Deployment → Custom Domain**
2. Check if `docs.auth-agent.com` is listed:
   - If **NOT listed** → Continue to Step 3
   - If **listed but not working** → Check DNS (Step 4)

### Step 3: Add Custom Domain to Correct Project
1. In **Settings → Deployment → Custom Domain**
2. Enter: `docs.auth-agent.com`
3. Click **"Add domain"**
4. Mintlify will show DNS instructions

### Step 4: Configure DNS
1. Go to your domain provider (where `auth-agent.com` is registered)
2. Add a CNAME record:
   ```
   Type: CNAME
   Name: docs
   Value: cname.vercel-dns.com.
   ```
   **Note:** Mintlify uses Vercel for hosting, so the CNAME points to Vercel's DNS.
3. Save the DNS record

### Step 5: Remove from Wrong Project (if needed)
If `docs.auth-agent.com` is connected to a different project (starter kit):
1. Go to that project
2. **Settings → Deployment → Custom Domain**
3. **Remove** or **Disconnect** `docs.auth-agent.com`
4. Then add it to the correct project (Step 3)

### Step 6: Wait for Propagation
- DNS changes: 1-24 hours (usually faster)
- TLS certificate: Automatic, within a few hours
- Verify DNS: https://dnschecker.org

## Verification

After setup:
- ✅ `authagent.mintlify.app` → Auth Agent docs
- ✅ `docs.auth-agent.com` → Auth Agent docs (same content)

## DNS Record Example

```
Type: CNAME
Name: docs
Value: cname.vercel-dns.com.
TTL: Auto (or 3600)
```

**Important:** Mintlify uses Vercel for hosting, so the CNAME must point to `cname.vercel-dns.com.` (not `cname.mintlify-dns.com.`)

## Verify DNS Configuration

1. Go to: https://dnschecker.org
2. Enter domain: `docs.auth-agent.com`
3. Select record type: **CNAME**
4. Click "Search"
5. Verify it resolves to: `cname.vercel-dns.com.`

If it doesn't resolve correctly, update your DNS record at your domain provider.

## Important Notes

1. **Only ONE project can have a custom domain** - Make sure it's removed from the starter kit project
2. **DNS must point to Mintlify** - The CNAME must be `cname.mintlify-dns.com.`
3. **Canonical URL added** - I've added `seo.metatags.canonical` to `docs.json` for SEO

## Quick Checklist

- [ ] Identified correct project: "authagent" (where subdomain works)
- [ ] Added `docs.auth-agent.com` to correct project
- [ ] Removed `docs.auth-agent.com` from wrong project (if exists)
- [ ] Configured DNS CNAME record
- [ ] Waited for DNS propagation
- [ ] Verified both domains show same content

The repository is correct. This is purely a Mintlify dashboard configuration issue.

