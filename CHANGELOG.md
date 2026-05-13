# Changelog

## Unreleased

### Added
- GitHub Pages deployment via `.github/workflows/pages.yml`. Site auto-publishes
  on every push to `main`. Empty `.nojekyll` so Pages serves files verbatim.

### Changed
- **Navigation wired across the prototype.** Top-nav tabs, remediation
  context tabs, mobile bottom-nav and brand mark are now real `<a>` links
  that navigate between screens. Overlay close buttons (`19`, `21`) and the
  search overlay's Esc key call `history.back()`. Every screen is reachable
  from every other screen.

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
