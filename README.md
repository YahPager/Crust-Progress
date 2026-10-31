<p align="center">
  <img src="assets/branding/crust-logo-transparent 1163x387.png" alt="Crust logo" width="420">
</p>

# Crust Progress

I'm building Crust, an experimental native systems language with C-style syntax
and `.cru` source files, with a focus on interoperability with C, C++, and Rust.
Windows x64 is the supported target.

I'm documenting verified milestones and remaining work publicly here at Crust
Progress. Implementation remains private during development.

**Follow the project:** read the [progress journal](PROGRESS.md) for verified
milestones and the [roadmap](ROADMAP.md) for what's next.

Crust is intended for eventual public use as a general-purpose systems language.
The [growth roadmap](ROADMAP.md#general-purpose-language-growth) now covers
language maturity, reusable libraries, concurrency, developer tools and
independent application demonstrations. The composable-state, generic-abstraction
and library-build subsets are now verified; later additions remain planned. SDRTW
is one future proving ground; its full v3 rebuild stays deferred while Crust
grows and v2e development continues. Public release remains a separate review.

Maintained by [YahPager](https://github.com/YahPager).

## First week CodeGraph

Crust's compiler and build-driver structure during its first week of development,
captured October 29, 2026: **18 source files, 2,689 nodes and 3,978 indexed
relationships**. This compiler-only snapshot excludes the SDRTW proof,
experiments and external test fixtures.

![First-week CodeGraph snapshot of the Crust compiler and build driver](assets/progress/crust-first-week-codegraph-2026-10-29.png)

## Current status

**Crust now supports Windows x64 only.** Linux support has been withdrawn and
removed from the implementation. Earlier Fedora milestones remain historical
results for their recorded revisions. See the [platform update](PROGRESS.md#october-31-2026---windows-only-development).

Selected Windows AOT and optional JIT checks cover private record fields, typed
owning storage, checked views/transfers, reusable buffers/vectors, owned UTF-8
strings, a bounded queue, an ordered map, initial scalar/complex math, typed
formatting and checked endian bytes. Independent models, allocation failures,
ownership rejection and exact native cleanup are covered with unoptimized and
optimized output. Selected C/C++/Rust interfaces work in both directions.

Version-2 host projects retain separate Windows locks and build outputs;
incompatible targets and artifacts reject. Bounded JSON event reading/writing
also passes Windows AOT/JIT checks. Owned files, lossless native paths and
clocks pass selected Windows checks. Synchronous TCP also passes selected
Windows IPv4/IPv6 and failure-path checks; independent application acceptance
remains pending. There is no public
compiler or binary release.

**Reusable packages and Windows libraries are verified on Windows x64.**
Projects share code through local package dependencies with explicit public
items, and build static libraries or DLLs that independent C, C++ and Rust
programs use. Crust programs consume prebuilt C, C++, Rust and Crust
libraries. Those programs pass in AOT and JIT with unoptimized and optimized
output.
See the [milestone](PROGRESS.md#october-29-2026---reusable-packages-and-windows-libraries).

**Reusable generic abstractions are verified on Windows x64.** Selected generic
algorithms and data types now handle primitive, record and owned values, with
static interface constraints. Ownership, cleanup, module visibility and rejection
checks pass in AOT and JIT with unoptimized and optimized output. See the
[milestone](PROGRESS.md#october-29-2026---reusable-generic-abstractions).

**Composable owned state is verified on Windows x64.** Owned records, methods,
tagged variants, optional values and input-tied returned views pass selected
ownership, cleanup and failure checks in both AOT and JIT, with unoptimized and
optimized output. Existing native interfaces remain compatible. See the
[milestone](PROGRESS.md#october-29-2026---composable-owned-state).

**First bounded SDRTW v3 offline framing proof verified on Windows x64.**

**Opt-in JIT execution is also verified on Windows x64.** Existing ahead-of-time
execution remains the default. Selected C/C++/Rust interfaces, checked failures,
resource cleanup and native-library lifecycle checks pass in both modes. The
earlier JIT checkpoint passed 254 tests. See the separate
[whole-process AOT/JIT comparison](JIT-COMPARISON.md) for the earlier measured
results and limits. A later October 28 pass kept three improvements against
the previous Crust compiler: pure JIT programs skip an extra support library,
unlocked C and C++ projects do less repeated driver work, and eligible
widening conversions use the existing checked-sum path. Empty JIT startup and
the largest checked sum were faster than that previous Crust build. See the
[progress journal](PROGRESS.md#october-28-2026---faster-jit-startup-and-a-faster-checked-sum).
These runs do not show Crust matching C.

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

## Follow progress

- [Roadmap](ROADMAP.md): planned milestones and status definitions.
- [Progress journal](PROGRESS.md): dated updates and verified results.

This public repository contains project summaries, reviewed branding, and,
when available, reviewed screenshots and demonstration videos. Compiler source,
detailed specifications, internal development records, and binaries remain private.
No compiler download is available here.

Planned features describe goals. Compatibility and performance claims will
identify what was actually tested and any remaining limitations.
