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

1. Push this repo to GitHub

2. In your GitHub repo settings → Pages → set source to "GitHub Actions"

3. Configure your DNS for `d-ocean.com`:
   - Add `A` records pointing to GitHub's IPs:
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`
   - Or add a `CNAME` record pointing to `<your-username>.github.io`

change  parkingpage.namecheap.com 
for albertosoto.github.io

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