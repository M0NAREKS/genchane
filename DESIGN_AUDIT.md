# GENCHANE — UI/UX Design Audit

Audit date: 2026-11-05. Scope: the existing approved website, without redesign or implementation changes.

## Executive assessment

The site has a coherent foundation: a distinctive original GENCHANE mark, strong dark/cream transitions, expressive headings, clear corporate attribution, and restrained editorial sections. The circular Başkayalar presentation and oversized GENCHANE footer now belong to that system. Neither needs replacement.

The remaining weaknesses concern orientation, the meaning of arrows, mobile heading differentiation, and paragraph composition. **No High-severity issue was established in the tested scope.** Four Medium findings and two Low findings are documented below. Most are design refinements; they must not be misrepresented as proven accessibility failures or measured user confusion.

The strongest next step is a small correction to mobile story orientation and a consistent distinction between navigation arrows and ornament. Preserve the palette, fonts, original assets, section sequence, desktop grids, corporate badge, and footer identity.

## Method and evidence boundaries

- Read `AGENTS.md` and `DESIGN_BRIEF.md`, then inspected the current page, CSS, layout, and shared navigation/icon components with line numbers.
- Used Playwright MCP against the running static preview at `http://localhost:4321/`, at **390 × 844** and **1440 × 1000** CSS pixels.
- Inspected every major section, computed styles, element geometry, rendered paragraph line lengths, image loading, anchor destinations, keyboard focus, and reduced-motion behavior.
- Captured and inspected exactly two new full-page audit images: `/tmp/genchane-audit-mobile.png` and `/tmp/genchane-audit-desktop.png`. These are temporary inspection artifacts, not new project assets or redesign mockups.
- Paragraph line lengths below are approximate counts of rendered characters, including spaces, measured with DOM text ranges after fonts loaded. Rounded section positions may differ by one pixel.
- Bricolage Grotesque Latin and Latin Extended faces were loaded. Turkish text was visually inspected in the tested browser; this is not a claim of identical rendering on all platforms.
- Severity describes user impact and design quality: **High** = a serious barrier to the page's core use; **Medium** = a meaningful clarity or hierarchy weakness; **Low** = localized optical polish. Visual preference alone does not justify a High rating.
- No user study, screen-reader session, cross-browser certification, full accessibility audit, Lighthouse audit, or remote Instagram profile-content inspection was performed. No application code, assets, business content, dependencies, or existing project documentation were changed. No build was needed or run for this documentation-only audit.
- Later user approvals take precedence over the brief's historical approval boundary and its initial rectangular corporate-logo presentation. The current approved circular presentation is the baseline.

## Verified baseline

| Check | 390 px | 1440 px | Assessment |
| --- | --- | --- | --- |
| Document width | 390 px | 1440 px | No horizontal overflow |
| Document height | 4789 px | 3575 px | Descriptive measurement, not a defect by itself |
| Main navigation | 14 px, two rows | 14 px, one row | Readable and functional |
| Navigation targets | 165 × 44, 165 × 44, 350 × 44 px | About 83 × 44, 65 × 44, 159 × 44 px | All meet the project's 44 × 44 px target |
| Hero H1 | 42.51 px / 45.06 px line height, weight 750 | 88.56 px / 92.10 px, weight 750 | No visible clipping |
| Section H2 range | 38.4–40 px, weight 650 | 51.84–59.04 px, weight 650 | Mobile differentiation is discussed in F4 |
| Main body copy | Mostly 16 px / 27.2 px | Mostly 16 px / 27.2 px | Comfortable line spacing; story introduction is 17/18 px |
| Labels and captions | Labels 12 px; captions 13 px | Labels 12 px; captions 13 px | No inconsistent story-label override remains |
| Logo loading | Both loaded | Both loaded | No broken images observed |

Instagram text colors were read from the actual rendered elements and their opaque ancestor backgrounds. Calculations use linearized sRGB relative luminance:

| Location | Foreground / background | Contrast | Assessment |
| --- | --- | --- | --- |
| Hero Instagram | `#D78A5C` / `#050402` | **7.49:1** | Exceeds the 4.5:1 normal-text AA threshold |
| Footer Instagram | `#B03E02` / `#F4EDE3` | **5.11:1** | Exceeds the same threshold |

No Instagram color adjustment is justified. Both links have meaningful Turkish names, a hidden new-tab notice, the correct `https://www.instagram.com/genchane22/` destination, `target="_blank"`, and `rel="noopener noreferrer"`. Their icons are hidden from assistive technology because the text already names the destination.

