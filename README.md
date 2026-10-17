# iVizhin company site

The company site for **ivizhin.ai** (primary) and **ivizhin.com** (redirects to .ai).
Plain HTML, one stylesheet, no build step, no dependencies.

It is about the studio, not any one product: who we are, Farmgirl Finance, iVizhin Darts,
Legend's Stadium Basketball, Legend's Dragway, the Red Barn Ranch farm automation, Android and
Apple app work, managing the whole Farmhouse Getaways digital presence, and the history from
1996 on (Modern Arcade Machines, 2001, San Diego; source material in `K:\Websites\Modern Arcades`).

## How it goes live

```
edit a file -> commit to main -> push -> Netlify builds -> live (~30s)
```

Netlify project **ivizhin** deploys `main` of `FarmhouseGetaways/ivizhin` with `publish = "."`.
Never drag files onto Netlify; the repo is the source of truth.

## Domains

Until 14 Oct 2026 ivizhin.ai and ivizhin.com were aliases on the Farmgirl Finance site
(`fffarmgirl`). They were moved to this site that night. DNS is at directnic: apexes are A records
to Netlify's load balancer `75.2.60.5`, the www names are CNAMEs to `ivizhin.netlify.app`.

ivizhin.ai is primary; `netlify.toml` 301s ivizhin.com and www.ivizhin.com to it. One Let's Encrypt
certificate covers all four names.

**If ivizhin.ai goes dark again:** check `nslookup -type=NS ivizhin.ai 8.8.8.8`. Nameservers at
`emailverification.info` mean directnic's ICANN email check suspended it (that happened 24 Sep to
14 Oct 2026). ivizhin.ai has no privacy service, so the validation email goes to the registrant
address, corydzbinski@gmail.com, and Gmail files it in Spam and deletes it after 30 days. Netlify
issues ONE certificate for every name on the site and refuses domain changes while it waits, so a
dead .ai also takes ivizhin.com off HTTPS. Fix the verification, then Netlify → Domain management →
Verify DNS configuration.

## Files

| File | What |
|---|---|
| `index.html` | The one page |
| `thanks.html` | Contact form landing page |
| `404.html` | Not found |
| `css/site.css` | All styling. Bump `?v=` in `index.html` when it changes |
| `js/scroll-progress.js` | The thin line across the top that fills as the page scrolls. A copy: the master is `reports/scroll-progress/` in the projects folder, shared by all the sites |
| `images/` | Game photos (from the barn micro-site), product marks, Modern Arcades photos |
| `images/og-ivizhin-v3.jpg` | The link preview card (1200x630 JPEG). Only og:image + twitter:card in the head, the set that worked before: iPhone Messages over RCS showed a blank box when og:image:width/height/type/alt and twitter:image were added (16 Oct 2026) shown when ivizhin.ai is sent in a text or posted. Source `reports/ivizhin-og/og.html`, rendered with headless Chrome; a new version gets a new filename (`-v2`) |
| `images/apple-touch-icon-v1.png` | 180x180 icon for the preview's small logo and the iPhone home screen. Source `reports/ivizhin-og/icon.html` |

`images/*` is served as immutable for a year (`netlify.toml`). To change a picture, save it under a
**new filename** and update the `src`; overwriting the same name leaves visitors on the old one.

`images/modern-arcades-m3-900-v2.png` is the M3 cut out of its white studio background so it sits on
the card's blue. Made by `reports/ivizhin-m3-cutout/cutout.py` from `modern-arcades-m3-900.jpg`
(kept as the source): the cut sits 3 px inside the cabinet and the edge takes the cabinet's own
colour, because the photo's edge pixels are half white and showed as a light rim.

The contact form is a plain Netlify form named `contact` with a `bot-field` honeypot. Email
notifications for it live in the Netlify UI, not here.

## Copy rules

Plain, short sentences. Say what we build and what it does. No swagger, no mechanics.
Numbers that appear here and on a product site (price, game count) must agree with the product site.

Most of the copy is Cory's own wording (who we are, the games, the whole History timeline, 15 Oct
2026). When he sends a line, it goes on word for word; only typos and capitalisation get fixed
(IoT, its/it's), and those fixes are listed back to him. Facts in it that are his to keep straight:
the entertainment barn was built by someone else and automated by us; Legend's Stadium replaced a
failed automatic basketball scoring system; iVizhin itself dates from 2026 (`foundingDate` in the
JSON-LD), while "Building since 1996" is the people behind it.

Names in the History timeline (Farmhouse Getaways, iVizhin and the other businesses and builds) are
`<strong>` so they show in white. Keep that on new entries.
