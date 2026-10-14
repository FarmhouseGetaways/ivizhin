# iVizhin company site

The company site for **ivizhin.ai** (primary) and **ivizhin.com** (redirects to .ai).
Plain HTML, one stylesheet, no build step, no dependencies.

It is about the studio, not any one product: who we are, Farmgirl Finance, iVizhin Darts,
Legend's Stadium Basketball, Legend's Dragway, the Red Barn Ranch farm automation, Android and
Apple app work, managing the whole Farmhouse Getaways digital presence, and the Modern Arcade
Machines history (2001, San Diego; source material in `K:\Websites\Modern Arcades`).

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

## Files

| File | What |
|---|---|
| `index.html` | The one page |
| `thanks.html` | Contact form landing page |
| `404.html` | Not found |
| `css/site.css` | All styling. Bump `?v=` in `index.html` when it changes |
| `images/` | Game photos (from the barn micro-site), product marks, Modern Arcades photos |

The contact form is a plain Netlify form named `contact` with a `bot-field` honeypot. Email
notifications for it live in the Netlify UI, not here.

## Copy rules

Plain, short sentences. Say what we build and what it does. No swagger, no mechanics.
Numbers that appear here and on a product site (price, game count) must agree with the product site.