Keyboard tabbing reached the navigation, primary CTA, both Instagram links, discovery link, and footer links with solid visible focus outlines. The skip link transferred focus to `main`. The three main anchors and back-to-top link reached existing targets. Under reduced motion, scrolling was `auto` and arrow transition duration was `0s`. No console errors were reported during this inspection.

## Prioritized findings

### F1 — The mobile story heading appears well after the section begins

**Severity: Medium. Category: objectively measured content order, with an inferred orientation cost.**

**Evidence:** At 390 px, `#story` begins at approximately document y=2127. Its H2 begins at y=2696, about **569 px later**. The corporate panel occupies 416 px before the 44 px grid gap and the story heading group. Clicking “Biz Kimiz?” lands with the H2 approximately **593 px below the viewport top**, because the anchor aligns the beginning of the section, not its heading. The “02 / BİZ KİMİZ?” label also sits after the badge. See `src/pages/index.astro:67–80` and `src/styles/global.css:154–158`.

**Why it matters:** The destination works, but the user first sees a logo and corporate caption rather than an immediate title confirming the selected section. This is an orientation weakness, not a broken anchor. The corporate identity is already clear; enlarging or replacing its artwork would not solve the ordering problem.

**Minimal correction:** On mobile, place the existing section label and H2 before the badge, with the story paragraphs following it. Preserve the desktop two-column layout, circular logo, current artwork scale, and corporate caption. Reuse the existing heading; do not add duplicate visible headings or new copy. Verify that the anchor landing immediately exposes the section identity. Do not compensate by adding sticky navigation.

### F2 — Diagonal arrows do not consistently describe link behavior

**Severity: Medium. Category: verifiable direction/destination mismatch; the predicted confusion is a design inference.**

**Evidence:** The header's “Gelecek Hedeflerimiz ↗” points to the lower `#future` section (`src/components/Header.astro:7`). The hero CTA uses `<Arrow diagonal />` but moves down to `#story` (`src/pages/index.astro:33`). The footer's story link and back-to-top link also use upward diagonal arrows (`src/components/Footer.astro:9,16`). All these are same-page links. The shared diagonal icon is a right arrow rotated −40 degrees (`src/components/Arrow.astro:5–6`, `src/styles/global.css:33–34`). By contrast, the hero's discovery link correctly uses `↓` for a lower section (`src/pages/index.astro:44`).

**Why it matters:** A repeated diagonal-arrow treatment makes destinations with different behavior look equivalent and borrows the visual convention often used for outward navigation. The Turkish labels still explain their actions, so this is not a navigation blocker or a claim that an external window actually opens.

**Minimal correction:** Adopt one internal-navigation rule: down for a lower section, up for a higher section, or omit an arrow where the text is sufficient. Keep the working discovery arrow. Reuse the existing SVG with deliberate orientation rather than installing an icon library. Keep Instagram's recognizable icon and accessible new-tab notice. Do not change destinations or CTA priority.

### F3 — Nonfunctional arrows repeat the language of actionable links

**Severity: Medium. Category: subjective visual recommendation grounded in identifiable elements.**

**Evidence:** The future section contains a standalone `↗` span, `aria-hidden="true"`, outside any link or button (`src/pages/index.astro:92`). It renders at **100 px** with a 35 px top margin on desktop and is hidden on mobile (`src/styles/global.css:99,162`). The corporate story note has a second noninteractive `↗` at **34 px** (`src/pages/index.astro:80`, `src/styles/global.css:90–92`). Neither identifies a destination, a measured growth result, or a specific brand motif from the logos.

**Why it matters:** The large desktop arrow competes with the future-goals introduction without supplying information. Repeating the same diagonal gesture in static notes and functional links weakens the site's restrained editorial vocabulary and adds a generic agency-style flourish. Their noninteractive status is verified; actual user attempts to click them were not observed.

**Minimal correction:** Remove the standalone future arrow without filling the resulting space. Remove the story-note arrow while retaining its sentence and useful separating rule. Rebalance only the local note indentation or margin if necessary. Preserve genuine navigation indicators, Instagram icons, and all marks embedded in the original logos. Do not turn these ornaments into new CTAs to justify their presence.

### F4 — Mobile primary and secondary headline sizes nearly converge

**Severity: Medium. Category: measured typography with a subjective hierarchy recommendation.**

