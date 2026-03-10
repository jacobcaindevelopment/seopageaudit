# ⚡ PageAudit

**A browser-based SEO and content audit tool for your top website pages.**

Upload your GA4 traffic data, paste page source HTML, and get a prioritised report of SEO issues, content gaps, and technical fixes — with a downloadable PDF.

No login. No server. No setup. Just open the URL and go.

---

## 🔗 Live App

👉 **[jacobcaindevelopment.github.io/seopageaudit](https://jacobcaindevelopment.github.io/seopageaudit)**

---

## What It Does

PageAudit replaces the manual process of opening each page, checking the source, and writing down issues in a spreadsheet. Instead:

1. Export your top pages from GA4 (30 seconds)
2. Select which pages to audit
3. Paste the HTML source for each page (Ctrl+U in any browser)
4. Get a full prioritised report with actionable recommendations
5. Download a presentation-ready PDF

---

## Workflow

### Step 1 — Export from GA4

1. Open **Google Analytics → Reports → Engagement → Pages and screens**
2. Set your date range (top-right corner)
3. Click the **download icon** → **Download CSV**

> PageAudit handles all GA4 CSV formats automatically, including the comment lines GA4 adds at the top of every export.

---

### Step 2 — Load your data

Open the app and either:
- **Upload CSV** — drag and drop your GA4 export
- **Paste data** — copy rows directly from the GA4 table
- **Try Demo** — loads sample car dealership data to explore the tool

Enter your website URL (e.g. `https://yourwebsite.com`).

---

### Step 3 — Select pages to audit

Your pages are ranked by traffic (Views by default). The top 10 are pre-selected.

- Select up to **25 pages**
- Deselect any pages you don't want to include
- Click **Start Audit →**

---

### Step 4 — Paste HTML source for each page

For each selected page you'll see a panel with the page URL and a paste box.

**How to get the page source (takes ~20 seconds per page):**

1. Click **Open page ↗** to open the page in a new tab
2. Press **Ctrl+U** (Windows) or **⌘+Option+U** (Mac)
3. A new tab opens showing the raw HTML source
4. Press **Ctrl+A** then **Ctrl+C** to copy everything
5. Switch back to PageAudit and paste into the box
6. Click **Analyse this page ✓**

> This works on any website regardless of Cloudflare protection or bot blocking — because you're viewing it in your own authenticated browser session.

**Don't want to audit a page?** Click **Skip (manual review)** — it stays in the report with its traffic data but is flagged for manual review.

The sidebar shows your progress. PageAudit automatically advances to the next page after each one is saved.

---

### Step 5 — Generate the report

Click **Generate Report →** at any point (top-right or sidebar).

You'll see:

- **Summary stats** — pages audited, total findings, critical + high issues, quick wins
- **Page findings** — expandable cards for each page, sorted by priority score
- **Priority labels** — HIGH / MEDIUM / LOW based on traffic × issue severity
- **Quick Win tags** — issues that are fast to fix and high impact

---

### Step 6 — Download the PDF

Click **⬇ Download PDF** to get a presentation-ready report including:

| Section | Contents |
|---|---|
| Cover page | Domain, date, metric used, summary numbers |
| Executive Summary | Stats overview + priority breakdown table |
| Pages Overview | All pages ranked by traffic with priority and issue count |
| Page-by-Page Findings | Every issue with description and recommendation |
| Quick Wins Summary | All quick-win fixes across all pages in one table |
| Manual Review | Pages that were skipped or not analysed |

---

## What Gets Checked

### SEO
| Check | Why It Matters |
|---|---|
| Missing title tag | Single biggest on-page SEO signal |
| Title too long / short | Google truncates at ~60 chars |
| Missing meta description | Controls SERP click-through rate |
| Meta description too long / short | Truncated or underused in search results |
| Missing H1 | Tells Google the primary topic of the page |
| Multiple H1 tags | Dilutes heading hierarchy |
| Thin content (<300 words) | May be ranked as low quality |
| No structured data | Misses rich result opportunities |
| Low internal linking | Limits authority distribution |

### Technical
| Check | Why It Matters |
|---|---|
| Missing canonical tag | URL variants split SEO authority |
| Images missing alt text | Accessibility (WCAG 2.1 AA) + image SEO |
| Incomplete Open Graph tags | Poor social share previews |
| Missing viewport meta tag | Broken mobile rendering |

### Content
| Check | Why It Matters |
|---|---|
| No H2 subheadings on long pages | Users scan before reading — structure reduces bounce |
| Meta description misaligned with title | Keyword inconsistency hurts CTR |

---

## Priority Scoring

Each page gets a score out of 100:

```
Score = Traffic Weight (0–50) + Issue Weight (0–50)

Traffic Weight = ((total pages − page rank + 1) / total pages) × 50
Issue Weight   = sum of: CRITICAL=15, HIGH=10, MEDIUM=5, LOW=2  (capped at 50)

HIGH   = score ≥ 65
MEDIUM = score ≥ 40
LOW    = score < 40
```

Your highest-traffic pages with the most serious issues always appear at the top.

---

## Technical Notes

- **Runs entirely in your browser** — no data is sent anywhere
- **No login, no account, no tracking**
- **GA4 CSV formats supported** — handles all column name variants and the `#` comment lines GA4 adds at the top of every export
- **Numbers parsed correctly** — `12,345` → `12345`, `1.2K` → `1200`
- **PDF generated client-side** using [jsPDF](https://github.com/parallax/jsPDF) + [jspdf-autotable](https://github.com/simonbengtsson/jsPDF-AutoTable)

---

## Deploying Your Own Copy

This is a single HTML file. To host it yourself:

### GitHub Pages (recommended — free)
1. Fork this repo
2. Go to **Settings → Pages**
3. Set branch to `main`, folder to `/ (root)`
4. Your URL: `https://YOUR-USERNAME.github.io/pageaudit/`

### Netlify (even easier)
1. Drag `index.html` onto [app.netlify.com/drop](https://app.netlify.com/drop)
2. Get an instant URL — no account needed

### Any web server
Upload `index.html` to any static hosting. No build step, no dependencies, no configuration.

---

## Known Limitations

| Limitation | Reason |
|---|---|
| Cannot auto-fetch pages | CORS and Cloudflare block browser requests — source paste is intentional |
| Cloudflare-protected pages | Ctrl+U in your own browser works because you're already authenticated |
| Login-required pages | Same — Ctrl+U works while you're logged in |
| Large GA4 exports | Only the top 25 pages by traffic are used |

---

## Stack

- Vanilla HTML + CSS + JavaScript — zero dependencies, zero build tools
- [jsPDF 2.5.1](https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js)
- [jsPDF-AutoTable 3.8.2](https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.8.2/jspdf.plugin.autotable.min.js)
- [Google Fonts — DM Sans + JetBrains Mono](https://fonts.google.com)

---

## License

Private — this application is for private use only, free to use, can not copy or duplicate.
