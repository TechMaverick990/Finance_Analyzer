# Contributing to Finance Analyser

Thank you for your interest in contributing! Here is everything you need to get started.

---

## Development Setup

1. Fork the repository on GitHub
2. Clone your fork locally:
   ```bash
   git clone https://github.com/YOUR_USERNAME/finance-analyser.git
   cd finance-analyser
   ```
3. Install dependencies:
   ```bash
   pnpm install
   ```
4. Start the dev server:
   ```bash
   pnpm dev
   ```

---

## Making Changes

### Branching

Always create a feature branch from `main`:

```bash
git checkout -b feature/your-feature-name
```

Use these prefixes:
- `feature/` — new functionality
- `fix/` — bug fixes
- `docs/` — documentation only changes
- `refactor/` — code cleanup with no behaviour change

### Code Style

- TypeScript is required — no plain `.js` files in `src/`
- Follow the existing Tailwind class patterns (dark gold theme: `#c9a84c` gold, `#f0e0c0` primary text)
- Run the linter before committing:
  ```bash
  pnpm lint
  ```
- Run a type check:
  ```bash
  pnpm build
  ```

### Adding New Vendor Categories

Edit `src/utils.ts` and add keywords to the `CATEGORY_KEYWORDS` object under the appropriate category. Use lowercase substrings that will match the vendor description from the bank:

```typescript
'Groceries': [
  // ... existing keywords ...
  'your new grocery store',
],
```

---

## Submitting a Pull Request

1. Push your branch to your fork:
   ```bash
   git push origin feature/your-feature-name
   ```
2. Open a Pull Request against the `main` branch of the original repository
3. Fill in the PR template (describe what changed and why)
4. Ensure the build passes (`pnpm build` runs without errors)

---

## Reporting Bugs

Open a [GitHub Issue](../../issues/new) and include:
- Steps to reproduce
- Expected behaviour
- Actual behaviour
- Browser and OS version
- A sample CSV (with sensitive data removed) if the bug is related to CSV parsing

---

## Suggesting Features

Open a [GitHub Issue](../../issues/new) with the label `enhancement` and describe:
- The problem you are trying to solve
- Your proposed solution
- Any alternatives you considered
