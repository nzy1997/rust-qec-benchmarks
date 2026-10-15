# Two-workload near-Clifford campaign closeout

Report date: 2026-10-15. Measurements: 2026-10-13/14, OMEN Windows/Ubuntu WSL2,
CPU0, CPU execution, FP64, six threading environment variables set to one.
This closes out the recent distillation / MSC-d5 investigation. **No recent
candidate established a broad or 1024-shot improvement. No SOTA claim is made.**

This is a **summary archive**, not a raw-run replay bundle. It preserves every
published comparison from four completed analyses, including unsuccessful
candidates, all paired round ratios, available drift/chronology diagnostics,
frozen peer policies, 32 native counter populations and 96 CPU windows.
The original command streams, ELF files, full correctness vectors, raw timing
observations and execution/review closures remain in the local retained archive;
they are not downloadable through this publication. Hashes identify those
previously reviewed originals; hashes alone are not an independent attestation.

## Result and disposition

| Experiment | Completed evidence | Result | Disposition |
| --- | --- | --- | --- |
| Frozen peer comparison | 1344 initial workers; 648 new fixed-policy repeat workers | Rust loses to compiled SymFT at 64/1024 attempted shots; some one-shot cells favor Rust | Preserve both runs separately; no overall superiority |
| Zero-lane mask early return | 24 functional workers + 288 evaluation workers, 12 contrasts | All 12 approximate intervals contain 1 | Park; no merge or repeat to seek significance |
| Packet output mode specialization | 24 functional workers + 288 evaluation workers, 12 contrasts | Two isolated nominal pointwise wins; other 10 contain 1, including all 1024-shot cells | Park; no broad-gain claim or performance merge |
| Two-entry packet transition memo | 50 relevant Rust tests and independent source/committed-head review passed | Native build attempt stopped in host preflight; no Linux candidate binary or timings | Correctness-qualified hypothesis only; do not promote as a speedup |

The production source is unchanged by this publication. The three experimental
branches and all original failure evidence are retained locally. None is merged
on the strength of this report. The bounded closeout does not start another
benchmark sweep or an autonomous optimization loop.

## Frozen peer results

