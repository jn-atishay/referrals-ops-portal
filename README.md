# Referrals Ops Portal

Internal ops portal for the Skydo Referrals programme — CX resolution playbook,
tracking queries, gift/sheet links, and (in progress) self-serve campaign, credit
and gift-mail actions.

**Live site:** https://jn-atishay.github.io/referrals-ops-portal/

> Every page carries `noindex, nofollow`. The URL is still publicly reachable by
> anyone who has it — **don't** commit private Sheet URLs, customer PII, API keys,
> or anything you wouldn't want a stranger with the link to see.

## Pages

| File | Module | Status |
|---|---|---|
| `index.html` | Portal home — module hub + roadmap | Live |
| `playbook.html` | CX Resolution Playbook (v2.1, self-contained) | Live |
| `sql-tracking.html` | Tracking Guide — what to track & how | Live |
| `sheets-and-ids.html` | Sheets registry + gift tracking-ID scheme | WIP (links) |
| `campaigns.html` | Campaign Controls — self-serve action UIs | Planned (UI only) |
| `inventory.html` | Inventory, Orders & Finance | WIP (data) |
| `assets/portal.css` | Shared design system (tokens lifted from the playbook) | — |
| `assets/portal.js` | Shared behaviour (nav highlight, copy buttons, WIP form guards) | — |

## How it's built

- Plain static HTML — **no build step, no dependencies.** GitHub Pages serves the
  files as-is, same as before.
- Every module page links `assets/portal.css` + `assets/portal.js` so they share
  one look and one set of behaviours.
- `playbook.html` stays **fully self-contained** (its own inline CSS/JS) so its
  search still works untouched — it only gained the shared top-nav bar.
- "WIP" / "Planned" features are real UI with clearly-marked placeholders:
  `WIP` cells, disabled inputs, and `<form data-wip>` guards that show a notice
  instead of submitting. Backends get wired in later phases.

## Adding a module

1. Copy an existing module page (e.g. `sheets-and-ids.html`) to `yourmodule.html`.
2. Keep the `<nav class="portal-nav">` block and add your link to it **in every page**.
3. Add a `<a class="mod-card">` to the grid in `index.html` with a `status` badge
   (`live` / `wip` / `planned`) and a row in the roadmap table.
4. Use the shared classes: `.panel`, `.callout`, `.sqlq`, `table.data`, `.ops-form`,
   `.stat`, `.status`, `.wip-banner`.

## Tracking notes

`sql-tracking.html` is a **public page**, so it deliberately carries no production
connection details, schema, or customer IDs — just plain-English guidance on *what*
to track and *how* to think about querying it. Keep the concrete SQL recipes,
connection details and any customer/exporter IDs in the team's **private** space,
not in this repo.

## Editing & deploy

```bash
git add -A
git commit -m "Update: <what changed>"
git push
```

GitHub Pages redeploys from `main`/root in ~1 minute.

## Adding collaborators

```bash
gh api -X PUT repos/jn-atishay/referrals-ops-portal/collaborators/<github-username> \
  -f permission=push
```

The invitee gets an email/notification and must accept before they can push.
