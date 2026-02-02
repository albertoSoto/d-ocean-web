# d-ocean.com Setup Instructions

## Project Structure

```
d-ocean-web/
├── .github/workflows/deploy.yml  # GitHub Actions for auto-deployment
├── public/
│   ├── CNAME                     # Custom domain configuration
│   └── favicon.svg
├── src/
│   └── pages/
│       └── index.astro           # Homepage
├── astro.config.mjs              # Configured for d-ocean.com
├── package.json
└── tsconfig.json
```

## What's Configured

- **Astro** with static output for GitHub Pages
- **GitHub Actions workflow** that auto-deploys on push to `main`
- **CNAME file** for `d-ocean.com` custom domain

## To Complete the Setup

### 1. Push this repo to GitHub

### 2. Enable GitHub Pages
In your GitHub repo settings → Pages → set source to "GitHub Actions"

### 3. Configure DNS (Namecheap)

In Namecheap → Domain → Advanced DNS, configure these records:

**A Records (for root domain d-ocean.com):**

| Type | Host | Value |
|------|------|-------|
| A Record | @ | 185.199.108.153 |
| A Record | @ | 185.199.109.153 |
| A Record | @ | 185.199.110.153 |
| A Record | @ | 185.199.111.153 |

**CNAME Record (for www subdomain):**

| Type | Host | Value |
|------|------|-------|
| CNAME | www | albertosoto.github.io |

> **Important:** The Host for A records must be `@` (not `www`). The `@` symbol represents the root domain.

change  parkingpage.namecheap.com
for albertosoto.github.io

### 4. Wait for DNS Propagation

DNS changes can take 15 minutes to 48 hours to propagate globally.

### 5. Enable HTTPS

Once DNS propagates:
1. Go to GitHub repo → Settings → Pages
2. Click "Check again" next to your custom domain
3. Once verified, check "Enforce HTTPS"

## Troubleshooting

### Check DNS Propagation Status

Run these commands to verify DNS is working:

```bash
# Check root domain (should show 4 GitHub IPs)
dig d-ocean.com +short

# Check www subdomain (should show albertosoto.github.io and IPs)
dig www.d-ocean.com +short
```

**Expected output for root domain:**
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

### Common Issues

| Problem | Cause | Solution |
|---------|-------|----------|
| "DNS address could not be found" | DNS not propagated yet | Wait 15-60 minutes, then retry |
| "DNS check unsuccessful" in GitHub | A records have wrong Host | Change Host from `www` to `@` |
| HTTPS checkbox disabled | Domain not verified yet | Wait for DNS propagation, click "Check again" |
| Site loads on www but not root | A records not propagated | Wait longer, www propagates faster |

### Online DNS Checkers

- https://dnschecker.org/#A/d-ocean.com
- https://www.whatsmydns.net/#A/d-ocean.com



What to do now:
1. Try https://www.d-ocean.com - it should load
2. Wait 15-60 minutes for the root domain to propagate
3. Once d-ocean.com resolves, go to GitHub Pages settings and click "Check again"
4. After GitHub verifies the domain, the "Enforce HTTPS" checkbox will become available - check it

## Local Development

```bash
# Install dependencies
npm install

# Start dev server at http://localhost:4321
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```