The peer runs used the original finite-attempt raw postselected counts contract:
all raw detectors zero for acceptance, raw observable-zero XOR for logical errors,
without reference normalization. Accepted throughput is distinct from attempted
throughput. The two original fixtures are
[distillation](https://github.com/nzy1997/rust-qec/blob/7223e746c0e85b5b5568f041671bc70b3205c30d/benchmarks/near_clifford/application_counts/fixtures/distillation.stim)
and
[MSC-d5](https://github.com/nzy1997/rust-qec/blob/7223e746c0e85b5b5568f041671bc70b3205c30d/benchmarks/near_clifford/application_counts/fixtures/msc_d5_inject_cultivate_p1e-3.stim).

| Frozen implementation | Revision recorded at measurement |
| --- | --- |
| Rust | `9852a733afbde09bcfd668f0ddbc4675bbdaa753` |
| SymFT | `3f718e9e0c58b277a8fb506b4170863db5c3dbe6` |
| Clifft | `847757e2bc8c4f7439b9e92011550fd61719eb85` |

The initial run contains 666 tuning workers, 30 functional workers and 648
evaluation workers. The repeat uses 18 new process rounds (18..35), the same
18 selected peer policies and 648 workers, with no retuning. Both runs use seven
warm observations of at least 50 ms per process. Warm latency is the process
median of elapsed-ns / calls; paired ratios use matching round/request/role.
Compilation, preparation and first calls are separate from warm latency.
True compiled SymFT execution was checked; unsupported scalar policies are
capability refusals, not performance scores.

Repeat 1024-shot latency, expressed as **Rust latency / SymFT latency**
(larger means Rust is slower):

| Workload | Strict | Fused |
| --- | ---: | ---: |
| Distillation | 2.99x | 3.08x |
| MSC-d5 | 3.08x | 3.18x |

The [initial table](fair-primary.csv) and [repeat table](fair-repeat.csv) contain
all 36 contrasts each, including Clifft and the one-shot results.
Their speedup column has the **opposite orientation to the slowdown table
above: peer latency / Rust latency**, so values above 1 favor Rust.
The JSON files contain every round ratio, all six strict/control drift series
and the selected tuning policies. They preserve the original nominal Bonferroni36
bootstrap labels: 50,000 shared whole-18-round resamples give only a sparse
extreme tail. Calibrated family-wise 95% coverage is **not established**.
Do not pool initial and repeat rounds. Disjoint integer seeds do not prove PRNG
independence. The initial d5/one-shot round56 strict-control ratio of 8.217
remains in the initial drift series; it is not discarded because it did not
recur in the repeat.

The original initial-run hash/parse reads were separate; their historical
non-atomic provenance limitation is retained. The successor repeat verified and
parsed the same captured bytes. That fix does not retrospectively prove the
absence of transient replacement in the initial run.

These are historical, revision-bound results. Rust's history cleanup maps the
recorded `9852a733` to `5c8c7880a4e7fa1d6f11db0b76ede5e78a70f2c0`, and
`74b6e05e` to `32a5cbad4b972207f001a630dec0f3813b743aa4`; original revision
labels remain intact. No measurement is relabeled as current master.
Clifft subsequently changed runtime batching at
`1dc3551dad02f3b098d041d5bdf8067531eaa588`. The old Clifft scores do not
describe that revision or establish leadership over today's implementations.

## Candidate screens

Both screens compare their candidate against exact Rust
`74b6e05ed060f48f3bad2eebe4e0f29ddf3a3ddb`, using the same unchanged
non-marker application probe, CPU0, default 64 MiB cache, one-thread settings,
FP64 and no GPU. Each uses 12 independent process rounds, six requests
(two workloads x 1/64/1024 shots), four roles (baseline/candidate x Strict/Fused)
in a Williams-balanced order, seven >=50 ms observations per process and no
parameter reselection. Each has 24 fixed-8192-attempt functional workers before
288 timing workers. Full measurement vectors/counts agree in 12 functional
pairs; each binary also checks counts against structured records and a
16-word RNG continuation. This is not a cross-binary full-RNG-state proof.

| Candidate | Recorded revision | Evaluation rounds | Complete table |
| --- | --- | --- | --- |
| Zero-mask return | `42770197e0192bfada25f4e5ef5f909c54d10fb8` | 400..411 | [12 contrasts](zero-mask.csv) |
| Output specialization | `ad47858eccef9f2663285c284970daefaf33f7dd` | 600..611 | [12 contrasts](output-specialization.csv) |

Here speedup is **baseline latency / candidate latency**. All 12 contrasts are
retained, with 50,000 shared whole-12-round bootstrap resamples (seed1739).
Intervals are approximate **pointwise** 95% percentile intervals, not calibrated
family coverage. No outlier removal, post-hoc extra rounds, pooling with earlier
candidates or selecting only successful cells was used.

The output-specialization screen's two intervals above 1 are:

| Workload / attempted shots / arithmetic | Speedup | Approximate interval |
| --- | ---: | --- |
| Distillation / 1 / Fused | 1.11593x | [1.03745, 1.19508] |
| MSC-d5 / 64 / Fused | 1.20864x | [1.01343, 1.43546] |

All four 1024-shot intervals contain 1. This is insufficient evidence for the
priority batch-size improvement, overall benefit, equivalence or regression.
Output-specialization chronology/position diagnostics are retained in JSON;
they are descriptive, and are not same-code control roles or a causal drift
correction. Per-process lifecycle rows are omitted from this compact archive.

## What diagnosis established

The separate six-process warm-phase profile on Rust74b6 retained 775 samples,
536 in warm windows. Among those warm leaf locations: packet105,
rotate_coeff71, packet_apply70, cached_rotate48 and replay skip_zero42.
These are flat sample counts, not inclusive CPU time or proof of a cause for
the peer gap. Earlier failed profiles contribute no partial hotspots.

[operation-census.json](operation-census.json) retains all 32 native SmallRng
counter populations: two workloads x Strict/Fused x first0/warm1..7, each1024
attempts, evaluation720 and seed_call0. Large raw bit arrays are omitted.
Strict and Fused counts agree here; arithmetic policies remain separate.

| Warm counts per 1024 attempts | Distillation | MSC-d5 |
| --- | ---: | ---: |
| Rotation calls (mean of seven warm populations) | 3184 | 37880 |
| Aggregate rotation-cache hit fraction | 100% | 82.5901% |
| Cache reservation ledger, bytes | 37864 | 67108792 |
| Scalar coefficient logical input / output, MiB | 0 / 0 | 77.20 / 79.36 |
| Packet typed-tape logical words | 347136 | 3713024 |

First-call rotation misses are 21 for distillation and 7567 for d5. Coefficient
entry extents are not arithmetic operations, measured DRAM traffic or RSS.
Requested RNG API payload is not internal engine draws. The first
LinearCountsPlan build rejects rotation/active projection once for each cell;
empty warm events mean lazy reuse, not repeated rejection or a rank diagnosis.
The internal counts/records and next16 assertions passed; independent review
also reconstructed detector/observable XORs from the full captured measurements.
This does not provide an external independent quantum-state simulation.
Historical producer strings saying "prospective" / "NOT YET VERIFIED" are
retained literally; the separate successful runtime review supplies the bounded
execution evidence.

[cpu-windows.json](cpu-windows.json) is an unchanged copy of the independently
reconstructed pristine CPU diagnostic: 12 new processes at rounds740..742,
12 first and 84 warm windows. Per-process summed warm CPU / wall lies between
0.968317 and 0.996056. One first window has CPU above wall, and d5 Strict742
has 130 involuntary warm context switches; both remain present. RUSAGE_SELF
microseconds are read before MONOTONIC nanoseconds, so boundaries are not
simultaneous. There is no clamping, wall-latency normalization, first/warm
pooling or pooling with instrumented counters. The data support investigating
execution work next, not attributing the old ~3x peer gap to one cause.
Lifetime ru_maxrss cannot establish current/scoped simulator memory advantages.

## Bounded next direction

There is a concrete d5 direction: reduce repeated transition/coefficient work
on persistent rotation-cache misses without hashing/copying whole coefficient
vectors. A two-entry stack-local memo of successful packet transitions is
implemented at local revision `7bd67de524fafb623ffa0f6083b528dea5e3c4f2` and
correctness-reviewed. Its sole native build attempt failed in the host-status
preflight before compilation. **It has no performance result.** A reviewed
CPU-only build successor exists but was not launched when work was paused.

If work resumes on a quiet node, this is the one bounded candidate to measure
before broader changes; retain full functional/RNG checks and require measured
benefit plus independent final-head review/CI before proposing a production
merge. This report does not rerun or enlarge the previous unsuccessful screens.
Distillation's packet/tape path is a separate direction. Larger caches or
coefficient hashing are not justified by these counters; an earlier full-cache
lookup experiment already lost on FULL36.

A new current-peer result additionally requires fresh peer builds, compiled
active-width inspection, separate tuning and frozen evaluation policies.
Clifft's direct API auto policy and Sinter's default batch policy differ; output
record width is not compiled active width. Full36, larger circuits and Tsim
remain outside this two-workload closeout.

## Archive contents and integrity

- `fair-primary.*`, `fair-repeat.*`, `zero-mask.*`, `output-specialization.*`:
  byte-identical original CSVs plus JSON projections retaining all primary
  contrasts/round ratios and available drift/temporal/policy fields.
- `operation-census.json`: all32 counter rows with only `raw_*` bit arrays removed.
- `cpu-windows.json`: all96 numeric windows, unchanged from the independent review.
- `provenance.json`: original analysis/review fingerprints, exact projection
  descriptions and historical source mapping. Full dependency closures remain
  private, so this archive alone cannot re-certify raw execution or recompute
  process medians from the seven original observations.

All new paths are covered by the repository's `ARTIFACTS.sha256`. From the
repository root, verify the publication alone without fetching older artifacts:

```sh
python3 - <<'PY'
from pathlib import Path
import hashlib
prefix = 'benchmarks/near_clifford/results/omen-two-workload-wrapup-2026-10-15/'
for line in Path('ARTIFACTS.sha256').read_text().splitlines():
    expected, name = line.split('  ', 1)
    if name.startswith(prefix):
        assert hashlib.sha256(Path(name).read_bytes()).hexdigest() == expected, name
print('PASS publication checksums')
PY
```
