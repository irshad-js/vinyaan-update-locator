# Agent guidance

## Mission

Maintain an exact public fallback copy of the signed Vinyaan staging extension tree.

## Read order

Read `README.md`, `mirror-inventory.json`, then workspace extension policy.

## Ownership

This repository owns GitHub Pages publication only. `vinyaanblocks` owns contracts and publishing tools; `bits32_lms` owns the primary staging tree.

## Invariants

- The published tree is the complete locator, catalog, manifest, and referenced
  artifact set; GitHub Actions deploys committed bytes without signing or
  transformation.

## Boundaries

✅ Always:
- Preserve exact bytes; the mirror stays byte-for-byte with the signed staging
  tree.

🚫 Never:
- Never commit private keys, credentials, or unsigned generated locator/catalog
  data.
- Never hand-edit files under `ide/extensions` or `mirror-inventory.json`.

## Commands

### Bootstrap

The complete operator runbook is `../vinyaan-workspace/docs/extensions.md`.
Build `../vinyaanblocks` with `npm run build` before refreshing the mirror.

### Verify

Refresh the mirror from the LMS staging tree:

```powershell
node ..\vinyaanblocks\tools\sync-extension-mirror.mjs `
  --source-root ..\bits32_lms\public\ide\extensions `
  --destination-root .
```

The tool verifies byte parity against the publish manifest and writes
`mirror-inventory.json`; commit the complete generated tree as one batch.

## Test matrix

Require shared publisher tests, byte-for-byte mirror parity, HTTPS availability, CORS readability, and GitHub Pages deployment success.

## Documentation duties

Keep this guide stable. Put milestone status and evidence in `vinyaan-workspace`.

## Git rules

Use `main`. Commit generated publication updates as one coherent batch. Push only after parity checks pass.

## Open questions

Track cross-repository decisions in `vinyaan-workspace/docs/register.md`.
