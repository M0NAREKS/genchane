# GENCHANE — Brand Analysis and Design Brief

Phase 1: analysis and planning only. Neither direction is approved for implementation.

## 1. Sources and factual boundaries

Reviewed `AGENTS.md`, `content/biz-kimiz.md`, `content/gelecek-hedeflerimiz.md`, `genchane.jpeg`, and `baskayalar.jpeg`.

The instructions refer to `başkayalar.jpeg`, but the actual asset is named `baskayalar.jpeg`. Use the existing file without renaming it. GENCHANE is a registered trademark created by Başkayalar Kantin İşletmeciliği. The business began operating in 2022; the sources do not give a GENCHANE registration or launch date. Do not label GENCHANE as founded or registered in 2022.

The business describes serving educational institutions within Trakya University, with a focus on university students, affordable and hygienic food and drinks, quality, accessibility, and belonging. This does not establish an official university partnership or justify using university branding. Growth, new locations, greater product variety, digital investment, employment opportunities, local producer cooperation, and social projects are stated ambitions. Present them as goals, not completed achievements.

All explanatory documentation is in English. Proposed website labels and copy below are in Turkish. Preserve original business texts and brand names. No unverified address, hours, contact details, social handle, branch count, menu, price, testimonial, or business photograph should appear.

## 2. Brand identities and relationship

### GENCHANE: the primary public brand

The 1254 × 1254 JPEG has an almost black, subtly warm background, cream brush lettering, and a burnt-orange to peach underline. A cup, steam, cutlery, circular strokes, and small decorative marks connect it visually to food, drinks, and informal social time. The slanted lettering and sweeping underline suggest movement and youthfulness. This is a visual interpretation, not an additional business claim.

Its detailed composition is effective as a prominent brand illustration but becomes hard to read as a tiny navigation logo. The supplied image includes substantial dark margins and has no transparent background. Do not recreate its lettering as a font, extract its symbols, or redraw its strokes.

### Başkayalar Kantin İşletmeciliği: the corporate identity

The 1024 × 1024 JPEG uses circular typography, a centered cup with steam, green branches, dark lettering, and the year 2022. Its symmetry and restrained shapes communicate a more formal institutional identity. Green provides freshness as a visual association; it does not establish environmental certification, organic products, or sustainability achievements.

The image includes a white panel with a pale outer surround. Its visible wording is “BAŞKAYALAR KANTİN HİZMETLERİ”. Preserve that artwork exactly; use the source-backed corporate name “Başkayalar Kantin İşletmeciliği” in website text. Do not silently edit the logo wording to match the prose.

### Shared foundation

The cup and steam, circular construction, and dark neutral tones provide continuity. The website should have one GENCHANE-led visual system with a clearly identified corporate endorsement, rather than alternate between orange and green themes as if the two identities were competing services.

## 3. Measured color palette

Method: decoded the existing JPEGs with the installed Windows System.Drawing library and counted exact RGB values on a grid sampled every two pixels in both axes. For GENCHANE, near-white pixels and orange-family pixels were counted separately because dark background pixels dominate the image. Orange selection used R > 120, R > 1.5 × G, G > 20, and B < 0.8 × G; light selection used R > 200, G > 200, and B > 180. No packages were installed and no assets were written or modified.

These are measured raster samples, not an official vector palette or print specification. JPEG compression, antialiasing, and the orange tonal variation produce many neighboring values. The light gray surround belongs to the supplied image presentation and is not necessarily a brand color.

