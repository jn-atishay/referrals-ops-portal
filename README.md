# Referrals Ops Portal

Internal CX resolution portal for the Skydo Referrals program.

**Live site:** https://jn-atishay.github.io/referrals-ops-portal/

## What this is

A single self-contained page (`index.html`) — the *Skydo Referrals: CX Resolution
Portal* playbook (v2.1). It bundles escalation flows, resolution scripts, and refund
/ SOP references for the referrals CX team. All CSS is inline, so there is no build
step and no dependencies.

> The page carries a `noindex, nofollow` tag so it stays out of search engines. The
> URL is still publicly reachable by anyone who has it — don't treat it as private.

## Editing

1. Edit `index.html` (it *is* the site).
2. Commit and push to `main`.
3. GitHub Pages redeploys automatically in ~1 minute.

```bash
git add index.html
git commit -m "Update playbook: <what changed>"
git push
```

## Hosting

Served by GitHub Pages from the `main` branch, root folder — the same setup as
[onboarding-flowchart](https://jn-atishay.github.io/onboarding-flowchart/).

## Adding collaborators

```bash
gh api -X PUT repos/jn-atishay/referrals-ops-portal/collaborators/<github-username> \
  -f permission=push
```

The invitee gets an email/notification and must accept before they can push.
