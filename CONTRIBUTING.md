# Contributing

Thanks for your interest in improving this calculator!

## Ground rules

- **No backend** — this is a static HTML file. No fetch calls, no form submissions, no server.
- **No PII** — never collect name, email, DOB, SSN, or any personal data.
- **No secrets** — never commit API keys, tokens, `.env` files, or credentials. Secret scanning runs automatically on every PR.
- **No frameworks** — vanilla JS only. No React, Vue, or bundlers.

## How to contribute

1. Fork the repo and create a branch from `main`
2. Make changes to `index.html` (everything lives there)
3. Run `node verify-calc.mjs` to confirm math is intact (18/18 must pass)
4. Open a pull request with a clear description of what changed and why

## Reporting issues

Found a bug or have a suggestion? [Open an issue](https://github.com/apiarya/fire-calculator/issues).

For security concerns, see [SECURITY.md](SECURITY.md).