| Source | Measured sample | Evidence in sampled pixels | Proposed website role |
| --- | --- | --- | --- |
| GENCHANE | `#050402` | Most frequent exact color: 167,790 samples | Warm dark background and primary text |
| GENCHANE | `#F4EDE3` | Most frequent light-filter color: 1,244 samples | Cream surfaces and text on dark backgrounds |
| GENCHANE | `#B03E02` | Most frequent orange-filter color: 29 samples | Burnt-orange accents and buttons on light surfaces |
| GENCHANE | `#D78A5C` | Second most frequent orange-filter color: 19 samples | Peach accents and links on dark surfaces |
| Başkayalar | `#FFFFFF` | Most frequent exact color: 194,214 samples | Corporate logo panel and clean surfaces |
| Başkayalar | `#2C2A2B` | Frequent dark lettering color: 3,934 samples | Corporate text and shared dark neutral |
| Başkayalar | `#3DA536` | Frequent branch green: 2,611 samples | Limited corporate accents |
| Başkayalar | `#F6F7FB` | Frequent pale surround: 13,267 samples | Optional neutral surface, not a primary brand color |

Calculated flat-color contrast ratios:

| Pair | Ratio | Usage constraint |
| --- | --- | --- |
| Cream / warm dark | 17.63:1 | Suitable for body text |
| Burnt orange / cream | 5.11:1 | Suitable for normal text and button labels |
| Burnt orange / warm dark | 3.45:1 | Avoid for normal text; use peach instead |
| Peach / warm dark | 7.49:1 | Suitable for normal text |
| Peach / cream | 2.35:1 | Decorative use only |
| Green / white | 3.17:1 | Avoid for normal text; use dark labels beside green accents |
| Corporate dark / white | 14.26:1 | Suitable for body text |
| Corporate dark / cream | 12.27:1 | Suitable for body text |

These calculations describe solid UI colors, not every pixel within the logos. Keep the original logo colors intact. Verify final focus indicators, borders, hover states, and actual rendered text contrast during implementation.

## 4. Shared content and interaction model

Use a concise single-page static site. Initial navigation: “Biz Kimiz?”, “Yaklaşımımız”, and “Gelecek Hedeflerimiz”, linking to corresponding sections. The GENCHANE brand link returns to the top. Future code identifiers, section IDs, components, and new filenames must be English while visible labels remain Turkish.

Do not show a contact link or social icon without a verified destination. The initial page can be complete without a contact section. Calls to action should navigate to real page sections, with no ordering or membership features.

Both directions use one H1, descriptive H2 headings, short readable paragraphs, semantic landmarks, keyboard-visible focus, a Turkish skip link (“İçeriğe geç”), and a Turkish document language. Touch targets should be at least 44 × 44 px. Respect reduced-motion preferences and avoid motion-dependent content. Use no autoplay, carousel, or heavy widget.

Font baseline: `system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif`. This avoids external font requests and new dependencies. Verify Turkish characters, especially İ/ı, Ş/ş, Ğ/ğ, Ö/ö, Ü/ü, and Ç/ç, in the actual browser. Logo artwork remains an image and is not typeset with this stack.

## 5. Direction A — Modern, youthful, and energetic

### Concept and visual hierarchy

A warm campus-oriented editorial composition: a dark opening, confident Turkish headlines, cream reading sections, and purposeful burnt-orange accents. Use the existing logo's movement as a compositional cue through offset alignment and spacing, without copying or altering its illustrated strokes. Avoid generic grids of identical floating cards.

Hierarchy: GENCHANE and student-focused message → service values → corporate origin → future ambitions. Broad cream areas maintain readability and prevent a predominantly dark page from becoming visually heavy. Green remains local to the corporate story.

### Typography

- Headings: system sans, weight 750–800 where supported, otherwise 700; modest negative letter spacing, avoiding tight Turkish glyph collisions.
- H1: approximately 64–80 px on wide screens and 36–42 px on mobile; line height 1.08–1.15, with natural wrapping.
- H2: 36–44 px desktop and 28–32 px mobile. Body: 17–18 px, line height about 1.65, reading width around 60 characters.
- Short orange section labels may establish rhythm; avoid long uppercase Turkish text.

### Navigation and hero

Use a compact, non-sticky dark header. A plain live-text GENCHANE home link supports navigation; it does not replace or imitate the logo. Put the complete original logo prominently in the hero, where its details have enough room.

