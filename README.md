# Enterprise Process Navigator

**APQC-Inspired Knowledge System** — A comprehensive, single-file web application for exploring, comparing, and learning from the APQC Process Classification Framework (PCF) across five industries.

---

## Overview

The Enterprise Process Navigator brings together **9,755 processes** spanning five APQC frameworks into an interactive, searchable knowledge system. Built as a zero-dependency HTML file, it runs entirely in your browser — no server, no installation, no internet required after download.

Whether you're benchmarking operations, designing process improvements, or training teams on industry standards, this tool provides instant access to structured process data, definitions, metrics, and cross-industry comparisons.

### Included Frameworks
- **Cross-Industry** v8.0 — 2,017 processes (foundation PCF)
- **Retail** v7.2.1 — 1,708 processes
- **Consumer Products** v7.2.2 — 1,997 processes
- **Consumer Electronics** v7.2.1 — 2,021 processes
- **Petroleum Downstream** v7.2.2 — 2,012 processes

---

## Getting Started

### Installation
1. Download `process_navigator.html`
2. Double-click to open in any modern web browser (Chrome, Safari, Firefox, Edge)
3. The app loads instantly — all data is embedded

**No internet connection required.** The app is fully self-contained.

### Browser Requirements
- Modern browser with ES6+ JavaScript support
- Local file access (file:// protocol)
- ~3 MB free memory

Tested on:
- Chrome 120+
- Safari 16+
- Firefox 121+
- Edge 120+

---

## Features

### 1. **Explorer** — Browse & Discover
The primary interface for navigating the PCF hierarchy.

**Left Sidebar: Industry Tree**
- Five industry sections with expandable hierarchy
- Five levels of nesting:
  - **L1**: Categories (e.g., "Plan" → 1.0, 2.0, 3.0)
  - **L2**: Process Groups (e.g., 1.1, 1.2)
  - **L3**: Processes (e.g., 1.1.1)
  - **L4**: Activities (e.g., 1.1.1.1)
  - **L5**: Tasks (e.g., 1.1.1.1.1)
- Color-coded by industry:
  - Slate: Cross-Industry
  - Amber: Retail
  - Green: Consumer Products
  - Blue: Consumer Electronics
  - Purple: Petroleum Downstream
- Click to select, keyboard navigation with arrow keys

**Right Panel: Process Details**
Expandable sections for the selected process:
- **Overview** — PCF ID, hierarchy code, description
- **Metrics** — Data availability flag (if applicable)
- **Sub-processes** — Child processes at the next level
- **Version Change History** — Changes from prior versions (Δ badge indicates presence)
- **Industry Availability** — 5-card matrix showing which industries include this process
- **Position in Framework** — ASCII tree showing ancestors in the hierarchy

**Metadata Badges**
- **M** — Process has metrics available
- **Δ** — Process changed in recent version (includes delta details)
- **♥** — Bookmarked (red when active)

---

### 2. **Compare** — Side-by-Side Analysis
Analyze how processes differ across industries.

**How to Use**
1. Select two industries from the dropdowns
2. Select a process (by ID, name, or from the tree)
3. View side-by-side descriptions with differences underlined
4. Navigate between industries' versions of the same process

**Highlights**
- Shows when a process name or description differs between industries
- Underlined text marks differences for quick spotting
- Reveals industry-specific variations of the same logical process

---

### 3. **Glossary** — Searchable Definitions Hub
A curated dictionary of all process definitions with smart filtering.

**Search & Filter**
- **Keyword search** — Searches process names and descriptions
- **Industry filter** — Limit to specific industries
- **Hierarchy level filter** — Show only Categories, Process Groups, Processes, Activities, or Tasks
- **Result cap** — Shows top 250 results; refine search to narrow results

**Variant Definitions**
- When a process appears in multiple industries with different descriptions, the glossary shows all variants
- Useful for understanding how industries interpret the same logical process

**Example**
- Search: "inventory"
- Filter by: Consumer Products + Process level
- Results: All inventory-related processes in Consumer Products, with definitions and industry context

---

### 4. **Map** — Visual Process Landscape
A card-based view for visual exploration and drilling.

**Layout**
- 13 category cards (1.0–13.0, e.g., "Plan," "Develop & Manage Products")
- Click a category to expand and see Process Groups
- Click a Process Group to drill into individual Processes
- Each card shows:
  - Process name
  - PCF ID
  - Count of sub-items
  - Industry indicators (colored dots)

**Use Case**
- Get an at-a-glance overview of the full PCF structure
- Identify which categories have the most processes
- Visual discovery without text search

---

### 5. **Path** — Learning Progress Tracker
Track your learning journey through the PCF.

**Bookmarks**
- Click the heart icon (♥) on any process to bookmark it
- View all bookmarks in a single list
- Remove bookmarks by clicking again

**Progress Tracking**
- Progress bar shows bookmarks as a percentage of:
  - **L1–L3 Cross-Industry Total**: 286 core processes across all categories/groups
- Useful for training programs, certification prep, or audit readiness

**Persistence**
- Your bookmarks and last-viewed state are saved to browser storage (localStorage)
- Survives browser close/restart on the same device
- **Note**: Clearing browser data will reset bookmarks

---

## Search & Navigation

### Global Search (⌘K / Ctrl+K)
Press the keyboard shortcut or click the search box in the header to activate.

**What You Can Search**
- **PCF IDs** — e.g., `10002` → finds "Develop Vision and Strategy"
- **Hierarchy codes** — e.g., `4.3.1` → finds process at that position
- **Process names** — e.g., `inventory` → finds all inventory-related processes
- **Descriptions** — e.g., `supply chain` → searches process definitions

**Navigation**
- **Arrow keys** ↑↓ — Move through results
- **Enter** — Select highlighted result
- **Escape** — Close search

### Sidebar Navigation
- **Click** — Select a process and view details
- **Arrow keys** ↑↓ — Move between processes
- **Right arrow** → — Expand a folder
- **Left arrow** ← — Collapse a folder

---

## Data Sources & Quality

### Source Data
All data extracted from official APQC PCF Excel workbooks (v7.2.1–v8.0), processed through a validated Python pipeline.

### Structural Details
- **PCF ID**: Unique identifier (e.g., 10002) consistent across all industries
- **Hierarchy Code**: Human-readable position in tree (e.g., 4.3.1)
- **Name**: Process title
- **Description**: Detailed explanation (sourced from "Combined" sheets in original Excel files)
- **Metrics**: Flag indicating data availability for that process
- **Change History**: Differences from prior PCF versions (when available)

### Fallback for Retail & Consumer Electronics
The Retail and Consumer Electronics frameworks did not include inline descriptions in their source sheets. When viewing these industries:
- Descriptions fall back to the Cross-Industry definition (when the PCF ID matches)
- The glossary notes the origin: "Cross-Industry definition used"
- This ensures comprehensive information without information gaps

### Data Completeness
- All 5 industries included in full
- All hierarchical levels (L1–L5) represented
- Metrics and change-history badges only appear where source data provided them

---

## Settings & Persistence

### Browser Storage (localStorage)
The app automatically saves:
- **Bookmarked processes** (`epn_bookmarks_v1`)
- **Last viewed state** (`epn_state_v1`) — current industry, selected process, expanded tree nodes

**To Reset**
1. Press F12 or Cmd+Option+I to open Developer Tools
2. Go to **Application** → **Storage** → **Local Storage**
3. Delete entries starting with `epn_`
4. Refresh the page

---

## Tips & Best Practices

### Benchmarking Operations
1. Use **Compare** to align your company's processes with industry standards
2. Note PCF IDs for documentation and reporting
3. Bookmark key processes to build a customized reference

### Training & Certification
1. Start with **Explorer** at **L1** (Categories) to get the big picture
2. Drill into **L2–L3** to understand process groups and core processes
3. Use **Glossary** to study definitions
4. Bookmark key processes and track progress in **Path**

### Process Documentation
1. Search by industry and PCF ID to find pre-defined process descriptions
2. Use **Details Panel** to see metrics and change history
3. Check **Industry Availability** to see how similar companies structure the process
4. Document cross-industry variations for alignment discussions

### Data Analysis
- Use **Metrics** badge to identify processes with data tracking capability
- Use **Δ** (delta) badge to understand what changed in recent PCF versions
- Cross-reference **Industry Availability** to benchmark staffing and resource allocation

---

## Keyboard Shortcuts

| Action | Shortcut |
|--------|----------|
| Open Search | Ctrl+K or Cmd+K |
| Move in Search Results | ↑ ↓ |
| Select from Search | Enter |
| Close Search / Dialog | Esc |
| Expand/Collapse Tree | → ← (when in sidebar) |
| Navigate Sidebar | ↑ ↓ (when in sidebar) |

---

## Technical Details

### Architecture
- **Single-file deployment**: All data, styles, and JavaScript embedded in one HTML document
- **Zero dependencies**: No frameworks, libraries, or external APIs required
- **Lightweight**: 2.74 MB total (with ~1.9 MB compressed JSON data)
- **Vanilla JavaScript**: ES6+, compatible with modern browsers

### Performance
- **Load time**: < 1 second (file:// protocol)
- **Search**: Indexed lookups < 50ms for 9,755 processes
- **Memory**: ~50–80 MB in-browser footprint

### Data Format (Internal)
```json
{
  "industry_order": ["cross", "retail", "cprod", "celec", "petro"],
  "industries": {
    "retail": {
      "name": "Retail",
      "version": "7.2.1",
      "processes": [
        {
          "id": 10002,
          "h": "1.1.1",
          "n": "Develop Vision and Strategy",
          "l": 3,
          "d": "Description here...",
          "m": true,
          "ch": "Changed in v7.2.0",
          "di": "Industry-specific variant"
        }
      ]
    }
  }
}
```

---

## FAQ

**Q: Do I need internet to use this?**  
A: No. The app is fully self-contained. You only need internet to first download the file.

**Q: Can I modify or extend the data?**  
A: The HTML file is not designed for easy editing. However, the embedded JSON is clearly marked with `<script id="pcf-data" type="application/json">`. Advanced users can extract, modify, and re-embed it if needed.

**Q: My bookmarks disappeared. What happened?**  
A: Bookmarks are stored in browser local storage. If you cleared your browser cache or switched browsers/devices, they will be lost. Consider exporting your bookmarks (not currently automated—manual copy from **Path** tab is recommended).

**Q: Why are some processes missing for Retail/Consumer Electronics?**  
A: Retail and Consumer Electronics source files did not include individual process descriptions. The app falls back to Cross-Industry descriptions when PCF IDs match, ensuring no information gap. This is noted in the glossary with an origin label.

**Q: How often is the data updated?**  
A: This snapshot includes PCF versions as of early 2025. For the latest APQC frameworks, download the current Excel files from [apqc.org](https://www.apqc.org) and regenerate the HTML (requires Python data extraction script).

**Q: Can I share this file with colleagues?**  
A: Yes. The HTML file is self-contained and has no licensing restrictions for internal business use. Share the file freely within your organization.

**Q: What if the app doesn't load?**  
A: Ensure you are:
1. Using a modern browser (Chrome, Safari, Firefox, Edge)
2. Accessing the file as `file://` (double-click works)
3. Not opening it in a text editor

---

## Support & Feedback

This tool was built to make APQC frameworks accessible and interactive. If you encounter issues or have feature requests, consider:

1. **Search refinement** — Try shorter keywords or PCF IDs
2. **Sidebar navigation** — Expand the industry tree to browse manually
3. **Glossary search** — Filter by hierarchy level to narrow results

---

## Version History

### v1.0 (May 2026)
- Initial release
- All 5 APQC frameworks integrated
- Explorer, Compare, Glossary, Map, and Path tabs
- Global search with keyboard shortcuts
- Bookmarks with progress tracking
- Browser storage persistence
- Industry color coding
- Metadata badges (Metrics, Change History, Bookmarks)

---

## License & Attribution

**APQC Process Classification Framework** — Data sourced from official APQC PCF Excel workbooks v7.2.1–v8.0.

This application is a knowledge interface tool. APQC is a registered trademark. For questions about PCF usage rights, refer to [apqc.org](https://www.apqc.org).

**About APQC** : 

An internationally recognized resource for process and performance improvement, APQC helps organizations adapt to rapidly changing environments, build new and better ways to work, and succeed in a competitive marketplace. With a focus on productivity, knowledge management, benchmarking, and quality improvement initiatives, APQC works with its member organizations to identify best practices; discover effective methods of improvement; broadly disseminate findings; and connect individuals with one another and the knowledge, training, and tools they need to succeed. Founded in 1977, APQC is a member-based nonprofit serving organizations around the world in all sectors of business, education, and government. APQC is also a proud winner of the 2003, 2004, 2008, 2012, and 2013 North American Most Admired Knowledge Enterprises (MAKE) awards. This award is based on a study by Teleos, a European based research firm, and the KNOW network.

**COPYRIGHT AND ATTRIBUTION** : 

©2022 APQC. ALL RIGHTS RESERVED. This Process Classification Framework® ("PCF") is the copyrighted intellectual property of APQC. APQC encourages the wide distribution, discussion, and use of the PCF for classifying and defining organizational processes. Accordingly, APQC hereby grants you a perpetual, worldwide, royalty-free license to use, copy, publish, modify, and create derivative works of the PCF, provided that all copies of the PCF and any derivative works contain a copy of this notice.


**Designed by Zamir Gori**



---

**Built for process professionals, operational analysts, and teams dedicated to continuous improvement.**

*Last updated: May 12, 2026*
