# Changelog

## Unreleased

### Added
- Initial 21-screen SecOps Workbench prototype (static HTML, hand-tuned).
- Landing page `index.html` cross-linking all screens by cluster
  (Remediation tabs · Pages · Drawers · Overlays).
- Per-page metadata in `<head>` (`description`, `og:*`, `secops:screen-id`,
  `secops:narrative`, `secops:policy`).
- Example metadata layer under `metadata/`:
  - `screens.json`, `issues.json`, `agents.json`, `playbooks.json`,
    `policy.json`, `ceremonies.json`
  - Matching JSON Schema under `metadata/schema/`.
- README documenting the prototype layout and the SEC-1745 narrative thread.

### Notes
- Metadata is illustrative — not yet wired to a runtime.
- No build step: every screen is hand-tuned HTML with a single inline `<style>` block.
