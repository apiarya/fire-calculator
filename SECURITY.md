# Security Policy

## Scope

This project is a **fully client-side, static HTML application**. It has no backend, no server, no database, and no user accounts. No data is collected, stored, or transmitted.

## What to report

Please report any of the following via a [private security advisory](https://github.com/apiarya/fire-calculator/security/advisories/new):

- Accidental inclusion of secrets, tokens, or API keys in the codebase
- Cross-site scripting (XSS) vulnerabilities in the HTML/JS
- Any logic that inadvertently collects or leaks user input

## What is out of scope

- Theoretical attacks requiring physical access to the user's machine
- Issues in third-party CDN libraries (Bootstrap, Chart.js) — report those upstream

## Guidelines for contributors

- **Never commit** `.env`, API keys, tokens, or credentials of any kind
- **Never add** fetch calls, form submissions, or any code that sends data to a server
- **Never collect** name, email, date of birth, SSN, or any PII
- All secrets scanning is automated via GitHub Actions on every push and PR
