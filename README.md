# Kind Mechanics site

Static, four pages, no build step, no JavaScript. Deployable as-is.

## Deploy (GitHub Pages, kindmechanics account)

1. Check which repo currently serves terminology.kindmechanics.com (its Settings > Pages will show that custom domain). Leave it alone.
2. Create a new public repo, e.g. `kindmechanics-site`. Upload these six files (web UI: Add file > Upload files works fine, no git required).
3. Repo Settings > Pages > Source: "Deploy from a branch", branch `main`, folder `/ (root)`. Save, wait a minute, confirm the temporary URL renders (all asset paths here are relative, so it works under a subpath).
4. GoDaddy DNS for kindmechanics.com:
   - Remove whatever currently points the apex at Buttondown (likely GoDaddy "domain forwarding").
   - Add four A records on `@`: 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153.
   - Optionally add a CNAME on `www` -> kindmechanics.github.io.
   - Touch nothing else: not the `terminology` CNAME, not MX, not TXT.
5. Back in the repo's Pages settings, set custom domain: kindmechanics.com. Wait for the DNS check to pass, then tick "Enforce HTTPS" once the certificate issues (can take up to an hour).
6. Verify the domain for the whole account: GitHub account Settings > Pages > Add a verified domain > kindmechanics.com, and add the TXT record it gives you at GoDaddy. This prevents anyone else ever claiming the domain on GitHub Pages.
7. Test all four: https://kindmechanics.com loads the new site; https://terminology.kindmechanics.com still loads; a test mail to brian@kindmechanics.com arrives; the subscribe form submits.

## Before deploying — TODOs in the files

- The April archive mystery is solved: it is https://terminology.kindmechanics.com/ (Terminology Tuesday cards + newsletter series links). It is now linked from the nav, home, programmes and writing pages. Find where it is hosted before touching DNS: in GoDaddy DNS, look at the CNAME record for `terminology` — a target ending in github.io means GitHub Pages, pages.dev means Cloudflare Pages, netlify.app means Netlify. Or run: dig CNAME terminology.kindmechanics.com
- `writing.html`: "A Soft Room With No Exit" link is a placeholder (`#`). Add the LinkedIn article URL.
- Timing: the award shortlisting appears on `index.html` and `work.html`. The finalists are public on the awards site, but if you want Datavant's PR to land first, deploy after their posts go out (or temporarily delete the Recognition section from index.html).
- `work.html` names Datavant. Given the press push this is presumably fine, but worth a quick sanity check with comms that naming the employer on your personal project site is fine by them.
- Buttondown: keep the newsletter itself on Buttondown; the subscribe forms post to the standard Buttondown embed endpoint for the `kindmechanics` account. Once the site is live, consider trimming the Buttondown profile page down to a short blurb + link back to kindmechanics.com so there aren't two competing homepages.

## Content decisions already made in this build

- No status claims anywhere (nothing "in review", no dates that rot).
- The SocArXiv preprint is linked as a preprint, nothing more.
- Research scope on writing.html is deliberately narrow: the workplace-and-cognition strand only. Wider research (AI, consciousness) is not claimed by this site; "A Soft Room With No Exit" is framed as a crossing point, which keeps the bridge visible without moving anything else across it.
- ORCID and credentials live on the About page, not the homepage.