**Evidence:** At 390 px the H1 is **42.51 px**, while the approach and future H2s are **40 px**, a size ratio of only **1.06**. The future headline occupies three lines and about **130 px** vertically; the H1 occupies two lines and about **90 px**. On desktop the H1 is 88.56 px against H2s of 51.84–59.04 px, so size differentiation is much stronger. Source: `src/styles/global.css:27–28,135,148,157,160`.

**Why it matters:** Weight, wording, and color still distinguish the hero, and the headings do not clip. Nevertheless, the future section's headline becomes an equally strong or stronger typographic event on mobile. This softens the intended hierarchy between the primary introduction and supporting sections. It is not a contrast or semantic-heading failure.

**Minimal correction:** Trial a mobile H2 range around 34–36 px while preserving the current H1, Bricolage Grotesque, color accents, and desktop sizing. Choose the final value after checking existing Turkish words and wrapping at 360 and 390 px. Do not increase every heading, tighten line heights further, or globally rescale the page.

### F5 — Desktop corporate paragraphs use a wider reading measure than neighboring text

**Severity: Low. Category: measured line length with an optical/readability recommendation.**

**Evidence:** At 1440 px the story text column is approximately **644 px** wide. Its 16 px paragraphs render full lines of approximately **77–87 characters**, with another paragraph at 80/78 characters. The hero text is constrained to 380 px and its full lines are about 58 characters; the approach introduction is 445 px wide with full lines around 53–58 characters. See `src/styles/global.css:50,71,79,88`.

**Why it matters:** This is the densest prose area and has a noticeably wider reading rhythm. The generous 1.7 line height prevents it from becoming a severe readability problem. No line-length accessibility failure is claimed.

**Minimal correction:** Trial a desktop-only maximum reading width around 58–62ch on the story paragraphs and note, retaining the existing outer column and heading position. Do not narrow the whole desktop grid, alter the corporate logo, or rewrite business facts. Check resulting paragraph heights before accepting the change; if it worsens column balance, retain the current measure.

### F6 — A few short final lines interrupt otherwise controlled paragraph shapes

**Severity: Low. Category: subjective optical polish supported by rendered wrapping.**

**Evidence:** The 390 px approach introduction ends with the six-character final line “olmak.” Its measured character counts are approximately 44/45/43/6. The desktop hero description ends with a ten-character last line, “buradayız.”, after two lines of about 58 characters. See `src/pages/index.astro:31,53`; rendered widths are 380 px desktop for the hero and 350 px mobile for the approach introduction.

**Why it matters:** These are small paragraph-shape irregularities, not missing content or broken wrapping. They should not drive a copy rewrite or a global layout change.

**Minimal correction:** After the higher-priority adjustments, test a local paragraph wrapping treatment such as `text-wrap: pretty`, or a small measure adjustment on these two introductions only. Keep the Turkish wording intact and accept the treatment only if it improves both audited widths. Do not insert hard line breaks into prose or balance every body paragraph indiscriminately.

## Section-by-section assessment

### Header and mobile navigation

The desktop header is compact and legible. On mobile, two rows and a 181 px overall header are an explicit tradeoff for visible links and comfortable touch targets. The first row is aligned to opposite edges; the second is a full-width target. The 8 px row gap is consistent. There is no evidence that a hamburger, script, sticky header, or another navigation redesign is needed. F2 is the only recommended header correction.

### Hero

The original mark remains the primary illustration, integrated with the sampled `#050402` field. A faint raster background boundary is visible on desktop but is permitted by the brief; masking, recoloring, or rebuilding the mark is not justified. The cream “Bizi tanıyın” button clearly outranks the lighter secondary Instagram link. The mobile CTA stack has separate 52 px and 44 px targets with an 8 px gap. At 390 px the header plus hero extends to about y=1050; this alone is not a problem, and the brief expressly avoids forcing the complete hero into one viewport. Preserve the composition. Address only F2, F4, and optionally F6.

### Our Approach

The open three-column desktop layout and stacked mobile rows communicate three principles without repeated boxes or shadows. Numbering and rules support grouping. The unequal paragraph lengths are normal; do not force equal-height copy, invent content, or remove meaningful whitespace to make all rows identical. Main text is 16 px with approximately 27.2 px line height. F4 and the localized F6 are sufficient refinements here.

### About Başkayalar / Our Story

