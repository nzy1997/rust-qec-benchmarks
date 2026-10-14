# RustQEC benchmark artifacts

This repository stores large, generated benchmark evidence for
[RustQEC](https://github.com/nzy1997/rust-qec). Keeping the raw results here
allows the source repository to remain fast to clone while preserving exact,
publicly auditable evidence.

The source repository pins an immutable commit from this repository in
`tools/benchmark_artifacts_revision.txt`. Its fetch helper verifies every file
against `ARTIFACTS.sha256` before installing the evidence at the original
repository-relative path.

## Contents

- `benchmarks/near_clifford/results/`: retained near-Clifford benchmark runs.
- `ARTIFACTS.sha256`: SHA-256 manifest for every retained file.

## Updating artifacts

Add or replace the generated evidence, regenerate the complete manifest, and
commit the result. Never change an existing commit or reuse a revision after
its contents have been published.

```sh
LC_ALL=C find benchmarks/near_clifford/results -type f -print0 \
  | LC_ALL=C sort -z \
  | xargs -0 shasum -a 256 > ARTIFACTS.sha256
shasum -a 256 -c ARTIFACTS.sha256
```

## License

Apache-2.0. See `LICENSE`.
