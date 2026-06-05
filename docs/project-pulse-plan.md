# Project Pulse — Implementation Plan

## 1. Overview

**Project Pulse** is a lightweight, browser-based dashboard that visualizes project health metrics for a team or portfolio. It is a fully static front end (HTML + CSS + vanilla JS) that loads its content from a local JSON file at runtime.

**Goals**
- Give stakeholders an at-a-glance view of project status, key metrics, and team composition.
- Keep the architecture trivial to host (open `index.html` in any browser or serve via Live Server).
- Separate concerns cleanly: structure (HTML), presentation (CSS), data (JSON), and developer ergonomics (VS Code launch config).
- Provide a foundation that can later be extended with charts, filters, or a real API.

**Non-goals**
- No backend, no build step, no framework.
- No authentication or persistence.

---

## 2. File Assignments

| File | Owner | Purpose |
|---|---|---|
| `app/index.html` | **Coder** (structure + JS), guided by **Designer** (layout/semantics) | Dashboard markup, semantic regions for header/KPIs/projects/team, inline `<script>` that fetches `project-data.json` and renders the DOM. |
| `app/styles.css` | **Designer** | Visual design system: color tokens, typography, spacing, grid/flex layout, status badges, responsive breakpoints. |
| `app/project-data.json` | **Coder** | Realistic sample data: overall KPIs, list of projects (name, status, health score, owner, due date, progress), and team roster. |
| `.vscode/launch.json` | **Coder** | One-click launch configuration (Live Server or Chrome debugger) targeting `app/index.html`. |

---

## 3. Designer Responsibilities

- Define the **visual direction**: color palette (including semantic status colors — green/amber/red), typography scale, spacing scale, and iconography approach.
- Produce **layout decisions**:
  - Page shell: header with product name + timestamp, KPI strip, projects grid/table, team section, footer.
  - Responsive behavior: 1-column on mobile, multi-column grid on desktop.
- Author **`app/styles.css`** in full, including:
  - CSS custom properties (`:root` tokens) for colors, spacing, radii.
  - Component styles: `.kpi-card`, `.project-card`, `.status-badge--healthy|at-risk|critical`, `.progress-bar`, `.team-member`.
  - Accessible contrast (WCAG AA) and focus styles.
- Provide **structural guidance to the Coder** for `index.html`: required semantic elements, class names, and ARIA landmarks so styles attach cleanly.
- Provide a short **style guide comment block** at the top of `styles.css` documenting tokens.

---

## 4. Coder Responsibilities

- Implement **`app/index.html`**:
  - Valid HTML5 doctype, `<meta charset>`, `<meta viewport>`, descriptive `<title>`.
  - Link `styles.css` in `<head>`.
  - Use the semantic regions and class names agreed with the Designer.
  - Inline `<script type="module">` (or plain `<script defer>`) that:
    - `fetch('./project-data.json')` → parses JSON.
    - Renders KPIs, project cards, and team members into placeholder containers (`#kpis`, `#projects`, `#team`).
    - Handles fetch/parse errors by rendering a visible error message.
    - Formats dates and progress values for display.
- Author **`app/project-data.json`** with a clear schema and realistic sample values.
- Author **`.vscode/launch.json`** with a Live Server or Chrome configuration that opens `app/index.html`.
- Ensure the JSON file is well-formed and matches what the HTML/JS expects.

### Proposed `project-data.json` schema

```json
{
  "generatedAt": "2026-06-05T12:00:00Z",
  "kpis": {
    "activeProjects": 7,
    "onTrack": 5,
    "atRisk": 1,
    "critical": 1,
    "averageHealth": 82
  },
  "projects": [
    {
      "id": "proj-001",
      "name": "Atlas Migration",
      "status": "healthy",
      "healthScore": 92,
      "progress": 0.75,
      "owner": "A. Rivera",
      "dueDate": "2026-08-15"
    }
  ],
  "team": [
    { "name": "A. Rivera", "role": "Tech Lead", "availability": 0.6 }
  ]
}
```

### Proposed `.vscode/launch.json` shape

Use the **Live Server** extension's launch action, or a Chrome debug config pointed at the local server. Note: `fetch` to a local file may be blocked by browsers; a static server like Live Server is preferred and should be the primary configuration.

---

## 5. Dependencies

```
project-data.json schema  ──►  index.html render JS (reads exact field names)
Designer class-name contract ──►  index.html structure (selectors must match)
styles.css ◄──► index.html (co-dependent; styles drafted from contract, polished after render)
.vscode/launch.json  ──►  no dependencies (only needs app/index.html path to exist eventually)
```

- `app/project-data.json` **schema** must be agreed before `index.html`'s render JS is written.
- `app/index.html` **structure** depends on the Designer's class names and layout decisions.
- `app/styles.css` can be drafted in parallel with HTML implementation from the agreed contract.
- `.vscode/launch.json` has **no dependencies** on other files.

---

## 6. Parallel Work Decisions

**Can run in parallel (Phase 1)**
- Designer drafting `styles.css` (tokens, component styles) against the agreed class-name contract.
- Coder authoring `project-data.json`.
- Coder authoring `.vscode/launch.json`.

**Must run sequentially (Phase 2)**
- `index.html` implementation must come **after**:
  1. Designer's structural/class-name contract is published, **and**
  2. JSON schema is finalized.
- Final visual QA on `styles.css` must come **after** `index.html` renders real data.

---

## 7. Phases

### Phase 1 — Foundations (parallel)
- **Designer:** publish the structural contract (regions, class names, ARIA) + first pass of `app/styles.css` with tokens and component styles.
- **Coder:** write `app/project-data.json` with the schema above and realistic sample data.
- **Coder:** write `.vscode/launch.json` (Live Server preferred).

### Phase 2 — Integration (sequential)
- **Coder:** implement `app/index.html` consuming the Designer's contract and the JSON schema, including the fetch/render script and error handling.

### Phase 3 — Validation & Polish
- Open the dashboard via the VS Code launch config.
- Designer reviews rendered output and adjusts `styles.css` for spacing, hierarchy, and responsive behavior.
- Coder fixes any rendering or data formatting issues surfaced during review.

---

## 8. Validation Expectations

- [ ] **HTML loads cleanly:** `app/index.html` opens in a browser with no console errors and no broken asset references.
- [ ] **CSS is wired:** `styles.css` is linked from `<head>`; computed styles confirm tokens and layout are applied.
- [ ] **JSON is valid and consumed:** `project-data.json` parses without error; KPI values, project cards, and team members visible on page match the JSON.
- [ ] **Launch config works:** Running the `.vscode/launch.json` configuration opens the dashboard in one click via a local server.
- [ ] **Error path:** Temporarily renaming `project-data.json` causes a visible, user-friendly error message instead of a blank page.
- [ ] **Responsive check:** Layout collapses gracefully at ~375px width and expands at ≥1024px.
- [ ] **Accessibility smoke test:** Landmarks present (`header`, `main`, `section`), color contrast meets WCAG AA on status badges and body text.
