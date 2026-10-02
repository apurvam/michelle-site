# mschaffnerlcsw.com

Static website for Michelle Schaffner, LCSW-R. It was migrated off Wix in October 2026.

It's plain HTML and CSS with no build step, framework or dependencies.

```
index.html                  Home
about-me.html               /about-me
services-provided.html      /services-provided
helpful-information.html    /helpful-information
payment-and-policies.html   /payment-and-policies
contact-me.html             /contact-me
404.html                    Not-found page
styles.css                  All styling
images/                     Photos and leaf banner
vercel.json                 Clean URLs (no .html), redirect from old /blog-1
sitemap.xml, robots.txt, favicon.svg
```

The URLs are the same as on the old Wix site, so search results and bookmarks keep working.

## Editing

Edit the `.html` file for the page you want to change. The header, nav and footer are repeated in every page. If you change the phone number, address or menu, update all seven HTML files (including `404.html`):

```sh
grep -l "391-4587" *.html
```

## Preview locally

```sh
npx serve .
```

Then open http://localhost:3000.

## Deploy to Vercel

1. Push this repo to GitHub.
2. In Vercel, choose **Add New → Project** and import the repo. Use **Other** as the framework preset, leave the build command empty, and set the output directory to `.` (the root).
3. Each push to `main` deploys automatically.

### Move the domain

1. In the Vercel project, go to **Settings → Domains** and add `www.mschaffnerlcsw.com` and `mschaffnerlcsw.com`. Set the apex domain to redirect to `www`.
2. Vercel shows the DNS records to create, usually an `A` record for `@` and a `CNAME` for `www` pointing to `cname.vercel-dns.com`. Add them wherever the domain's DNS is managed.
3. If the domain is registered through Wix, either change the records in Wix's DNS settings or transfer the domain to another registrar (Cloudflare, Porkbun, Namecheap) first. Wix domain renewal is separate from the Wix site plan.
4. Once the Vercel site is live on the domain, cancel the Wix premium plan, but don't let the domain lapse.

As of October 2026, `mschaffnerlcsw.com` is registered with Wix (created 2023-11-30, **expires 2026-11-30**) and uses Wix nameservers. It has no MX records, so no email depends on it. The contact address is Gmail.
