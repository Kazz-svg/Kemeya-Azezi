# Kemeya Azezi

Source for [kemeyaazezi.com](https://kemeyaazezi.com) — a reference site
about the origins, culture and science of tea (and coffee), written by
Kemeya Azezi.

There's no build step: it's plain HTML and CSS, so any page can be opened
directly in a browser or edited by hand.

The site intentionally avoids first-person "about me" framing in its
visible copy (no "Hello, I'm...", no location-heavy taglines) — identity
signals for search live in structured data (JSON-LD `Person`/`ProfilePage`
on Home/About) and in substantive content (the Brussels section on the
Europe page) rather than in stated-outright prose. Keep that pattern when
adding new copy.

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
fr/                        French versions of every page above
nl/                        Dutch versions of every page above
assets/css/style.css       Shared stylesheet
sitemap.xml, robots.txt, CNAME, 404.html   SEO / hosting files
```

Every page shares the same header/nav and footer markup (copy-pasted, not
templated, since there's no build tool). When editing shared content like
the nav or footer links, update it across all pages.

## Deploying (GitHub Pages + GoDaddy domain)

The domain (`kemeyaazezi.com`) is registered on GoDaddy; the site itself is
hosted for free on **GitHub Pages**, serving directly from this repo.

This repo currently has one branch, `claude/kemeyaazezi-page-creation-1mhppb`
(it became the default branch since the repo was empty before this project
started) — use that branch name below, not `main`.

**One-time setup — GitHub side:**

1. Go to the repo on GitHub → **Settings → Pages**.
2. Under **Build and deployment → Source**, choose *Deploy from a branch*.
3. Set **Branch** to `claude/kemeyaazezi-page-creation-1mhppb` and folder
   to `/ (root)`. Click **Save**.
4. GitHub Pages will detect the `CNAME` file at the repo root (already set
   to `kemeyaazezi.com`) and configure the custom domain field automatically
   — you should see it appear under "Custom domain" within a minute or two.

**One-time setup — GoDaddy side:**

5. Log into GoDaddy → **My Products** → find `kemeyaazezi.com` → **DNS**
   (sometimes labelled "Manage DNS").
6. Delete any existing `A` record(s) for `@` (GoDaddy usually parks the
   domain with one by default — it needs to go).
7. Add these four **A** records, all with host `@`:
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153`,
   `185.199.111.153`
8. Add one **CNAME** record: host `www`, value `<your-github-username>.github.io`
   (this is your GitHub *account* username, e.g. `kazz-svg.github.io` —
   not the repo name).
9. Save. DNS changes can take anywhere from a few minutes to a few hours
   to propagate.

**Last step, back on GitHub:**

10. Once `https://kemeyaazezi.com` loads the site (check after DNS has
    propagated), go back to **Settings → Pages** and tick **Enforce HTTPS**.

After that, every push to `claude/kemeyaazezi-page-creation-1mhppb`
redeploys the live site automatically — no further steps needed.

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
- Every page has a French (`/fr/`) and Dutch (`/nl/`) version — Brussels'
  two official languages. Every EN/FR/NL trio cross-links via `hreflang`
  tags, and each page carries a small EN/FR/NL switcher in the header.

## Contact form

`contact.html` uses [Formspree](https://formspree.io) — a free service
that emails form submissions to you without publishing your address on
the page. It needs a one-time setup before it will actually deliver
anything:

1. Sign up free at formspree.io with whichever email you want messages
   sent to, and confirm your email.
2. Create a new form in the Formspree dashboard — it gives you an
   endpoint URL like `https://formspree.io/f/abc1234`.
3. In `contact.html`, replace `REPLACE_WITH_YOUR_FORM_ID` in the form's
   `action` attribute with that URL.

Until step 3 is done, the form is visible but won't send anywhere.

## Open items

- Wire up the contact form (see above).
- Add links to existing social profiles (YouTube, Substack, Twitter/X)
  once handles/URLs are confirmed. Placeholder `TODO(Kemeya)` comments
  mark where they go on `about.html` and its `/fr/` and `/nl/` versions.
