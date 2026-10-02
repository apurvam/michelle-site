# mschaffnerlcsw.com

Static website for Michelle Schaffner, LCSW-R. It was migrated off Wix in October 2026 and is hosted on Cloudflare Pages.

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
_redirects                  Redirect from old /blog-1 (Cloudflare Pages)
vercel.json                 Same, for Vercel (unused)
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

## Hosting: Cloudflare Pages

The site is the Cloudflare Pages project `mschaffnerlcsw` at https://mschaffnerlcsw.pages.dev. It's free, and commercial use is allowed. Cloudflare drops `.html` from URLs automatically, `_redirects` sends the old `/blog-1` URL to the home page, and `404.html` is the not-found page. (`vercel.json` does the same on Vercel if the site ever moves there.)

### Deploy

If the project is connected to this GitHub repo (Settings → Builds → Connect to Git), each push to `main` deploys automatically. Use these build settings: framework preset **None**, build command empty, output directory `/`.

To deploy by hand without the README:

```sh
mkdir -p /tmp/site && cp -R *.html styles.css favicon.svg robots.txt sitemap.xml _redirects images /tmp/site/
npx wrangler pages deploy /tmp/site --project-name mschaffnerlcsw --branch main
```

### Move the domain

1. In the Pages project, open **Custom domains** and add `www.mschaffnerlcsw.com`, then `mschaffnerlcsw.com`.
2. The easiest route is moving the domain's DNS to Cloudflare: add the domain under **Websites** in Cloudflare and change the nameservers at the registrar (Wix) to the two that Cloudflare gives you. Cloudflare then creates the Pages records itself. You can also transfer the registration to Cloudflare Registrar, at cost.
3. Once the site loads on the domain, cancel the Wix premium plan, but don't let the domain lapse.

As of October 2026, `mschaffnerlcsw.com` is registered with Wix (created 2023-11-30, **expires 2026-11-30**) and uses Wix nameservers. It has no MX records, so no email depends on it. The contact address is Gmail.
