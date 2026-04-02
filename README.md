# Attachment Theory & The Self — Leif Buechi
## Science of the Mind — University Assignment Website

---

## Project Overview

A single-page academic website built in vanilla HTML/CSS/JS. The site is a multimodal university submission exploring attachment theory personally and academically. It is deployed via GitHub + Netlify (auto-deploy on push).

**File structure:**
```
/
├── index.html        ← the entire site (single file)
└── README.md         ← this file
```

Everything — HTML, CSS, JavaScript, and Chart.js charts — lives in `index.html`. There are no external stylesheets, no build steps, no frameworks, no dependencies except Google Fonts and Chart.js (both loaded via CDN).

---

## Design System

### Colour Palette (CSS variables in `:root`)
| Variable | Hex | Usage |
|----------|-----|-------|
| `--teal` | `#1B6B6B` | Primary brand, hero background, nav, section accents |
| `--teal-light` | `#2A8F8F` | Hover states |
| `--teal-pale` | `#E1F5EE` | Light teal backgrounds, embed blocks |
| `--cream` | `#F9F5EF` | Page background, alternating sections |
| `--coral` | `#E8735A` | Accent colour, active states, section labels |
| `--coral-pale` | `#FAECE7` | Light coral backgrounds |
| `--charcoal` | `#2D2D2D` | Primary text, tigers section background |
| `--mid` | `#666` | Secondary text |
| `--border` | `#DDD8CF` | Borders, dividers |

### Typography
- **Display/headings:** `Playfair Display` (Google Fonts) — serif, used for titles, pull quotes, section titles
- **Body:** `DM Sans` (Google Fonts) — used for all body text, labels, nav
- Heading sizes: `clamp(1.8rem, 4vw, 2.8rem)` for section titles, `clamp(2.8rem, 7vw, 5.5rem)` for hero
- Body text: `1.02rem`, `line-height: 1.85`, `font-weight: 300`

### Layout
- Max content width: `900px` (`.container`), `1100px` (`.container-wide`)
- Fixed top navigation bar: `60px` height, `position: fixed`
- Sections use `min-height: 100vh`, `padding: 100px 0 80px`
- Responsive grid breakpoint: `700px` (collapses all 2-col grids to 1-col)

---

## Site Structure & Sections

The site is a single scrolling page with a fixed top nav. Each section has an `id` that the nav links to.

| Section ID | Nav Label | Background | Description |
|------------|-----------|------------|-------------|
| `#home` | Home | `--teal` | Hero with title, pull quote, nav buttons |
| `#science` | The Science | `--cream` | Part 1a — Mark Solms theory + Video 1 embed |
| `#mystory` | My Story | `white` | Part 1b Section 1 — Secure attachment + memories + Video 2 embed |
| `#numbers` | By The Numbers | `--cream` | Data charts — 3x Chart.js charts + data table |
| `#clara` | Clara & Me | `white` | Part 1b Case Study — relationship analysis + Video 4 placeholder |
| `#tigers` | The Tigers | `--charcoal` (dark) | Cross-species attachment evidence + Video 3 embed |
| `#references` | References | `white` | Full academic reference list |

---

## Video Embeds

All videos use the `.embed-block` / `.embed-wrap` pattern with a 16:9 `padding-bottom: 56.25%` responsive iframe.

| Location | Section | YouTube URL | Description |
|----------|---------|-------------|-------------|
| Video 1 | `#science` | `https://www.youtube.com/embed/YcQg1EshfIE` | Crash Course Psychology #19 — Harlow, Ainsworth, attachment styles |
| Video 2 | `#mystory` | `https://www.youtube.com/embed/YcQg1EshfIE?start=237` | Same video, starts at attachment styles section (3m57s) |
| Video 3 | `#tigers` | `https://www.youtube.com/embed/ZYAUyiuAG7s` | Dog raised Bengal tiger cubs — cross-species attachment |
| Video 4 | `#clara` | **PLACEHOLDER** — to be replaced | Clara interview — currently shows a teal placeholder box |

