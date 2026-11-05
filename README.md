# GENCHANE visual prototype

Static Astro site with Tailwind CSS through the official `@tailwindcss/vite` integration. Headings use locally bundled Bricolage Grotesque (Latin and Latin Extended); body copy uses system fonts. No client-side application JavaScript is required.

## Local development

Use Node.js 24 (the deployment workflow also uses Node 24), then:

```sh
npm ci
npm run dev
```

Open the address printed by Astro (normally http://localhost:4321).

```sh
npm run build
npm run preview
```

## Assets and content

Original JPEGs and business Markdown remain in the project root and `content/`. Astro generates responsive WebP derivatives from the imported JPEGs during build. All displayed copy is adapted from the provided business texts. Font files are bundled locally from the Fontsource package, which includes the upstream OFL license.

## Deployment boundary

Production configuration targets `https://genchane.com.tr/` at the domain root, with static output in `dist/`. The local Pages workflow, canonical/social metadata, sitemap integration, robots file, CNAME, and brand sharing assets are prepared. No deployment has been performed. Follow [DEPLOYMENT.md](DEPLOYMENT.md) for the remaining GitHub, DNS, and HTTPS steps; do not add a repository-specific base path.

Full-page visual review screenshots are saved in `previews/`.
