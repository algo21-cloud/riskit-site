# RiskIt website (riskit.gg)

Static landing page + privacy policy + terms of service for the RiskIt iOS app.

## Local preview

```bash
cd website
python3 -m http.server 8000
# open http://localhost:8000
```

## Structure

```
website/
├── index.html         # Landing page
├── privacy.html       # Privacy Policy
├── terms.html         # Terms of Service
├── CNAME              # GitHub Pages → riskit.gg
├── .nojekyll          # Disable Jekyll processing
└── assets/
    ├── site.css       # Brand-aligned dark theme
    ├── favicon.svg    # Gold diamond brand mark
    └── screenshots/   # iPhone 17 Pro screenshots
        └── hero-auth.png
```

## Deployment (GitHub Pages → riskit.gg)

```bash
# From the project root
cd website
git init
git add .
git commit -m "RiskIt website v1"
gh repo create riskit-site --public --source=. --remote=origin --push
gh repo edit --enable-pages --pages-branch=main
```

Then in Namecheap:
1. Domain List → riskit.gg → Manage → **Advanced DNS**
2. Add a CNAME record:
   - Type: `CNAME Record`
   - Host: `@` (or `www`)
   - Value: `<github-username>.github.io.` (with trailing dot)
   - TTL: Automatic
3. Add four A records (apex domain) pointing at GitHub Pages IPs:
   - `185.199.108.153`
   - `185.199.109.153`
   - `185.199.110.153`
   - `185.199.111.153`

DNS propagation: 1-24h. Then HTTPS auto-enables via Let's Encrypt.

## Updating after launch

Just push to the `main` branch — GitHub Pages auto-redeploys within 1-2 minutes.