### ⚠️ To add Clara's interview video:
Find the `embed-placeholder` div inside the `#clara` section and replace the entire `.embed-wrap` contents with:
```html
<div class="embed-wrap">
  <iframe src="https://www.youtube.com/embed/YOUR_VIDEO_ID_HERE" title="Clara Interview" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
```
Replace `YOUR_VIDEO_ID_HERE` with the YouTube video ID from the unlisted URL.

---

## Charts (Chart.js)

Three charts are rendered via Chart.js 4.4.1 (loaded from cdnjs CDN). All chart scripts are at the bottom of `index.html` before `</body>`.

| Canvas ID | Type | Data | Source |
|-----------|------|------|--------|
| `pieChild` | Doughnut | Secure 63%, Avoidant 21%, Ambivalent 16% | Fonagy et al. (2014) |
| `pieAdult` | Doughnut | Secure 58%, Dismissing 23%, Preoccupied 19% | Fonagy et al. (2014) |
| `barChart` | Bar | Recovery speed scores: Secure 95, Hyperactivating 20, Deactivating 65, Disorganised 15 | Derived from Luyten & Fonagy (2014) Table 6.1 |

Chart colours: Secure = `#1D9E75` (teal), Avoidant/Hyperactivating = `#D85A30` (coral), Ambivalent/Preoccupied = `#BA7517` (amber), Disorganised = `#888780` (grey).

There is also a **static HTML table** (not Chart.js) in `#numbers` replicating Table 6.1 from Luyten & Fonagy (2014). The secure row has class `secure-row` giving it a green highlight.

---

## Key CSS Classes Reference

### Layout & Structure
- `.container` — max-width 900px centered wrapper
- `.container-wide` — max-width 1100px centered wrapper
- `.section-label` — small coral uppercase label above section titles
- `.section-title` — Playfair Display serif section heading
- `.section-divider` — 48px wide 3px coral horizontal rule

### Content Components
- `.pull-quote` — teal background block quote with coral opening quotemark
- `.prose p` — styled body paragraphs (300 weight, 1.85 line-height)
- `.memory-grid` — 2-column grid for memory boxes
- `.memory-box` — white card with teal top border (`.coral` variant has coral border)
- `.stat-grid` — 3-column grid for stat callout cards
- `.stat-card` — white card with large Playfair number and label
- `.chart-grid` — 2-column grid for chart cards
- `.chart-card` — white card containing chart canvas
- `.table-card` — card with teal header containing the mentalising table
- `.interaction-grid` — 2-column grid for Leif vs Clara comparison cards
- `.interaction-card.leif` — teal-accented card
- `.interaction-card.clara` — coral-accented card
- `.theory-chips` — flex row of pill badges (used in tigers section)
- `.theory-chip` — individual pill badge (dark background with coral `<strong>` text)

### Embed Components
- `.embed-block` — white card wrapping a video embed
- `.embed-label` — small uppercase teal label
- `.embed-caption` — grey caption text below label
- `.embed-wrap` — 16:9 responsive iframe wrapper (`padding-bottom: 56.25%`)
- `.embed-placeholder` — teal box shown when no video yet (Clara section)

### Reference List
- `.ref-list` — unstyled list for references
- `.ref-list li` — bordered reference entry with `<strong>` author/year

---

## Content Sections — Text Summary

### Part 1a — The Science (Mark Solms)
Theory of attachment as hardwired in subcortical brainstem circuits. PANIC/GRIEF circuit, CARE circuit, attachment as primal addiction. Bridges Bowlby and neuroscience.

### Part 1b Section 1 — My Story (Secure Attachment)
Author: Leif Buechi. Bicultural household — Brazilian mother (expressive), Swiss father (quiet). Two memory boxes: sailing with father (secure base), mother at hospital 4am (CARE circuit). Father's Hawaii transformation = shifting internal working model. Identifies as Type B secure.

### Part 1b Section 2 — By The Numbers
Statistical data from Fonagy et al. (2014) and Luyten & Fonagy (2014). Three stat callouts, two pie charts, one bar chart, one Table 6.1 reproduction.

### Part 1b Section 3 — Clara & Me (Case Study)
Girlfriend of 11 months. Clara = fearful-avoidant. Approach-avoidance dynamic. Leif as secure base, high mentalising threshold, corrective attachment experience. Broaden and build cycles. Bicultural upbringing gave complementary models of love.

