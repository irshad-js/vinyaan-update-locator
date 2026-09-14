# Agent guidance

## Mission

Maintain an exact public fallback copy of the signed Vinyaan staging extension tree.

## Read order

Read `README.md`, `mirror-inventory.json`, then workspace extension policy.

## Ownership

This repository owns GitHub Pages publication only. `vinyaanblocks` owns contracts and publishing tools; `bits32_lms` owns the primary staging tree.

## Invariants

- Never commit private keys, credentials, or unsigned generated locator/catalog data.
- Never hand-edit files under `ide/extensions` or `mirror-inventory.json`.
- Mirror the complete locator, catalog, manifest, and referenced artifact set.
- Preserve exact bytes; GitHub Actions deploys without signing or transformation.

## Commands

Run the shared mirror tool from `vinyaanblocks`; verify hashes before commit.

## Test matrix

Require shared publisher tests, byte-for-byte mirror parity, HTTPS availability, CORS readability, and GitHub Pages deployment success.

## Documentation duties

Keep this guide stable. Put milestone status and evidence in `vinyaan-workspace`.

## Git rules

Use `main`. Commit generated publication updates as one coherent batch. Push only after parity checks pass.

## Open questions

Track cross-repository decisions in `vinyaan-workspace/docs/open-questions.md`.