The two-column desktop composition establishes the business behind GENCHANE, not a rival brand. The white circular badge, restricted green accent, and source-backed corporate name work together. The current image has a `circle(44%)` CSS mask and no recoloring or distortion; retain this approved presentation. The story note has useful content and a separating rule, but its arrow is unnecessary. Prioritize F1, then F3; evaluate F5 only if the remaining desktop balance benefits.

### Future Goals

The numbered list is a useful counterweight to the large left-hand introduction and clearly states ambitions rather than achievements. Desktop spacing is intentionally asymmetric. The standalone arrow is the weakest ornament on the page (F3). Remove it without introducing another filler object. On mobile the existing three-line H2 is a reason to evaluate F4, not a reason to change the section's content or collapse it into cards.

### Footer

The oversized GENCHANE treatment provides a memorable ending and should remain. It is marked `aria-hidden` as a redundant visual brand treatment; accessible GENCHANE identification remains in ordinary page text. Corporate attribution and the official Instagram link are present. Back-to-top is functional and all footer links have at least 44 px target height. The diagonal direction treatment belongs in F2. Do not add unverified contact details or more footer columns to fill space.

## Decorative-element inventory

| Element | Role | Decision |
| --- | --- | --- |
| Top burnt-orange strip | Restrained brand framing | Keep |
| Small GENCHANE navigation dot and footer punctuation | Consistent typographic brand accent | Keep |
| 26 px line before the hero eyebrow | Groups a short introductory label | Keep; no evidence it causes clutter |
| `01 /`, `02 /`, `03 /` section labels | Page orientation and editorial sequence | Keep |
| Principle and goal numbers | Local grouping within each section | Keep; contextual repetition is not itself a defect |
| Hairline section, row, and caption rules | Grouping and separation | Keep; do not treat them as interactive control boundaries |
| Small green corporate dot | Connects the caption area to Başkayalar's green palette | Keep; do not present it as certification |
| Original logos' lettering, circles, strokes, cup, steam, leaves, and cutlery | Actual brand artwork | Preserve unchanged |
| Hero discovery `↓` | Functional navigation to the next section | Keep |
| Header/CTA/footer directional arrows | Functional navigation, inconsistent orientation | Correct under F2 |
| Instagram outline icon | Recognizable destination cue beside named links | Keep; accessible text supplies its name |
| Corporate story-note `↗` | Static ornament with no destination | Remove under F3 |
| Desktop future `↗`, 100 px | Static ornament; no informational target | Remove under F3; retain empty space |

## Elements that should remain unchanged

- Original `genchane.jpeg` and `baskayalar.jpeg`, including every logo detail and their source colors.
- GENCHANE's primary role and Başkayalar Kantin İşletmeciliği's supporting corporate role.
- Measured black, warm cream, burnt-orange, and peach palette; green only in the corporate context.
- Bricolage Grotesque, locally loaded Latin/Latin Extended faces, and Turkish website language.
- Dark hero, section order, black/cream rhythm, desktop asymmetry, and approved circular corporate badge.
- Oversized GENCHANE footer, official Instagram URL, Turkish link labels, and secure external-link attributes.
- Semantic landmarks, single H1, H2/H3 structure, visible focus, skip link, reduced-motion support, and generous touch targets.
- Existing business facts and future-tense ambitions. Missing unverified locations, hours, photographs, and contact channels are not audit defects.
- Static Astro architecture and minimal client-side behavior. None of these findings requires a new dependency, widget, backend, or animation system.

## Prioritized implementation plan — approval required

1. **Orientation and functional clarity:** implement F1's mobile heading order and F2's directional-icon rule. Verify anchor landings and DOM reading order, retain visible focus, and preserve the current desktop columns.
2. **Remove unsupported ornament:** implement F3 by deleting the two static arrows. Keep their meaningful adjacent text and useful rules. Accept intentional negative space rather than filling it.
3. **Refine mobile hierarchy:** trial F4 at 360/390 px and compare with unchanged 1440 px typography. Approve by actual wrapping and emphasis, not a blanket numerical scale.
4. **Optional optical pass:** evaluate F5 and F6 locally. Keep either only if it measurably improves paragraph shape without increasing awkward gaps or damaging column balance.
5. **Verify the approved corrections:** production build, focused Playwright checks at 360/390/1440 px, text contrast, keyboard order, anchor destinations, image integrity, and one desktop/mobile screenshot pair. This is a future implementation check, not work performed by this audit. Run no Lighthouse audit unless separately authorized.

Only this audit document is delivered as a project change. Wait for approval before applying any recommendation.