### Cross-Species — The Tigers
Dog raised Bengal tiger cubs. Illustrates Harlow's contact comfort, Solms' CARE circuit, Van Rosmalen et al. on no biological tie required, Bowlby's internal working model persisting to adulthood.

### References
10 academic sources. Three marked `[Perlego]` as required by assignment brief.

---

## Academic Sources Used

All three required Perlego sources are marked `[Perlego]` in the reference list.

1. **Van Rosmalen, Van IJzendoorn & Bakermans-Kranenburg (2014)** — Chapter 1, Routledge Handbook of Attachment: Theory [Perlego]
2. **Fonagy, Lorenzini, Campbell & Luyten (2014)** — Chapter 2, Routledge Handbook of Attachment: Theory [Perlego]
3. **Luyten & Fonagy (2014)** — Chapter 6, Routledge Handbook of Attachment: Theory [Perlego]
4. Ainsworth, Blehar, Waters & Wall (1978) — Patterns of Attachment
5. Bowlby (1969) — Attachment and Loss Vol. 1
6. Bowlby (1973) — Attachment and Loss Vol. 2
7. Harlow (1958) — The Nature of Love
8. Panksepp (1998) — Affective Neuroscience
9. Solms (2021) — The Hidden Spring
10. Lecture slides — Attachment Theory, Science of the Mind, Week 9

---

## Common Edit Tasks for Claude Code

### Change text in a section
Find the section by its `id` (e.g. `id="science"`), locate the `.prose p` elements, and edit the text directly.

### Change a pull quote
Find `.pull-quote` inside the relevant section and edit the text. The `<cite>` tag inside is for the attribution line.

### Change a memory box
Find `.memory-box` inside `#mystory`. Edit `.memory-tag` (label), `.memory-title` (heading), `.memory-text` (body).

### Update a chart data value
Find the relevant `new Chart(...)` call in the `<script>` at the bottom. Change the `data: [...]` array values.

### Add Clara's video
Find the `.embed-placeholder` div inside `#clara` and replace the `.embed-wrap` div contents with a YouTube iframe (see Video Embeds section above).

### Change a section's background colour
Find the `<section id="...">` tag and update its inline `style="background:..."` attribute.

### Add a new stat card
Inside `.stat-grid` in `#numbers`, add:
```html
<div class="stat-card">
  <div class="stat-number">XX%</div>
  <div class="stat-label">Description here</div>
  <div class="stat-source">Source citation</div>
</div>
```

### Add a new reference
Inside `.ref-list` in `#references`, add:
```html
<li><strong>Author, A. (Year)</strong> <em>Title.</em> Publisher.</li>
```

---

## Deployment

- **GitHub repo:** add `index.html` and `README.md` to root
- **Netlify:** connected to GitHub repo, auto-deploys on every push to `main`
- **To update the live site:** edit `index.html` → commit → push → Netlify auto-deploys in ~30 seconds

---

## Assignment Brief Requirements Checklist

| Requirement | Status | Location |
|-------------|--------|----------|
| 1,500–2,000 words written content | ✅ | Across all prose sections |
| At least 4 images | ⚠️ To be added manually | Add via `<img>` tags in sections |
| At least 2 data charts | ✅ | 3 Chart.js charts in `#numbers` |
| At least 2 video/audio links | ✅ | 3 embedded YouTube videos |
| Each video has 1-sentence explanation | ✅ | `.embed-caption` under each embed |
| 3 academic sources from Perlego | ✅ | Chapters 1, 2, 6 of Routledge Handbook |
| Visually attractive with colour | ✅ | Teal/cream/coral design system |
| Multimodal format | ✅ | Text + charts + video + interactive |

### ⚠️ Images still needed (4 required)
The brief requires at least 4 images. These need to be added manually. Suggested placements:
1. `#science` — Harlow wire vs cloth monkey image
2. `#science` — Brain/neuroscience diagram
3. `#mystory` — Sailing / father and child image
4. `#clara` — Couple / relationship image

To add an image, use:
```html
<img src="YOUR_IMAGE_URL" alt="Description" style="width:100%; border-radius:12px; margin:1.5rem 0;">
```
Or place inside a styled card wrapper for a more polished look.
