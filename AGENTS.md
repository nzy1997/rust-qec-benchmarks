# Agent instructions

This repository is an immutable artifact store for RustQEC benchmark evidence.

- Preserve repository-relative artifact paths.
- Regenerate and verify `ARTIFACTS.sha256` after every payload change.
- Do not commit build caches, credentials, or unrelated source changes.
- Never rewrite a published artifact commit; publish a new commit and update
  the pin in `nzy1997/rust-qec`.
