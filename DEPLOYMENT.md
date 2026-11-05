# GENCHANE production deployment

Production URL: **https://genchane.com.tr/**. Hosting: GitHub Pages with GitHub Actions. The website is Turkish, statically generated, and has no backend.

## Completed locally

- Astro `site` is `https://genchane.com.tr/`, `base` is `/`, and output is static. The old `BASE_PATH` override is removed. Do not add a repository-name prefix for this custom root domain.
- Turkish language, page title/description, canonical, Open Graph, and Twitter large-image metadata are configured. Font preloading and the existing CLS fix remain intact.
- `@astrojs/sitemap` generates `dist/sitemap-index.xml` and `dist/sitemap-0.xml`. `public/robots.txt` points to the actual sitemap index URL.
- `public/CNAME` contains only `genchane.com.tr`, copied into `dist/CNAME`.
- Static favicon PNGs (16, 32, 48, 180, 192 px), a multi-size ICO, and `public/social/genchane-og.png` (1200 × 630) use derivatives of the existing brand artwork. Original JPEGs are unchanged. The sharing image uses the existing Bricolage font, headline, palette, and official domain, with no external image or invented business fact.
- `.github/workflows/deploy.yml` prepares a Node 24 build with `npm ci`, builds the site, uploads only `dist/` using the official Pages artifact action, and deploys that artifact with the official Pages deployment action. It follows the build/artifact/deployment pattern in Astro's guide while making lockfile installation explicit.
- The workflow runs on pushes to `main` and permits deployment only from `refs/heads/main`, including manual dispatch. Set `main` as the repository's default branch. No GitHub owner or repository name is hardcoded.
- Local browser profiles and review outputs are ignored for future source-control use. Keep those local files out of the repository.

**Publication boundary:** local Git initialization and the initial commit are separate from publication. No push, remote repository configuration, workflow run, DNS modification, publication, or live HTTPS validation has been performed. Local preparation does not activate hosting.

## Manual GitHub setup — requires the owner

1. Choose/create the `genchane` GitHub repository and set its default branch to `main`. Use a repository visibility and account plan that support GitHub Pages. Preserve the project's root structure.
2. Include `src/`, `content/`, original root JPEGs, `public/`, Astro/TypeScript configuration, `package.json`, `package-lock.json`, `.github/workflows/deploy.yml`, and project documentation in the source repository. Do not commit `node_modules/`, `dist/`, browser profiles, or local review artifacts. Remote setup and pushing are left to the owner; local preparation may already include the initial commit.
3. Under repository **Settings → Pages → Build and deployment**, select **GitHub Actions** as the source. Do not select a `gh-pages` branch publication strategy.
4. Allow the official actions used by the workflow in the repository/organization Actions policy. The build job needs source read access; the deploy job needs `pages: write` and `id-token: write`. It targets the `github-pages` environment. Check environment protection rules if a workflow waits for approval.
5. Configure **Custom domain** as `genchane.com.tr`. Save it before pointing DNS at Pages. If the field is unavailable before initial Pages activation, finish the first owner-approved workflow, then claim the domain before changing DNS. Do not validate asset paths using a temporary repository-subpath URL; production is configured for the custom domain root.
6. For custom Actions publishing, GitHub's domain setting is authoritative: the copied CNAME file is supplied as requested, but GitHub does not use it to configure the domain automatically. The owner must set the domain in Pages settings.
7. When authorized to publish, push to the repository's `main` branch or dispatch **Deploy GENCHANE to GitHub Pages** from `main`. The workflow serializes deployments and publishes only the built `dist/` artifact. No PAT or application secret is needed for the deployment token.

## Verify domain ownership first

Use the GitHub account/organization Pages settings to add and verify `genchane.com.tr`. GitHub supplies a TXT record name and a unique verification token. Copy those exact values into the DNS provider, verify them in GitHub, and retain the TXT record. Do not invent a token or use a different account's challenge name. A typical record name follows `_github-pages-challenge-OWNER.genchane.com.tr`, where `OWNER` is the actual account identifier supplied by GitHub.

This ownership check is separate from the repository's custom-domain setting and from DNS routing. Complete it before routing traffic when possible.

## Apex DNS for genchane.com.tr — manual

