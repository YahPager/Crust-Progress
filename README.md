<p align="center">
  <img src="assets/branding/crust-logo-transparent 1163x387.png" alt="Crust logo" width="420">
</p>

# Crust Progress

Crust is an experimental native systems language with C-style syntax and `.cru`
source files. Its goal is first-class interoperability with C, C++, and Rust,
with Windows x64 as the initial target.

Maintained by [YahPager](https://github.com/YahPager).

## Current status

**First bounded SDRTW v3 offline framing proof verified on Windows x64.**

The first application proof exercises selected synthetic P25 Phase 2 framing.
Crust owns orchestration, input validation, reset, event routing, and lifecycle,
with C, C++, and Rust integrations and an isolated native framing reference.
Actual Crust application runs passed with both unoptimized and optimized
output, including malformed-input, Unicode-path, native-library lifecycle,
and cleanup checks.

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

The compiler can check, build, and execute Crust programs and projects using
core numeric operations, functions, control flow, and modules. Native execution
and invalid-program rejection have been verified with both unoptimized and
optimized output, including checked arithmetic and diagnostics.

Selected generated interfaces support calls in both directions between Crust
and each of C, C++, and Rust for scalar values, borrowed primitive buffers,
records, and owned resources. All six directions were verified using synthetic
native programs on Windows x64 with both unoptimized and optimized output.

The selected resource checks cover scoped borrowing, ownership, errors,
deterministic cleanup, and explicit unsafe boundaries, including rejection of
invalid operations. These checks establish a limited interface and resource
proof. Foreign implementations still need to honor their declared contracts;
broader language safety, library compatibility, and platform support require
separate verification.

Developer toolchain checks and a separate mixed C/C++/Rust native-toolchain
smoke test are also verified in the Windows development environment.

Broader SDR: The Works v3 functionality and added features remain planned.
The selected proof does not establish a complete application or live receiver.

The full language, broader compatibility, clean-environment packaging, and
broader performance evaluation remain planned. Published performance results
apply to the named workloads and measured boundaries; they do not establish
a general language-wide speed or memory advantage.

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
| Crust checked export | 39.75-39.84 | Not implemented |
| C++ | 183.11-183.30 | 189.16-189.26 |
| Rust | 149.80 | 153.52 |
| Goose | 148.54-148.63 | 153.42 |

This routing test uses each build's recorded settings, including additional
Crust optimizations; its settings are not matched like the kernel table.
No separate C routing control was measured. Scratch results are native
prototypes; the Crust row measures actual generated routing code.

## Follow progress

- [Roadmap](ROADMAP.md): planned milestones and status definitions.
- [Progress journal](PROGRESS.md): dated updates and verified results.

This public repository contains project summaries, reviewed branding, and,
when available, reviewed screenshots and demonstration videos. Compiler source,
detailed specifications, internal development records, and binaries remain private.
No compiler download is available here.

Planned features describe goals. Compatibility and performance claims will
identify what was actually tested and any remaining limitations.
