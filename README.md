# SecOps Workbench — static prototype

A 21-screen exploration of an **agentic security remediation workbench**: Fortify,
Sonatype, Jira and GitLab feed an agentic Scrum team (SCN · TRG · DEV · REV · ORC)
that triages, fixes and ships security findings under policy. Every screen in this
prototype is governed by `secops-policy@v3.2`.

This repo is the working prototype: a set of hand-tuned static HTML screens plus
an example **metadata** layer ready to plug into a real backend later.

## Quick start

```bash
# from the repo root
python3 -m http.server 8000
# then open http://localhost:8000/
```

Or simply double-click `index.html` — every link is relative.

The prototype is also published via **GitHub Pages** on every push to `main`:
<https://pratiyush.github.io/Sec-ops/>

> First-time setup: in repo Settings → Pages, set **Source** to "GitHub Actions".
> The workflow at `.github/workflows/pages.yml` handles the rest.

## Screens

The landing page (`index.html`) groups all 21 screens into four clusters.

| Cluster              | Count | Files                                         |
| -------------------- | ----- | --------------------------------------------- |
| Remediation tabs     | 6     | `01-remediation.html` … `06-verdict.html`     |
| Top-level pages      | 3     | `07-intake.html`, `08-sprint.html`, `09-agentbook.html` |
| Utility drawers      | 9     | `10-integrations.html` … `18-settings.html`   |
| Overlays             | 3     | `19-approval-modal.html` … `21-toasts.html`   |

### Narrative thread — SEC-1745

Day 8 of Sprint 7. A critical SQL injection in `OrderRepository`. Thirteen of the
21 screens trace one decision: Alice's final approval. The thread enters at
**#07 Intake**, reaches its crux at **#19 Approval modal**, and closes with the
success toast at **#21**.

## Metadata layer

The `metadata/` folder contains example JSON manifests extracted from the design.
Nothing is wired to a runtime yet — these are illustrative payloads.

```
metadata/
  screens.json      # 21-screen manifest with clusters, threads, policy refs
  issues.json       # SEC-1745 + 3 sibling issues
  agents.json       # SCN, TRG, DEV, REV, ORC with tier + permissions
  playbooks.json    # 6 playbooks; spring-csrf@1.2 ready for T1 promotion
  policy.json       # secops-policy@v3.2 rules + pending v3.3 (backup-approver)
  ceremonies.json   # Sprint 7 Review & Retro agenda
  schema/           # JSON Schema for each manifest
```

Each HTML screen also carries page-level metadata in `<head>`:

```html
<meta name="description"        content="…"/>
<meta name="secops:screen-id"   content="07"/>
<meta name="secops:narrative"   content="SEC-1745"/>
<meta name="secops:policy"      content="secops-policy@v3.2"/>
<meta property="og:title"       content="…"/>
<meta property="og:description" content="…"/>
```

The custom `secops:*` tags pair each page with its entry in `screens.json`.

## Design system

- Font: **Geist** + **Geist Mono** (via Google Fonts).
- Palette: stone neutrals with red/orange/yellow/green/blue/purple/teal accents.
- Light + dark mode (preference persisted in `localStorage`).
- No build step: every screen is hand-tuned HTML + a single inline `<style>` block.

## Status

| Item                            | Status   |
| ------------------------------- | -------- |
| 21 screens                      | shipped  |
| Landing page with cross-links   | shipped  |
| Page-level `<meta>` tags        | shipped  |
| Example JSON manifests + schema | shipped  |
| Wired to real backend           | deferred |
| React/Vite port                 | deferred |