Desktop hero: approximately 55/45 split. Left: short source-backed context, large H1, supporting paragraph, and one cream button linking to “Biz Kimiz?”. Right: complete GENCHANE JPEG, proportionally contained on the sampled warm dark surface. Its embedded background may remain faintly visible; never remove it merely to disguise the raster boundary.

Proposed Turkish copy:

> **Gençlerin yanında, kampüs hayatının içinde.**
>
> GENCHANE, Başkayalar Kantin İşletmeciliği'nin tescilli markasıdır. Üniversite öğrencileri için kaliteli, hijyenik ve ulaşılabilir yiyecek ve içecek hizmetini önemsiyoruz.
>
> Button: **Bizi tanıyın**

### Page sections

1. **Hero:** GENCHANE identity and student-focused introduction.
2. **“Yaklaşımımız”:** a wide cream section with three editorial columns: “Ulaşılabilir hizmet”, “Kalite ve hijyen”, and “Aidiyet”. Use short, faithful paraphrases rather than unsupported performance claims.
3. **“Biz Kimiz?”:** an asymmetric corporate story panel, with the complete Başkayalar image on white and text explaining the business's 2022 beginning and its creation of the registered GENCHANE brand. Do not invent a chronology for the registration.
4. **“Gelecek Hedeflerimiz”:** three numbered ambitions: service development and new locations; product variety and digital communication; employment, local cooperation, and social contribution. Phrase every item as a goal. Use a static list, not a dated roadmap.
5. **Footer:** GENCHANE, the full corporate name, and useful section links. No fabricated contact or social details.

### Mobile layout

At 360–390 px, use 20 px horizontal gutters and a single column. Header brand link occupies one row; the three section links wrap below it, with generous touch areas. This avoids a JavaScript menu for three links.

Hero order: heading, paragraph, button, then a centered complete logo image up to the available width. Do not force the hero into one viewport or hide the logo to achieve that. Stack the three value columns as separated text rows; place the corporate logo above its story. Reduce section spacing to about 48–64 px from 80–112 px on desktop. No horizontal overflow, forced heading line breaks, or fixed-height copy containers.

## 6. Direction B — Premium, minimal, and corporate

### Concept and visual hierarchy

A quiet editorial presentation with white and cream surfaces, charcoal typography, ample whitespace, fine rules, and restrained orange accents. “Premium” describes visual restraint; it must not imply luxury pricing or contradict the affordable, student-friendly service positioning.

Hierarchy: clear GENCHANE introduction → business credibility and origin → service principles → future outlook. Keep GENCHANE dominant even when the corporate story appears earlier. Green accents are restricted to the Başkayalar section.

### Typography

- Use the same dependency-free system sans stack with more restrained weights: H1 600–650 where supported, otherwise 600; body 400; navigation 500.
- H1: 48–60 px desktop and 32–36 px mobile, line height about 1.18; H2: 30–36 px desktop and 26–30 px mobile.
- Body: 17–18 px, line height 1.7; reading width 55–65 characters. Prefer sentence case and a measured vertical rhythm over oversized labels.

### Navigation and hero

White header with GENCHANE home link, the same three Turkish section links, and a fine lower rule. No persistent floating controls.

Hero is centered and vertically composed rather than split. A short corporate attribution sits above the H1. Follow it with a compact paragraph, one burnt-orange link styled as a button with cream text, and the complete GENCHANE JPEG in a bounded dark square. The square's deliberate geometry accommodates the existing black background without recoloring or cutting out the logo.

Proposed Turkish copy:

> Attribution: **Başkayalar Kantin İşletmeciliği'nin tescilli markası**
>
> **Öğrenci odaklı hizmet, güçlü bir aidiyet.**
>
> Üniversite öğrencilerinin günlük ihtiyaçlarını gözeten kaliteli, hijyenik ve ulaşılabilir hizmet anlayışıyla çalışıyoruz.
>
> Button: **Hikâyemizi keşfedin**