Use the following four A records for the apex (`@` or `genchane.com.tr`, according to the provider's interface):

| Type | Name | Value |
| --- | --- | --- |
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |

Optional IPv6 routing uses all four matching AAAA records:

| Type | Name | Value |
| --- | --- | --- |
| AAAA | @ | 2606:50c0:8000::153 |
| AAAA | @ | 2606:50c0:8001::153 |
| AAAA | @ | 2606:50c0:8002::153 |
| AAAA | @ | 2606:50c0:8003::153 |

Review conflicting apex web A/AAAA records before updating them. Preserve unrelated MX, mail, and verification TXT records. An incorrect existing AAAA record can route IPv6 visitors elsewhere even if the A records are right. Do not add a wildcard DNS record or use an ordinary apex CNAME.

### Optional www

If `www.genchane.com.tr` should also work, add a CNAME named `www` pointing to the actual GitHub Pages owner host, `OWNER.github.io`. Substitute the real owner; do not include a repository path, protocol, or `genchane.com.tr` in that target. Keep the canonical/custom domain as the apex `genchane.com.tr`; verify GitHub's redirect from www to the apex after activation.

## DNS and HTTPS checks — manual

After the owner changes DNS, inspect the records (propagation may take up to 24 hours):

```sh
dig +short genchane.com.tr A
dig +short genchane.com.tr AAAA
dig +short www.genchane.com.tr CNAME
# Optional independent resolver comparison:
dig @1.1.1.1 +short genchane.com.tr A
```

Compare answers with the configured records above; query www only if it was configured. On Windows, `Resolve-DnsName genchane.com.tr -Type A` provides the equivalent basic check. Verify the ownership TXT record using the exact name GitHub provided. GitHub Pages settings must show a successful domain/DNS check.

Wait for certificate provisioning, then enable **Enforce HTTPS** in Pages settings. If the option is unavailable, allow time for provisioning and recheck DNS/certificate status. Inspect any existing CAA policy if GitHub reports that certificate issuance is blocked; do not change unrelated certificate policy blindly.

```sh
curl -I https://genchane.com.tr/
curl -I http://genchane.com.tr/
curl -I https://www.genchane.com.tr/  # only if configured
```

Confirm HTTPS returns the site, HTTP upgrades to HTTPS, and optional www redirects to the chosen apex URL. Local preview cannot establish these facts.

## Production validation checklist

Before publication, and again on the public domain after the first approved deployment:

- Run `npm ci` with Node 24, then `npm run build`. Check that the workflow's `main` branch condition matches the selected ref.
- Confirm `dist/index.html` has `lang="tr"`, one H1, an ordered H2/H3 hierarchy, the official canonical URL, and absolute production Open Graph/image URLs.
- Confirm the OG image is 1200 × 630, the ICO and PNG icons load, and Turkish letters and logo lettering remain legible in small previews.
- Confirm `dist/CNAME` is exactly `genchane.com.tr`, `robots.txt` names `/sitemap-index.xml`, and that index references the generated numbered sitemap containing `https://genchane.com.tr/`.
- Confirm root asset paths resolve under the custom domain without a repository prefix. Publish only the `dist/` artifact; review screenshots and local reports are not website assets.
- Check 360/390/768/1440 px layouts, the hero logo, circular Başkayalar logo, Soft Mocha `#CBB5A1`, image loading, touch targets, keyboard focus/skip link, and internal anchors.
- Verify the official Instagram links still point to `https://www.instagram.com/genchane22/` with secure new-tab attributes.
- Check font preloading/fallback stability on a cold mobile load. No full Lighthouse audit was requested for this preparation phase.
- On the public domain, confirm favicon, `/social/genchane-og.png`, `/robots.txt`, `/sitemap-index.xml`, and `/sitemap-0.xml` return successful responses. Use platform sharing preview tools to refresh any cached OG image after asset updates.

## Updates and redeployment

Edit source files while preserving verified business facts and original assets. Update the title/description or static sharing image when relevant; the sharing image is a committed output, not a runtime image service. Test locally with `npm run dev`, build, then inspect the production version with `npm run preview`. Keep dependency changes and `package-lock.json` together.

After the owner's approval, commit/push the reviewed source to the `main` branch. The workflow builds with the lockfile and redeploys automatically; manual dispatch from `main` is also supported. Verify the deployment result and domain after each release. Keep `public/CNAME`, the root base path, and the custom-domain setting consistent. Do not replace this with a manual upload of source directories.

## Official references checked for this configuration

- [Astro GitHub Pages deployment](https://docs.astro.build/en/guides/deploy/github/)
- [Astro sitemap integration and generated filenames](https://docs.astro.build/en/guides/integrations-guide/sitemap/)
- [GitHub custom domains and DNS records](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
- [GitHub domain verification](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages)
- [GitHub Pages HTTPS](https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https)
