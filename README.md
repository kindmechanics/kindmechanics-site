# Kind Mechanics site

Static, four pages, no build step, no JavaScript required for the site itself. Deployable as-is to GitHub Pages.

## Files

- `index.html` — homepage and main routes into the work
- `work.html` — Neurodiversity Awareness Month and Terminology Tuesday
- `writing.html` — archive highlights, essays, research and optional Buttondown subscription
- `about.html` — project background, principles, contact and site accessibility note
- `style.css` — shared visual system

The site currently uses a text wordmark in the header. Each HTML file contains a comment marking the place to swap in the original Kind Mechanics logo once the logo asset is added to the repository.

## Deploy (GitHub Pages, kindmechanics account)

1. Leave the repository serving `terminology.kindmechanics.com` alone.
2. Upload/replace the five site files above in the `kindmechanics-site` repository.
3. In repo **Settings → Pages**, use **Deploy from a branch**, branch `main`, folder `/ (root)`.
4. Confirm the temporary GitHub Pages URL renders correctly before changing DNS.
5. In GoDaddy DNS for `kindmechanics.com`:
   - remove the existing apex forwarding/record that points the root domain at Buttondown;
   - add GitHub Pages A records on `@`:
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`
   - optionally add `www` as a CNAME to `kindmechanics.github.io`;
   - do **not** change the `terminology` CNAME, MX records or unrelated TXT records.
6. Back in the repo's Pages settings, set the custom domain to `kindmechanics.com`.
7. Once the DNS check passes and GitHub issues the certificate, enable **Enforce HTTPS**.
8. In GitHub account **Settings → Pages**, verify `kindmechanics.com` and add the TXT verification record GitHub supplies. This protects the domain from being claimed by another GitHub Pages account.

## Checks after the DNS change

- `https://kindmechanics.com` loads the new static site.
- `https://terminology.kindmechanics.com` still loads the Terminology Tuesday site.
- `brian@kindmechanics.com` still receives mail.
- The Buttondown subscription form on `writing.html` submits correctly.
- The newsletter archive links open Buttondown rather than competing with the new homepage.

## Content notes

- The homepage no longer treats the newsletter as the primary call to action. Buttondown is retained as the archive and subscription management point.
- The award wording describes the Neurodiversity Awareness Month programme as developed at Datavant with Learning & Development and Ireland HR. It does not imply that Datavant commissioned Kind Mechanics as an external programme.
- `writing.html` links to the existing Buttondown versions of *When Is A Glass Not Just A Glass?* and *The Soft Room With No Exit*, so there are no placeholder `#` links.
- The wider research portfolio is deliberately not imported into this site. The research section stays on the workplace, cognition and neurodivergence strand.
- Before publicising the site, add the original Kind Mechanics logo asset if available and replace the text wordmark. The current text wordmark remains usable if that is not done immediately.
