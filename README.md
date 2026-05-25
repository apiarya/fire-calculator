# FIRE Retirement Calculator

[![Live](https://img.shields.io/badge/live-GitHub%20Pages-blue?style=flat-square)](https://apiarya.github.io/fire-calculator/)
[![License: MIT](https://img.shields.io/badge/license-MIT-green?style=flat-square)](LICENSE)
[![Last commit](https://img.shields.io/github/last-commit/apiarya/fire-calculator?style=flat-square)](https://github.com/apiarya/fire-calculator/commits/main)

An interactive, single-page retirement calculator that helps you answer one question: **are you on track to retire early?**

Enter your income, savings, monthly contributions, and spending. The calculator models your portfolio growth through retirement and shows whether your money outlasts you — updated live as you type.

**[→ Find your FIRE number](https://apiarya.github.io/fire-calculator)**

Found a bug or have a question? [Open an issue](https://github.com/apiarya/fire-calculator/issues)

---

![FIRE Retirement Calculator](image.png)

---

## Why this exists

Most FIRE calculators are either too simple (a single number) or too complex (spreadsheet hell). This one aims to be just right — grounded in real math, usable in 2 minutes, and honest about its assumptions.

## What it models

- Portfolio growth during accumulation (pre-retirement)
- Inflation-adjusted drawdown during retirement
- Social Security and other guaranteed income offsets
- The 4% rule / 25× target, with a live chart showing your trajectory
- Save multiple scenarios in-memory to compare side by side

## Tech

Pure HTML/CSS/JS. No framework, no build step, no server, no tracking. Everything in `index.html`. Hosted on GitHub Pages.

## Limitations

- No taxes modeled (accumulation or drawdown)
- No sequence-of-returns risk
- Social Security is user-entered, not calculated from earnings history
- Single blended portfolio (no 401k vs Roth vs brokerage distinction)

> Educational only — not financial advice.
