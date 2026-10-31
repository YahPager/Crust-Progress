# Crust Measurements

These are historical measurements from October 28, 2026, on Windows x64.
Results apply to the named revisions, workloads and measured boundaries.
They do not establish a general speed or memory advantage for Crust.

## Measured comparisons across languages

The October 28 prepared-workload measurements compare **Crust, C, C++, Rust
and Goose** on Windows x64. The Goose control is pinned to v2026.3; newer
releases were not measured. Lower times are better.

The table shows median times at the largest tested size of each workload, in
**microseconds per complete workload**, from the second recursion-update
campaign using the original scheduling protocol:

| Workload | C | C++ | Rust | Crust | Goose |
|---|---:|---:|---:|---:|---:|
| Sum, 1,048,576 elements | 1,266.6 | 1,364.1 | 2,505.4 | 1,558.4 | 3,134.7 |
| Image blur, width 512 | 422.2 | 421.8 | 4,005.0 | 431.4 | 5,141.1 |
| Particles, 32,768 | 866.4 | 866.2 | 1,106.6 | 894.6 | 917.8 |
| Matrix multiplication, width 128 | 223.0 | 225.8 | 250.5 | 243.1 | 955.4 |
| N-Queens, 12 | 11,685.3 | 11,699.6 | 11,181.4 | 10,984.1 | 11,522.1 |
| Fibonacci, 30 | 1,263.7 | 1,267.4 | 2,257.8 | 1,179.4 | 1,428.4 |

All five builds use matched loop-unswitching and alignment settings. These
prepared kernels include their result digest but exclude allocation, setup
and cleanup. Language-specific checks and call boundaries still differ.
Both final campaigns passed 180 cross-language controls. C and Crust run as
adjacent alternating pairs. Only N-Queens meets the strict C target in both
campaigns: its upper 95% time-ratio endpoint is at most 1.00. Fibonacci is
about 12-13% faster than its old compiler path, but lower medians than C do
not confirm parity: its two Crust/C intervals are 0.9105-1.0117 and
0.9182-1.0019. A separate fixed-CPU follow-up also leaves that target open.
The other four C targets remain open. Large-sum timing is variable, so no
precise improvement is claimed there. These are workload
measurements, not an overall ranking or a reproduction of any language's
original benchmark suite. Historical results remain in the progress journal.

A separate **256-frame stereo routing test**, in **nanoseconds per block**,
measured the following medians of batch-average times across two recorded
campaigns. These are not individual-block latency measurements:

| Implementation | Reused buffers | Scoped scratch |
|---|---:|---:|
| Crust checked export | 40.04-40.33 | 48.63-48.93 |
| C++ | 183.11-183.30 | 189.16-189.26 |
| Rust | 149.80 | 153.52 |
| Goose | 148.54-148.63 | 153.42 |

This routing test uses each build's recorded settings, including additional
Crust optimizations; its settings are not matched like the kernel table.
No separate C routing control was measured. The Crust row is an October 28
Crust-only measurement of actual generated code. Its scratch time includes
reset inside the measured call, and prepared reuse remains the default
because scratch was slower on that boundary. The C++, Rust, and Goose rows
are earlier measurements and were not rerun; they are historical comparisons.

## Bounded offline framing comparison

An October 28 measurement on Windows x64 (Intel Core Ultra 7 265K) compared
Crust with a C++ orchestration control doing the same work over the same timed
boundary. Each synthetic stream represents **720 ms of radio data**:

| Feed size | Crust processing time | C++ control doing the same work |
|---|---:|---:|
| 256 dibits | **0.02677 ms/stream** | 0.02472 ms/stream |
| One dibit | **0.54506 ms/stream** | 0.50414 ms/stream |

These are medians of average processing times from nine runs per case, each
with 128 measured streams and eight warmups, rather than worst-case latency.
Crust took about **8% longer** than the C++ control. All **73 native and 146
Crust cases** passed, including invalid-input, reset and cleanup checks.
See the [measurement details and memory results](PROGRESS.md#october-28-2026---sdrtw-offline-framing-times-and-memory).

This is a bounded offline framing proof. It does not establish a Crust-native
P25 decoder, voice or security correctness, live hardware operation, a full
SDRTW v3 receiver rebuild, or host compatibility.

[Project introduction](README.md) | [Progress journal](PROGRESS.md) | [AOT/JIT comparison](JIT-COMPARISON.md)
