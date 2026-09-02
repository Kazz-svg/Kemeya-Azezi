# Kemeya Azezi

Source for [kemeyaazezi.com](https://kemeyaazezi.com) — a personal,
non-commercial site about the origins, culture and science of tea (and a
bit of coffee), written by Kemeya Azezi.

Nothing on this site is for sale. There's no build step: it's plain HTML
and CSS, so any page can be opened directly in a browser or edited by hand.

## Structure

```
index.html              Home
about.html               About
contact.html             Contact
tea/index.html            Tea hub (what tea is, how it's processed)
coffee/index.html         Coffee hub
tea-specialists.html      Historical & modern tea specialists
papers-science.html       Tea chemistry / science overview
blog/                     Blog index + posts
continents/                One page per continent's tea culture
  asia.html, africa.html, europe.html, north-america.html,
  south-america.html, oceania.html
assets/css/style.css       Shared stylesheet
sitemap.xml, robots.txt, CNAME, 404.html   SEO / hosting files
```

Every page shares the same header/nav and footer markup (copy-pasted, not
templated, since there's no build tool). When editing shared content like
the nav or footer links, update it across all pages.

## Deploying (GitHub Pages + GoDaddy domain)

The domain (`kemeyaazezi.com`) is registered on GoDaddy; the site itself is
hosted for free on **GitHub Pages**, serving directly from this repo.

**One-time setup:**

1. On GitHub: repo **Settings → Pages → Build and deployment → Source**:
   choose *Deploy from a branch*, branch `main`, folder `/ (root)`. Save.
2. GitHub Pages will detect the `CNAME` file at the repo root (already
   set to `kemeyaazezi.com`) and configure the custom domain automatically.
3. On GoDaddy: go to the domain's **DNS** settings and add:
   - Four **A** records for `@` pointing to GitHub Pages' IPs:
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`,
     `185.199.111.153`
   - One **CNAME** record: host `www`, pointing to
     `<github-username>.github.io`
   - Remove/replace any existing GoDaddy "parked domain" A records first.
4. Back in GitHub Pages settings, once DNS propagates (can take up to a
   few hours), tick **Enforce HTTPS**.

After that, every push to `main` redeploys the live site automatically —
no further steps needed.

## SEO notes

- Every page has a unique `<title>`, meta description, and canonical URL.
- `sitemap.xml` lists all pages — submit it in
  [Google Search Console](https://search.google.com/search-console) once
  the domain is live, and verify ownership there (GoDaddy lets you add a
  DNS TXT record for verification).
- `index.html` and `about.html` carry `Person`/`ProfilePage` structured
  data (JSON-LD) naming Kemeya Azezi, to help Google associate the site
  directly with searches for that name.
- The Europe continent page has a dedicated Brussels section — the main
  on-page signal for "kemeya azezi brussels" searches.
- Currently English-only. French/Dutch versions of the highest-priority
  pages (Home, About, Europe) are the natural next step, since Brussels
  is officially bilingual.

## Open items

- `contact.html` has a placeholder — decide on a public contact method
  (an email you're comfortable publishing, or links to social profiles).
- Consider setting up matching social profiles (Instagram, etc.) once
  ready, and linking them from the site (and vice versa) to reinforce
  identity signals for the name search.
