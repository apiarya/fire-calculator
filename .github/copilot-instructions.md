# FIRE Retirement Calculator — Copilot Instructions

## Project Identity
A **single-file, client-side HTML retirement calculator** — interactive, anonymous, and educational. Hosted on **GitHub Pages** via `index.html`. No build step, no server, no tracking.

---

## Locked Decisions (Do Not Change Without Asking)
- **Single file**: Everything lives in `index.html` — HTML, CSS, JS
- **No server**: No fetch calls, no localStorage, no cookies
- **Analytics**: Cloudflare Web Analytics (cookie-free, no PII, aggregate page views only) — do not add any other analytics or tracking
- **No PII**: Never ask for name, DOB, email, SSN. Use age (not DOB), anonymous inputs only
- **US-focused**: 401(k), Roth IRA, HSA, Social Security, US tax context
- **Theme**: Bootstrap 5, light theme, blue/amber accent palette
- **Charts**: Chart.js 4.x (CDN) — no D3, no Highcharts
- **Scenarios**: In-memory only — not persisted between sessions

---

## Tech Stack
```
Bootstrap 5.3      https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css
Bootstrap Icons    https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.css
Chart.js 4.x       https://cdn.jsdelivr.net/npm/chart.js
Bootstrap JS       https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js
```
All loaded from CDN. No npm, no build step, no bundler.

---

## File Structure
```
fat-fire/
  index.html                    <- The entire app (published to GitHub Pages)
  verify-calc.mjs               <- Node.js math verification suite (node verify-calc.mjs)
  README.md                     <- Project readme
  .gitignore
  .github/
    copilot-instructions.md     <- This file
```

---

## Architecture

### State Object
- Single `const S = { ... }` — the only source of truth
- Updated from DOM inputs via `oninput` / `onblur` handlers
- Never persisted outside the page session

### Layout
- Two-column (Bootstrap grid): left `col-lg-5` = input cards, right `col-lg-7` = results
- Right panel: scenarios bar -> result cards -> chart -> life timeline slider
- All inputs update results live on every `oninput`

### Calculation Layer
- Pure JS math, no libraries
- Accumulation: FV of lump sum + FV of monthly contributions, compounded monthly
- Drawdown: PV of growing annuity (inflation-adjusted monthly spending minus guaranteed income)
- Need = 25x rule (4% SWR) applied to net monthly gap

### Chart
- Chart.js line chart, real age on x-axis, portfolio value on y-axis
- Blue solid line = "what you'll have", amber dashed = "what you'll need"
- Inline `phaseBands` plugin: colored fills, dashed vertical lines + pills at current/retire age
- Tooltip shows surplus/deficit

### Scenario System
- `const scenarios = []` — in-memory array of `{ label, values }` snapshots
- `captureInputs()` / `restoreInputs(v)` snapshot/restore all input field values
- Chips rendered in `#scenarios-list`; clicking restores; x deletes

---

## Default Values (Bay Area high-tech, married, dual income)
```js
const S = {
  married: true, age: 46, income: 480000, savings: 1500000,
  contribRetire: 10000, contribBrokerage: 5000, budgetVal: 18000,
  otherIncome: 0, ssIncome: 3500,
  retireAge: 58, lifeExpect: 90,
  preRate: 0.06, postRate: 0.05, inflation: 0.03, raise: 0.00
};
```

---

## Math Verification
Run `node verify-calc.mjs` from the project root. 18 tests covering accumulation, inflation, SS offset, PV growing annuity, 25x rule, drawdown, and edge cases.

---

## What NOT to Do
- Do not use React, Vue, Angular, or any framework
- Do not add a backend, API calls, or form submissions
- Do not collect or log any user input
- Do not ask for name, email, date of birth, SSN, address
- Do not generate or guess external URLs
- Do not add features beyond what is requested
- Do not add docstrings or comments to unchanged code sections