### Page sections

1. **Hero:** centered GENCHANE presentation, with generous surrounding space.
2. **“Biz Kimiz?”:** a calm two-column editorial story. Text carries the 2022 founding and student focus; the Başkayalar logo occupies a smaller white figure panel with a corporate caption.
3. **“Yaklaşımımız”:** three numbered horizontal rows separated by fine rules, explaining accessibility, quality and hygiene, and belonging. Avoid icon-heavy cards or invented certifications.
4. **“Gelecek Hedeflerimiz”:** a narrow introductory paragraph followed by a two-column list of ambitions. No growth metrics, invented milestones, or implied completed partnerships.
5. **Footer:** a restrained divider, GENCHANE, the full corporate name, and section links.

### Mobile layout

At 360–390 px, use 20–24 px gutters, centered hero copy, and a centered contained logo. Brand and navigation occupy separate rows. Stack the corporate story and future goals into a single column; use left alignment for long-form copy. Keep 56–72 px between sections and maintain visible touch targets despite the minimal aesthetic. The design must not depend on excessive whitespace that buries the business story on a small screen.

## 7. Coexistence rules for both directions

- GENCHANE owns the primary introduction, navigation identity, and overall palette. Başkayalar Kantin İşletmeciliği appears as the business behind the registered brand, not as a separate competing offer.
- Present the complete Başkayalar logo in the corporate story with a nearby caption: “GENCHANE, Başkayalar Kantin İşletmeciliği'nin tescilli markasıdır.” Repeat the corporate name in the footer; a second large logo there is unnecessary.
- Give GENCHANE greater visual prominence. Judge by the visible artwork, not equal JPEG dimensions, because the two source images have different margins and visual density.
- Preserve each image's aspect ratio, background, lettering, and colors. Use proportional containment, no distortion, no filters, no redrawing, no new combined lockup, and no cropping of meaningful artwork. If optimization is later needed, generate separate derivatives and preserve the originals.
- Use a shared text system, container width of roughly 1120–1200 px, spacing rhythm, and button treatment. Keep orange and green in separate contextual areas; do not combine them in gradients or competing buttons.
- Keep comfortable layout space around both assets without claiming an official brand clear-space standard. On mobile, show logos separately rather than shrinking them into an unreadable side-by-side strip.
- Provide descriptive Turkish alternative text for informative logo images. Keep the corporate name and business relationship in HTML so readers do not need to decipher embedded logo lettering.
- Start with an asset-led design. No verified business photographs were identified among the inspected assets. Do not imply that stock or generated scenes depict actual premises, products, staff, or students. Any later business photography needs a supplied, approved source.

## 8. Recommendation and approval boundary

Recommend **Direction A**. The primary audience in the business sources is university students, and GENCHANE's brush lettering and warm orange already support a lively, welcoming identity. The strong dark opening gives the existing logo a natural home, while cream reading sections and an orderly corporate story preserve clarity and trust. This direction also works with the available assets, without relying on unverified photography.

Direction B is a viable alternative if the user's priority is a more restrained institutional presentation. Its tradeoff is that the animated character of the GENCHANE artwork and the large dark logo panel stand out more sharply against a quiet, light composition; careless execution could make the page feel less student-oriented.

Approval should select A or B and identify any desired adjustments to tone, palette balance, or section order. Until that approval, stop at this document. Do not implement the application, install packages, initialize Git, commit, push, or deploy.

After approval, retain Astro + Tailwind CSS and static generation for GitHub Pages, minimal dependencies, and JavaScript only for necessary interaction. Validate at 360 px, 390 px, and wide screens using Playwright MCP; run relevant build checks, then Lighthouse CLI for final performance, accessibility, and SEO review. No browser, build, or Lighthouse results are claimed in Phase 1. Verify deployment base path and any custom domain before publication; neither is fixed by this brief.
