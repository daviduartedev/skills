# Playwright

Load when **Driving** the live UI. Locator order and anti-patterns follow [Playwright Testing (Maggy)](https://github.com/alinaqi/maggy). The driver is `playwright-cli` against the URL from [local run](local-run.md).

## Driver

```bash
playwright-cli open http://localhost:PORT
playwright-cli goto /path
playwright-cli snapshot
playwright-cli find "visible text"
playwright-cli click "getByRole('button', { name: 'Save' })"
playwright-cli fill "getByRole('textbox', { name: 'Email' })" "user@example.com"
playwright-cli screenshot
```

If `playwright-cli` is missing: `npm install -g @playwright/cli@latest`. Prefer `localhost` over `127.0.0.1` when the _window_ said so. On Windows PowerShell, URLs with `&` need `--%` so the query string is not split.

## Locators

Use locators in this order (how a person uses the page):

1. Role: `getByRole('button', { name: 'Sign in' })`
2. Label, placeholder, or visible text
3. `getByTestId` when the page exposes one

Snapshot after each action that should change the page. `find` for copy. `run-code` when a form or calendar cannot be reached by a role locator.

## What to Drive

The same observable checks that will appear on the manual list, as far as the live UI allows: login with a documented profile, the happy path, the negative check. Report what the page showed. A blocked check (missing credential, no UI control) is `blocked`, not a silent skip.

## Out of this Drive

A committed Playwright spec, Page Object tree, CI workflow, or dead-link crawl — unless the _window_ asked for that file. Hardcoded sleeps. CSS or XPath as the first locator. Invented passwords.
