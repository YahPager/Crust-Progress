# Crust Progress Journal

## October 31, 2026 - Files, paths and clocks verified on Windows

Owned files, lossless native paths and clocks now pass selected Windows x64 checks with unoptimized and optimized AOT/JIT execution. Tests cover Unicode and non-Unicode native filenames, explicit open modes, partial and interrupted transfers, EOF, failed opens, native error information, monotonic time and wall timestamps. Allocation failures and ownership rejection checks verify exact cleanup.

Synchronous TCP and independent application acceptance remain the next Phase 5 work. Linux support remains withdrawn and concurrency remains later work. Implementation, detailed evidence and binaries stay private; there is no public compiler release.

## October 30, 2026 - Bounded JSON verified on Windows

The source library now includes bounded JSON event reading and writing on Windows x64. Unoptimized and optimized AOT/JIT checks cover independent token and output values, Unicode escapes, malformed numbers and grammar, truncation, nesting/output limits, allocation failures and exact cleanup. Rejected writer operations preserve existing output. Privacy and borrowed-view checks reject invalid use.

The full Windows regression and framing correctness gates pass. Files, paths, clocks, synchronous TCP and two independent application checks are the next ordered work in Phase 5. Linux support remains withdrawn; concurrency remains later work. Implementation and detailed evidence stay private, with no public source or binary release.

## October 31, 2026 - Windows-only development

Crust now supports Windows x64 only. Linux support and its development setup tools have been removed. Earlier Fedora entries remain historical evidence for their recorded revisions; they do not describe current platform support.

The Windows compiler, optional JIT and existing source-library work are retained. Windows regression checks cover the implemented library through initial math, formatting and endian bytes, with selected C/C++/Rust calls in both directions, allocation failures and exact cleanup. The framing correctness gate also passes.

JSON, files/paths/clocks, synchronous TCP and independent application acceptance remain later work. This platform decision does not cancel the remaining Windows roadmap or announce a public release. Implementation, detailed evidence and binaries stay private.

## October 30, 2026 - Initial math, formatting and byte facilities verified on Windows

The source library now includes initial scalar and complex math, typed number/boolean formatting, exact hexadecimal float text and checked endian byte operations. Selected Windows x64 checks pass with unoptimized and optimized output in AOT and optional JIT execution. Independent vectors cover numeric edge cases, signed zero, format round trips, byte order, truncation and overflow.

Concrete C/C++/Rust interfaces pass in both directions. Independent native parsing checks the float text, while allocation-failure tests verify cleanup of partial results and prepared byte operations perform no further allocation. The complete Windows regression and framing correctness gates pass. No performance improvement or complete numerical-library coverage is claimed.

Native Fedora execution of these additions remains pending. Cross-platform standard-library acceptance stays open. This implementation run stops here; JSON, files, clocks, synchronous TCP and concurrency remain later work. Source, detailed evidence and binaries remain private, with no public release announced.

## October 30, 2026 - Queue and ordered map verified on Windows

A bounded single-thread queue and ordered generic map now pass Windows x64 checks with unoptimized and optimized output in AOT and optional JIT execution. Checks cover queue wraparound and full/empty behavior, static integer and owned-string key ordering, insertion, replacement, removal and borrowed views.

Independent queue/map models agree with selected operation traces. Allocation failures preserve existing entries and committed capacity, partial construction cleans up exactly, and C/C++/Rust resource counters verify ownership through the selected success and failure paths. The full Windows regression and bounded framing correctness gates pass.

Native Fedora verification of these additions remains pending, so cross-platform acceptance stays open. Math, formatting, checked byte operations and further facilities remain later work at this checkpoint. Implementation, detailed evidence and binaries stay private; no concurrency or public release is claimed.

## October 30, 2026 - Owned UTF-8 strings verified on Windows

Owned UTF-8 strings now pass Windows x64 checks with unoptimized and optimized output in AOT and optional JIT execution. Construction and byte append validate text, checked slicing respects Unicode boundaries, and borrowed views keep ownership rules intact. Independent Unicode and ordering checks cover malformed input, multibyte boundaries, empty ranges and selected overflow cases.

Failed append and allocation preserve existing valid text, and allocation/release checks pass. Private representation access, mutable text views and escaping or conflicting borrows reject. The full Windows compiler regression gate passes.

Native Fedora verification of these additions remains pending, so cross-platform acceptance stays open. Queues, maps, math, formatting and further standard facilities remain later work at this checkpoint. Implementation, detailed evidence and binaries remain private; no public release or new performance result is claimed.

## October 30, 2026 - Reusable buffers and vectors verified on Windows

The first reusable byte buffers and generic vectors now pass Windows x64 checks with unoptimized and optimized output in AOT and optional JIT execution. Reservation is explicit; bounded operations do not grow silently. Checks cover allocation failures preserving existing contents, primitive and aggregate elements, native owners, nested containers, borrowed views and ownership rejection.

Independent operation traces and C/C++/Rust resource counters verify selected results and exact cleanup. Source-package consumers, relocated locked inputs, the full Windows compiler regression suite and bounded framing correctness gate also pass.

Native Fedora verification of the new collections remains pending, so cross-platform acceptance is open. UTF-8 strings, queues, maps, math, formatting and further standard facilities remain later work at this checkpoint. Implementation, detailed evidence and binaries remain private; no public release or new performance result is claimed.

## October 30, 2026 - Checked storage views verified on Windows

Windows x64 checks now cover owner-tied shared and exclusive element views, checked replacement, removal and ownership transfer between typed storage owners. Borrowing checks reject escaping views, conflicting access and owner movement or destruction while borrowed. Independent C, C++ and Rust counters verify exact cleanup through the selected ownership operations.

These checks pass with unoptimized and optimized output in AOT and optional JIT execution. The full Windows compiler regression and bounded framing correctness gates also pass. Native Fedora execution of these additions remains pending, so cross-platform acceptance remains open. Reusable collections are the next step; implementation and detailed evidence remain private.

## October 30, 2026 - Typed owning storage verified on Windows

Typed owning storage now passes Windows x64 acceptance with unoptimized and optimized output in AOT and optional JIT execution. Checks cover primitive values, records, variants, nested storage and move-only C/C++/Rust resources. Allocation failures, capacity overflow, full insertion and partial construction preserve the tested ownership rules; independent counters verify exact cleanup.

Source-package use, relocated locked execution and compiler rejection checks also pass. The full Windows compiler regression and bounded framing correctness gates pass. Together with the recorded native Fedora results, this verifies the selected typed-storage acceptance on both systems.

This delivery stops after typed owning storage. Checked element views, transfers, collections and later standard-library facilities remain planned. Implementation, detailed evidence and binaries remain private; no public release or new performance result is claimed.

## October 30, 2026 - Encapsulated types verified on Windows

Private record fields and encapsulated public types now pass Windows x64 checks with unoptimized and optimized output in AOT and optional JIT execution. Independent package consumers can use public operations while unauthorized state access and construction reject. Generic types, borrowed views and hidden C/C++/Rust native owners preserve ownership and exact cleanup checks.

The full Windows compiler regression and bounded framing gates pass. Together with the recorded Fedora results, this verifies the selected private-field acceptance on both systems. Collections and later standard-library facilities remain planned; implementation and detailed evidence stay private.

## October 30, 2026 - Windows JIT compatibility revalidated

The current compiler passes Windows x64 JIT regression checks with unoptimized and optimized output after the Linux JIT port. Selected checks cover native interfaces in all six C/C++/Rust directions, errors, resource cleanup, exceptions and panics, runtime locks, arguments, timeouts and library lifecycle. The full Windows regression and framing correctness gates pass. Ahead-of-time compilation remains the default.

Existing Fedora JIT results remain separate execution evidence. Implementation and detailed results stay private; public release remains later work.

## October 30, 2026 - Windows native compatibility revalidated

The current compiler passes Windows x64 native-build regression checks after the Linux work. Selected C, C++ and Rust interfaces run in all six directions, including borrowed buffers, errors and resource cleanup. Source dependencies, independent native library consumers, locked inputs, relocation and failed-build preservation also pass with unoptimized and optimized output.

The Windows compiler regression suite and bounded framing correctness gate pass. Existing Fedora execution evidence remains separate. Implementation and detailed evidence stay private; broader standard-library acceptance and public release remain later work.

## October 30, 2026 - Typed owning storage verified

**Verified on Fedora KDE 44 x86_64:** typed storage now owns allocated space, tracks initialized elements and releases them automatically. Checks cover primitive values, records, variants and move-only native resources from C, C++ and Rust, with unoptimized and optimized output in AOT and optional JIT execution.

Selected failures include overflowing capacity, rejected allocations, full storage and interrupted construction. Independent native counters verify that live resources are destroyed exactly once and existing values survive allocation failure. Ownership rejection, source-package use and relocated locked execution also pass. The Linux compiler and native-interface regression gate passes.

Checked element views, transfers, collections and the remaining standard library are later work. This Linux session does not revalidate Windows execution or establish a new performance result. Implementation, detailed evidence and binaries remain private; public release remains a separate decision.

## October 30, 2026 - Encapsulated public types verified

**Verified on Fedora KDE 44 x86_64:** public Crust types can now keep selected
record fields private to their defining module. Independent package consumers
use public operations while direct field access and construction attempts are
rejected. Existing unmarked fields retain their behavior.

Checks cover generic specialization, public interface boundaries and borrowed
views. Public types can hide move-only native owners from C, C++ and Rust;
independent counters verify cleanup through replacement, moves, nested values,
errors and interrupted construction. These checks pass with unoptimized and
optimized output, ahead of time and through the optional Linux JIT.

The existing Linux compiler and native-interface regression gate also passes.
Windows execution is not revalidated by this Linux session. Reusable storage,
collections and the remaining standard-library work are still planned.
Implementation, detailed evidence and binaries stay private; public release
remains a separate decision. No new performance result is claimed.

## October 30, 2026 - Linux JIT execution verified

**Verified on Fedora KDE 44 x86_64:** Crust programs and declared tests now run
through the optional in-memory JIT with both unoptimized and optimized output.
Ahead-of-time compilation remains the default.

Selected C, C++ and Rust interfaces pass in all six call directions, including
scalar and borrowed-buffer boundaries, explicit errors and exact resource
cleanup. Checks also cover native exceptions and panics, termination for invalid
destructors, argument forwarding, nested invocation and library teardown.

Locked inputs, moved package layouts and separately built libraries work with
the Linux JIT. Missing or incompatible runtimes, missing libraries, unresolved
symbols and worker timeouts fail explicitly. The existing Linux native-build
and numeric regression gate also passes.

The reusable standard library, Linux framing, broader platform acceptance,
packaging and public release remain later work. Windows regression results
remain recorded at their earlier revisions; this Linux session does not claim
a new Windows execution run. Source, detailed evidence and binaries stay
private. No new performance result is claimed.

## October 30, 2026 - Linux native acceptance completed

**Verified on Fedora KDE 44 x86_64:** the remaining selected native-interface
checks now pass with unoptimized and optimized output. Crust calls C, C++ and
Rust, and each language calls Crust, exercising scalar boundaries, borrowed
numeric and Boolean buffers, errors and exact resource destruction checks.

The native gate also passes for executable, static and shared library outputs,
local dependencies, locked inputs, relocated layouts, rejected inputs and
process cleanup. This completes the scoped Linux native-build acceptance step.
The compiler implementation is unchanged by this coverage closure; earlier
Windows regression results remain recorded separately.

Linux JIT and the reusable standard library remain later work. Framing on Linux,
broader platform acceptance, packaging and public release remain unverified.
Source, detailed evidence and binaries stay private. No new performance result
is claimed.

## October 30, 2026 - Fedora native execution checkpoint

**Verified on native Fedora KDE 44 x86_64:** selected Crust programs and
static/shared libraries build and execute with unoptimized and optimized
output. Independent C, C++ and Rust programs call Crust, and Crust calls each
language. The six call directions execute selected scalar, record and resource
interfaces. Separate checks cover explicit errors, ownership and resource
cleanup; this does not complete the full interface acceptance matrix.

Local source dependencies and separately built libraries work through locked
inputs and relocated package layouts. Checks reject incompatible, changed or
missing inputs while preserving earlier successful outputs. Process timeout
and descendant cleanup, executable permissions and missing-library failures
are exercised on the actual Linux host.

The pinned LLVM runtime also passes its prerequisite loading and small
execution check. This does not implement or verify the Crust Linux JIT.
The same source passes the Windows regression suite, including existing
native/JIT interoperability, and the framing correctness gate.

The native-build step remains open for additional interface and cleanup
verification identified during review. Linux JIT, the reusable standard library
and its independent application acceptance remain later work. Implementation
and detailed evidence stay private. No new performance result or public
release is claimed.

## October 29, 2026 - Linux native preparation

**Implemented for acceptance:** a Linux native build path and a terminal
runner for the designated Fedora KDE 44 x86_64 host. This is preparation;
Linux support has not passed execution acceptance.

**Verified on Windows x64:** the current compiler regression suite passes,
including existing C/C++/Rust native interoperability and optional JIT checks.
The pinned compiler also produces Linux object files from selected Crust
programs with unoptimized and optimized output. Linux target compilation and
lint checks pass. These checks do not execute Linux programs.

**Pending:** the Fedora installation, exact native prerequisite checks and
real Linux execution, including linking/loading, cleanup, relocation and all
six applicable C/C++/Rust call directions. Linux JIT remains a later step.
The Linux native step and the full standard-library phase remain open.

Implementation, detailed evidence and binaries stay private. No new timing
result, public release or completed Linux milestone is claimed.

## October 29, 2026 - Portable target foundation

**Verified on Windows x64:** opt-in portable projects select a concrete host
target and keep their locks and build outputs separate from other targets.
Synthetic programs pass with unoptimized and optimized output, ahead of time
and through the optional JIT. Relocated projects still run with locked inputs.
Static and shared library consumers pass; incompatible target metadata and
locks are rejected while previous outputs remain intact. Existing Windows
projects retain their behavior.

**Planned:** native builds and JIT execution on Fedora KDE 44 x86_64, followed
by reusable collections, Unicode text, formatting, bounded JSON, files,
clocks and synchronous TCP. Acceptance will use independent file-processing
and loopback-network programs. The Fedora execution environment is pending;
Linux execution and the standard library are not verified.

This is the platform-contract step of the next growth phase. The full phase,
concurrency, public release and packaging remain unfinished. Implementation
stays private. No new performance result is claimed.

## October 29, 2026 - Reusable packages and Windows libraries

**Verified on Windows x64:** Crust code can now be shared between independent
projects. Projects declare local package dependencies, which resolve once
across shared and diamond-shaped graphs. Only items marked public cross
package boundaries. Library packages build without an entry point, either
as static libraries or as DLLs with import libraries. Each library ships with
a generated C header and checked build metadata.

Independent C, C++ and Rust programs link these libraries and call their
exported functions. Crust programs consume libraries built by Crust, C, C++
and Rust toolchains, and dependency packages may bring their own native code.
These Crust programs pass ahead of time and through the optional JIT, with
both unoptimized and optimized output; building a library itself remains
ahead of time. Synthetic programs check successful calls,
failures and exact resource cleanup. Locked builds pin dependencies with
relocatable paths and survive moving a whole project layout.

Dependency cycles, conflicting package identities, private access, changed or
missing inputs and incompatible library metadata are rejected. Rejected builds
leave previous outputs untouched. Required library DLLs are staged with the
application and never loaded from PATH or the current directory. The
compiler suite passes 250 tests, and the existing offline framing correctness
checks also pass.

This completes the library-build phase of the language-growth roadmap.
Standard facilities, concurrency and broader developer tools remain planned.
The full SDRTW v3 rebuild stays deferred. Implementation remains private;
public release and packaging require separate review. No new performance
result is claimed.

## October 29, 2026 - Reusable generic abstractions

**Verified on Windows x64:** selected generic functions and data types reuse
algorithms and containers across primitive values, records and owned state.
Static interface constraints reject unsupported type arguments.

Synthetic programs check distinct and repeated instances, cross-module calls,
ownership transfers, exact cleanup and recoverable failures. The new runtime
scenarios pass ahead of time and through the optional JIT, with both unoptimized
and optimized output. Invalid ownership, unmet constraints and visibility errors
are rejected with source diagnostics. The compiler suite passes 240 tests.

The existing C/C++/Rust interface contract is preserved. Compatible wrappers
using generic code internally pass all six call directions. Generic data types
remain internal rather than new native interface types. The existing offline
framing correctness checks also pass.

This completes the reusable-abstraction phase of the language-growth roadmap.
Reusable library builds, standard facilities, concurrency and broader developer
tools remain planned. The full SDRTW v3 rebuild stays deferred. Implementation
remains private; public release and packaging require separate review. No new
performance result is claimed.

## October 29, 2026 - Composable owned state

**Verified on Windows x64:** Crust can now compose owned resources into
application records, use methods, represent state with tagged variants and
optional values, and return views tied to an input's lifetime.

Synthetic programs check complete ownership transfers, replacement, exact
cleanup order, recoverable failures and invalid-program rejection. The new
runtime cases pass with unoptimized and optimized output, both ahead of time
and through the optional JIT. A multi-module state example combines the new
capabilities. Source-level public calls work without creating native exports.

The existing C/C++/Rust interface contract is preserved. All six call
directions pass, including compatible wrappers that use the new owned state
internally. Richer owned state and returned views remain internal language
types rather than new native interface types. The existing offline framing
correctness checks also pass.

This completes the composable-state phase of the language-growth roadmap.
Generics, reusable library builds, standard facilities, concurrency and broader
developer tools remain planned. The full SDRTW v3 rebuild stays deferred.
Implementation remains private; public release and packaging require separate
review. No new performance result is claimed.

## October 29, 2026 - Goose-suite comparison scope

**Planned:** A whole-process comparison of the published Goose benchmark suite
is now scoped. It will cover the upstream C++ and Rust variants and
independent C and Crust counterparts. Those programs, the runner, and the
measurements are not done.

Published Goose timings remain results from another machine. They are not a
same-machine language ranking. Earlier measurements in this journal are
unchanged. Implementation stays private.

## October 28, 2026 - General-purpose language growth roadmap

**Planned direction recorded:** Crust is being developed for eventual public
use as a general-purpose native systems language. Its growth roadmap now covers
composable data, reusable abstractions and libraries, concurrency, developer
tools, documentation and independent application demonstrations.

This milestone establishes the roadmap and acceptance expectations. It does
not implement or verify new language features. Existing compiler, interface
and performance results retain their previously stated scope and limitations.

SDRTW is one future proving ground. Its full v3 build remains deferred while
Crust grows and v2e development continues. General language readiness will also
be tested through a CLI tool, a small network service and a synthetic streaming
program. Those demonstrations are planned.

Implementation remains private. Public release, licensing and packaging remain
separate decisions. See the [growth roadmap](ROADMAP.md#general-purpose-language-growth).

## October 28, 2026 - Faster JIT startup and a faster checked sum

**Verified:** three compiler changes, each kept only after it beat the previous
Crust build on Windows x64 (Intel Core Ultra 7 265K). Safety checks, the
workloads, and the timing boundaries stayed the same. The compiler suite
passes 192 tests, with formatting and lint checks.

Two independent campaigns used two warmup pairs and nine measured alternating
pairs. The ratio is the new compiler divided by the previous one. A change
stayed only when its median improved and the upper 95% endpoint stayed below
1 in both campaigns.

| Change | Campaign 1 | 95% interval | Campaign 2 | 95% interval |
|---|---:|---|---:|---|
| Empty pure-Crust JIT program | 0.551 | 0.543-0.576 | 0.558 | 0.536-0.576 |
| Small C project, JIT | 0.747 | 0.708-0.769 | 0.754 | 0.746-0.763 |
| Largest checked sum, ahead of time | 0.791 | 0.751-0.825 | 0.804 | 0.780-0.861 |

The empty JIT program still includes source checking and optimization. In two
later full comparisons its best times were 144 ms and 143 ms, beside prebuilt
empty programs near 13 ms. The largest sum's ahead-of-time best times were
527 ms and 534 ms, beside C at 522 ms and 526 ms. Those readings do not
establish a match with C. The sum checksum was unchanged.

Blur and particle controls showed no repeatable slowdown. Blur's small change
was not a target of this pass. Programs that call native libraries, and
programs that export functions, still build their support library. Matching C
across the published workloads remains open. Implementation and detailed
evidence remain private.

## October 28, 2026 - Checked scratch storage and lifecycle

**Verified:** Crust can acquire, zero, use, and reset temporary scratch storage
over caller-provided numeric buffers. Invalid sizes, alignments, and capacity
failures are rejected before any write or growth. The compiler suite passes
186 tests, with formatting and lint checks.

Two Crust-only routing campaigns on Windows x64 (Intel Core Ultra 7 265K),
nine repetitions each, measured 256-frame stereo blocks. Medians of
batch-average times were **40.33 and 40.04 ns/block** for prepared reuse, and
**48.63 and 48.93 ns/block** for scratch. Each campaign passed 120 checksum
controls, and steady processing made no allocation requests. Scratch's
measured call includes its reset. Prepared reuse remains the default because
scratch was slower on this boundary.

A separate lifecycle measurement ran both strategies at 1, 16, and 64 MiB
bursts, with retain and release, across three cycles. Two campaigns of 108
processes each passed output, alignment, and exact final-cleanup checks.
At 64 MiB, cold initialization was about 13.3-13.6 ms for both strategies.
Keeping the burst lowered the next initialization to about 4.1-4.2 ms.
Releasing it took about 1.8-2.0 ms and returned requested memory to the small
prepared footprint, then to zero at final cleanup. Processing a 64 MiB burst
was about 4.2-4.9 ms for both strategies. Reset medians were 0 ns and 100 ns,
and the largest observed reset sample was 1,000 ns.

The C++, Rust, and Goose figures in earlier entries were not remeasured and
remain historical. These results cover one machine, one block size, and the
checked call boundary. They do not establish a language-wide ranking, a
real-time bound, or a general allocator. Implementation and detailed evidence
remain private.

## October 28, 2026 - Opt-in JIT and whole-process comparisons

**Verified:** optional Windows x64 JIT execution for Crust programs and tests,
with AOT retained as the default. Selected interfaces pass in all six directions
between Crust and C/C++/Rust, including checked failures, errors, cleanup,
exceptions/panics and native-library lifecycle checks. All 180 compiler tests
pass with formatting and lint checks.

Two complete campaigns cover sum, flat blur and scalar f32 particles at all nine
selected published sizes. Each retains 250 process samples, including 100
warmups and 150 timed measurements, and passes 30 independent full-output
controls. Every timed application checksum passes; no sample was dropped.

The [complete public comparison](JIT-COMPARISON.md) includes fresh C/C++/Rust and
Crust AOT/JIT times, timing ranges, startup floors, separate build costs and
separate process-memory peaks. Goose's October 16 published values remain
unchanged and are labeled as historical results from a different machine.

JIT compilation and startup dominate the small cases, and it is slower than
the fresh prebuilt modes in these runs. Crust AOT has workload-specific wins
and losses; large-sum and particle times vary between campaigns. Three timed
runs per cell do not establish statistical superiority or an overall language
ranking. The full published workload suite, broader platforms, clean-machine
packaging and the full SDRTW receiver remain unverified.

## October 28, 2026 - Checked recursion: lower times, C target still open

**Verified:** a compiler optimization for eligible recursive functions keeps
checked arithmetic and failure order while reducing Fibonacci n=30 by about
12-13% against the previous compiler path. Benchmark inputs, native controls,
compiler settings and timing boundaries are unchanged. All 161 compiler tests
pass, including 164 new differential recursion cases with both unoptimized
and optimized output. Routing and the offline SDRTW framing checks pass.

Two complete campaigns retain all five languages, sizes and profiles, passing
180 cross-language controls each. Fibonacci times are in microseconds:

| Run | Crust | C | Paired Crust/C ratio | 95% interval |
|---|---:|---:|---:|---|
| Fresh previous compiler | 1,349.6 | 1,269.0 | 1.0630 | 1.0464-1.1286 |
| Updated compiler, campaign 1 | 1,177.4 | 1,266.0 | 0.9302 | 0.9105-1.0117 |
| Updated compiler, campaign 2 | 1,179.4 | 1,263.7 | 0.9380 | 0.9182-1.0019 |

The Crust medians are lower than C, but both intervals cross 1. **Strict C
parity is unconfirmed.** No sample was dropped. The median paired ratio need
not equal the ratio of the separate time medians.

A separate follow-up pinned every implementation to logical CPU 0 on the
same Windows x64 Intel Core Ultra 7 265K. Under that setting, the previous
compiler measured 1,357.9 microseconds. Two complete updated-compiler
campaigns measured 1,184.2 and 1,186.0, versus C's 1,275.5 and 1,277.9.
Their paired intervals were 0.8758-0.9533 and 0.9033-1.0016. The second
still crosses 1; pinning does not eliminate timing variation or close the
target. These results are kept separate from the original protocol above.

Only N-Queens meets the largest-size C target twice in each protocol. Sum,
blur, particles and matrix multiplication remain open too. The
[five-language comparison table](README.md#measured-comparisons-across-languages)
shows the second original-protocol campaign. These prepared-kernel results
exclude setup and cleanup; they do not establish a language-wide ranking.
Smaller N-Queens times varied; an immediate old/new paired check did not
confirm the apparent slowdown. No blanket absence of regressions is claimed.
Implementation and detailed development evidence remain private.

## October 28, 2026 - C comparison, phase 2

**Verified:** removing redundant work from checked signed-64-bit conversions
improves the largest particle workload to about 900/899 microseconds in two
full campaigns, from about 914/915 in phase 1. Inputs, C controls, build flags
and Crust's safety rules are unchanged. Both campaigns passed 180 cross-language
controls; all 159 root tests, including boundary and failure-order checks, pass.

The [comparison tables](README.md#measured-comparisons-across-languages)
now show the second final campaign for C, C++, Rust, Crust and Goose. Only
N-Queens meets the strict C target in both campaigns. Blur remains
inconclusive; sum, particles, matrix multiplication and Fibonacci remain
slower than C. Largest-sum timings are variable. No outlier was removed,
and the complete six-workload C target remains open.

These results cover prepared kernels with setup and cleanup outside the clock.
They do not establish a general language ranking or whole-application result.
No new public interface, allocator, CPU requirement or archive release is added.

## October 28, 2026 - C comparison, phase 1

**Verified:** the prepared-workload runner now measures C and Crust as
adjacent pairs, alternating order, while keeping the C++, Rust and Goose
controls. Two full campaigns each passed 180 cross-language controls.
N-Queens is the only largest-size case whose paired intervals favour Crust
in both campaigns; the other five remain slower than C.

A compiler change preserves checked arithmetic while reducing the medium
65,536-element sum from about 55.7 to 54 microseconds. Largest-sum timing
remains variable, so no precise improvement is claimed there. The expanded
499-case differential check, small-counter regression and all 157 root tests
passed, as did routing
and the SDRTW framing checks. These are existing prepared workloads, not a
general language ranking. The six-workload C target remains open.

## October 28, 2026 - Framing proof closes most of its gap to C++

**Implemented:**
- The compiler now writes a record returned by a native library straight
  into the variable that receives it, instead of copying it.
- It marks error branches as rare, so the optimizer treats the main
  processing loop as the hot path.
- It reuses one error buffer per function where that is safe.

The benchmark now runs the Crust framing program and a matched C++ program
doing the same work side by side, alternating which runs first.

**Verified:** on Windows x64, two independent campaigns compared the two
programs with nine side-by-side pairs per feed size. Each run processes 128
measured streams of 4,320 dibits after 8 warmup streams.

| Feed size | Crust before | Crust after | C++ | After, Crust/C++ |
|---|---:|---:|---:|---:|
| 1 dibit | 539.5 µs/stream | 506.8-507.5 µs | 502.7-506.4 µs | 1.000-1.010 |
| 256 dibits | 26.9 µs/stream | 25.2-25.3 µs | 24.5-24.7 µs | 1.027-1.029 |

All framing correctness, reset and cleanup checks, the 156 compiler tests and
the interoperability suites passed. Allocations and memory matched the C++
program, and other benchmarks showed no slowdown.

**Limits and remaining work:** the goal of matching or beating C++ is not yet
met:
- One-dibit feeds are within about 1%, a statistical tie in one campaign.
- 256-dibit feeds are still about 3% slower. The C++ compiler processes one
  input check 16 bytes at a time, while Crust checks it byte by byte; the
  reason is still under investigation.

## October 28, 2026 - Measured comparisons across languages

The public [comparison tables](README.md#measured-comparisons-across-languages)
now show the recorded Crust, C, C++, Rust and Goose measurements together.
They cover six prepared workloads and the separate audio-routing test, with
units, build-setting differences and unmeasured cases stated explicitly.

**Verified:** the prepared-workload campaigns each passed 180 cross-language
controls. Results show strengths and remaining gaps across the implementations;
no overall language ranking is claimed. These tables publish existing
measurements, not a new optimization or benchmark run. Memory-lifecycle
prototypes and the SDRTW framing measurements remain separate results below.

## October 28, 2026 - SDRTW offline framing times and memory

**Verified:** the bounded SDRTW v3 offline framing component passed **73
independent native cases and 146 actual Crust cases** at optimization levels
0 and 2, including invalid-input, reset and cleanup checks. Measurements ran
on Windows x64 with an Intel Core Ultra 7 265K using synthetic input.

Each stream contains 4,320 dibits, representing **720 ms of radio data**.
The table reports medians of average processing times from nine process runs
per case, with 128 measured streams and eight warmups in each run:

| Feed size | Crust processing time | C++ control doing the same work |
|---|---:|---:|
| 256 dibits | **0.02677 ms/stream** | 0.02472 ms/stream |
| One dibit | **0.54506 ms/stream** | 0.50414 ms/stream |

The C++ orchestration control uses the same work and timed boundary. This is
not a claim of identical compiler settings. Crust took about **8% longer**
in this measurement. These averages are not worst-case or live-radio latency.

With 256-dibit feeds, median Crust **private-memory snapshots** were
**1.051 MiB ready, 1.063 MiB after processing and 1.051 MiB after cleanup**.
These are process snapshots, not exact live-allocation counts or a claim of
returning all memory to the pre-setup footprint. The Rust collector recorded
**zero processing allocations**. The native decoder allocated separately;
its allocations were released during cleanup, and all lifecycle checks passed.

**Limits and remaining work:** this demonstrates an offline framing component
with synthetic data. Full receiver functionality, live-radio operation and
broader compatibility remain pending. Source, internal evidence and binaries
remain private.

## October 28, 2026 - Memory strategy chosen from full-lifecycle measurements

**Verified:** on Windows x64, native Rust, C++ and Goose prototypes were
measured over the whole life of an audio workload. Each run prepares its
buffers, handles temporary bursts of 1, 16 or 64 MiB followed by ordinary
256-frame stereo blocks, and releases everything. Two independent campaigns
of 324 runs each checked:
- every output;
- 64-byte alignment;
- zero ordinary-processing allocations in the instrumented Rust/C++ controls;
- where measurable, that memory returns exactly to its starting level.

**Decided:**
- Caller-prepared buffers stay the default. Temporary scoped scratch
  storage was 1-5% slower in every implementation and offered no benefit, so
  no arena feature is added to Crust.
- Large bursts are a declared tradeoff. Keeping their memory makes repeated
  bursts roughly 3-9 times cheaper to set up but leaves it in use; releasing
  it returns the process to its small starting footprint at a small,
  measured cost.
- The pinned Goose release keeps its peak memory either way. Newer Goose
  versions were not tested.

**Limits and remaining work:** these are native prototypes rather than
Crust-generated code; Crust's own routing path was re-measured separately
and is unchanged. Some allocation counts in the Goose control are not
observable; Goose allocation counts remain unknown. Other routing layouts
and block sizes remain to be measured.

## October 28, 2026 - Compiler optimizations checked against safe references

**Verified:** the recent loop and recursion optimizations are now checked
against ordinary, fully checked versions of the same code. A generated test
runs 371 fixed cases at two optimization levels. They include empty and
single-step loops, block-size boundaries, values at numeric limits, and runs
where two different errors compete. For every case, the optimized code
matches the checked version in:
- its result;
- the data it wrote before any error;
- which error it reported first;
- where in the source that error occurred.

Two deliberately introduced compiler bugs were both caught. The full compiler
suite (155 tests), the interoperability suites, the framing fixtures and
fresh performance campaigns all passed. No speed regression was found.

**Remaining work:** the next phase measures memory use over the full
lifecycle, including preparation, temporary bursts, reset and release.

## October 28, 2026 - Public-readiness checkpoint

**Planned:** ZIP/prerelease packaging is deferred while development continues.
Around 75% completion of the agreed roadmap, we will review readiness and
decide what to open to the public. This sets a future review point, not a
current completion estimate or an automatic publication date. Implementation
remains private, with reviewed progress shared here.
Sponsorship could bring the review forward. In the meantime, we will show
verified capabilities through reviewed progress updates and demos. Any broader
access will have an agreed scope before publication.

## October 28, 2026 - Checked loops close most of the gap to C

**Implemented:** for simple counting loops, the compiler now checks once,
before the loop starts, whether any array index could go out of range on any
iteration. If none can, it runs a copy of the loop without per-iteration index
checks; otherwise it runs the fully checked loop. Overflow-checked integer
totals are now added in blocks with vector instructions. A block whose
partial sums could overflow is redone with ordinary checked additions. Error
locations, order and messages are unchanged.

**Verified:** on Windows x64, two independent prepared-kernel campaigns each
passed 180 cross-language controls.
- **Blur, width 512:** about 7.7 times faster, within 3% of native C. Crust
  now uses about 8% of the Goose control's time.
- **Sum, 1,048,576 elements:** about 30% faster, about half the Goose
  control's time.
- **Other workloads:** no regressions.
- **Other checks:** compiler tests covering both the fast and the fully
  checked paths, routing and the framing fixtures all passed.

**Limits and remaining work:** large sums remain slower than native C, which
performs no overflow checks. Loops with more complex shapes still use
per-iteration checks. These prepared kernels are not a language-wide ranking.

## October 28, 2026 - Loop alignment removes code-placement slowdowns

**Implemented:** optimized Crust builds now start loops on 64-byte
boundaries. A loop's speed then no longer depends on the size of the code in
front of it. The comparison suite's matched profile gives C, C++, Rust and
Goose the same setting.

**Verified:** the Fibonacci change made earlier code larger, and N-Queens and
a mid-size particles run slowed by 2-7% even though their own compiled code
had not changed. On Windows x64, two independent campaigns with 180 passing
cross-language controls each brought both back to their earlier times. With
the setting matched, Crust used about 4% less time than the Goose control for
N-Queens at 12 queens, and Fibonacci stayed about 6% faster. Routing, the
compiler tests and the framing fixtures passed.

**Limits and remaining work:** framing at single-dibit feeds measured slightly
slower in two runs, though the fastest runs were unchanged. That is not yet
confirmed either way. These prepared kernels are not a language-wide ranking.

## October 28, 2026 - Recursive Fibonacci now faster than the Goose control

**Implemented:** when a Crust function calls itself, the compiler now checks
the function's simple base cases at the call site and skips calls that would
return immediately. Integer overflow and conversion checks are unchanged.

**Verified:** on Windows x64, two independent campaigns of the prepared-kernel
suite each passed 180 cross-language controls. With loop unswitching matched,
Crust used about 7% less time than the Goose control for Fibonacci at n = 30.
Every 95% interval favoured Crust at all three sizes, in both build profiles
and both campaigns. Before this change, Crust took about 56% more time. All
151 compiler tests and the framing fixtures passed, and the routing build is
unchanged.

**Limits and remaining work:** native C and C++ remain faster on this
workload. N-Queens' earlier 3% Crust advantage is now inconclusive. Its
compiled loop is unchanged, and the shift is suspected but not shown to come
from code placement. These prepared kernels are not reproductions of Goose's
published suite and are not a language-wide ranking.

## October 28, 2026 - Broader prepared-kernel comparisons

**Implemented:** a private comparison suite now covers sum, image blur,
particles, matrix multiplication, N-Queens and recursive Fibonacci, with
C, C++, Rust and pinned Goose controls at three sizes.

**Verified:** on Windows x64, 180 cross-language controls and full-output
checks passed, along with all 149 compiler tests. The measurements retain
8,100 timing samples and compare both existing build defaults and an equal
loop-unswitching setting. At the largest sizes with that setting matched,
Crust used about 28% less time for sum, 35% less for blur, 75% less for matrix
multiplication and 3% less for N-Queens than the Goose control. Particles was
inconclusive; Crust took about 56% more time for Fibonacci. C/C++ were faster
than Crust on several numeric cases.

**Limits and remaining work:** these are prepared kernels with changed
representations and timing boundaries, not reproductions of Goose's published
whole-process suite or evidence of a language-wide advantage. Nine paired
repetitions per comparison give screening evidence; near-ties need independent
confirmation. Allocation, setup and cleanup are outside the kernel timer.
Faithful calc, LRU, scene and library-dependent comparisons remain open. No
compiler optimization or safety rule changed for this experiment.

## October 28, 2026 - Prepared routing now faster than the Goose control

**Implemented:** optimized Crust builds now split loops on conditions that do
not change inside the loop. The routing block's per-sample mute checks
disappear, and its loop runs four samples at a time on the baseline x64
instruction set.

**Verified:** on Windows x64, two independent nine-pair campaigns measured the
256-frame reused-buffer routing block at about 40 ns per block for Crust. The
pinned Goose control measured about 149 ns, so Crust's time is roughly 27% of
Goose's. Checksums, mute and clipping controls, an exact output comparison
covering non-numeric values, infinities, and signed zero, the interoperability
suites, and the framing fixtures all passed. Crust-controlled processing
allocations stayed at zero.

**Limits and remaining work:** this covers prepared-buffer routing only. The
native controls were built without the same loop splitting, so this is not a
language ranking. Scoped scratch storage, clean-environment packaging, a full
SDRTW v3 rebuild, new receiver features, and Assembly remain open.

## October 28, 2026 - Prepared routing within 5% of the Goose control

**Implemented:** clamp-shaped value choices now compile to one minimum or
maximum step per bound. The compiler first proves that reordering cannot change
the result. Non-numeric values, infinities, and signed zero still pass through
unchanged.

**Verified:** on Windows x64, two independent nine-pair campaigns compared the
256-frame reused-buffer routing block with the pinned Goose control, alternating
which program ran first. Both put Crust about 1% slower than Goose. Every
95% interval stayed well under the 5% bar. Checksums, mute and clipping
controls, an exact output comparison covering non-numeric values, infinities,
and signed zero, the interoperability suites, and the framing fixtures at
one-dibit and 256-dibit feeds all passed. Crust-controlled processing
allocations stayed at zero.

**Limits and remaining work:** this covers prepared-buffer routing only. Crust
is still slower than the Rust control on this workload, and this is not a
language ranking or a live-receiver result. Scoped scratch storage,
clean-environment packaging, a full SDRTW v3 rebuild, new receiver features,
and Assembly remain open.

## October 28, 2026 - Prepared routing moved closer

**Implemented:** failure-only error construction stays off the successful
prepared-buffer path. A pure early return lowers to an ordered choice, so
clipping still preserves non-numeric values and infinities. Exclusive output
buffers are marked as not overlapping their inputs.

**Verified:** on Windows x64, a fresh three-repetition screen of the 256-frame
reused buffer leaves Crust about 20% above the fastest prepared native control.
That misses the 5% target, so the paired acceptance campaigns were not run.
Checksums, mute and clipping controls, and the framing fixtures passed,
including one-dibit and 256-dibit feeds. The 256-dibit feed is faster than its
kept Crust measurement. The one-dibit median stays inside that earlier run's
range. Crust-controlled processing allocations stayed at zero.

**Limits and remaining work:** this is prepared-buffer routing only. It does
not establish a live receiver, a language ranking, or a win over the native
controls. The 5% target remains open. Clean-environment packaging, a full
SDRTW v3 rebuild, new receiver features, and Assembly remain open.

## October 28, 2026 - Local code index

**Implemented:** a local index of modules, calls, and declared native bindings.
C sources are parsed separately from C++ headers. Language-server and agent
checks run as native Windows programs. Answer and embedding models stay on
the loopback interface, with cloud access disabled.

**Verified:** on Windows x64, the parser, process-cleanup, language-server,
and agent checks passed, and the compiler suite passed with the new extract
command. The configured answer context loaded on the Intel Arc B580. A
separate CPU-only request also completed. The embedding length was measured.
No startup service, Git hook, or recurring job was added.

**Limits and remaining work:** clean-environment packaging, a full SDRTW v3
rebuild, new receiver features, and Assembly remain open. This does not
establish a live receiver, a Crust-native P25 decoder, or a public compiler
download.

## October 28, 2026 - Developer workflow and measured execution cost

**Implemented:** project creation, ordinary-module tests, and locked builds that
pin the toolchain and native inputs. A compiler change reduced the cost of
successful calls from Crust into native code. A separate native framing runner
uses the same generated calls, reader, collector, validation, and timed
boundary as the Crust application.

**Verified:** on Windows x64, fresh before-and-after measurements of two
workloads each show a lower median cost. The 256-frame prepared-buffer routing
block is about 20% lower. Framing at a 256-dibit feed is about 50% lower.
Both clear a 10% bar. Nine alternating paired runs put the 95% confidence
interval entirely above a zero difference. One-dibit feeds are faster than their own
earlier Crust measurement, and patterned framing fixtures still pass. Checked
interfaces, complete error records, and zero Crust-controlled processing
allocations are unchanged. Native allocations stay reported on their own.
The narrower direct native measurement is unchanged and is not a language
ranking.

The native routing controls remain faster than Crust on the same boundary.
The separate native framing runner is also faster than the Crust application.
Pinned inputs do not promise byte-identical executables.

**Limits and remaining work:** no Assembly, custom allocator, full SDRTW v3
rebuild, new receiver features, clean-environment package, or public compiler
download is included. This does not establish a live receiver, a Crust-native
P25 decoder, or an advantage over the native controls.

## October 27, 2026 - First bounded SDRTW v3 framing proof

**Implemented:** a bounded offline application slice for selected P25 Phase 2
framing. Crust owns orchestration, validation, reset, event routing, and
lifecycle, using C, C++, and Rust native integrations and an isolated native
framing reference.

**Verified:** selected synthetic framing fixtures passed independently checked
native-reference expectations and actual Crust application runs on Windows x64.
The Crust checks passed with both unoptimized and optimized output, including
varied chunk boundaries, malformed inputs, reset, Unicode paths, native-library
loading, and resource lifecycle checks.

Repeated processing of the selected synthetic workload was faster than its
stream rate. This does not establish a Crust speed or memory advantage. The
native comparison used different timing boundaries, so these measurements do
not support a language-to-language speed ranking.

**Limits and remaining work:** this proves selected synthetic offline framing,
not a Crust-native P25 decoder, voice or security correctness, live hardware
operation, a full SDRTW v3 rebuild, or host compatibility. Broader receiver
features, other language and platform coverage, and clean-environment
prerelease packaging remain planned. No compiler download or public application
demonstration is available yet.

## October 27, 2026 - Selected records and checked resources

**Implemented:** selected records, owned resources, scoped borrowing,
ownership checks, error handling, deterministic cleanup, and explicit unsafe
boundaries.

**Verified:** selected synthetic native programs exercised these capabilities
across calls in both directions between Crust and each of C, C++, and Rust.
All six directions passed on Windows x64 with both unoptimized and optimized
output. Checks include rejection of invalid operations and resource cleanup
on selected failure paths.

These results cover the selected interfaces and documented rules. They do not
establish general memory safety, arbitrary foreign-library compatibility, or
a comparative speed or memory advantage.

**Application direction:** the planned first application proof has changed
from BTW recorded audio to a future SDR: The Works v3, beginning with a limited
P25 Phase 2 framing slice. Broader v3 functionality remains future work.
Earlier entries preserve the prior direction as a historical record.

**Remaining:** the application proof, broader language and library coverage,
other platforms, clean-environment packaging, and broader performance
evaluation. No application, receiver, decoder, or host compatibility has been
verified. No compiler download or application demonstration is available yet.

## October 27, 2026 - Selected symmetric interoperability

**Implemented:** generated interfaces between Crust and C, C++, and Rust for
scalar values and borrowed primitive buffers.

**Verified:** Crust calls each native language, and each native language calls
Crust, in synthetic native programs on Windows x64. All six directions passed
with both unoptimized and optimized output. Selected checks include invalid
input rejection, failure handling, and native cleanup paths.

**Remaining:** broader library and platform compatibility, records, owned
resources, full ownership and deterministic resource cleanup, BTW audio
execution, clean-environment packaging, and performance comparisons. This
limited interface proof establishes no application compatibility or comparative
speed or memory advantage. No compiler download or application demonstration
is available yet.

## October 27, 2026 - Core compiler and project builds

**Implemented:** core numeric operations, functions, control flow, modules,
and project builds.

**Verified:** native Crust programs and projects execute on Windows x64 with
both unoptimized and optimized output. Checks cover expected program results,
rejection of invalid programs, checked arithmetic, and diagnostics.

**Remaining at this checkpoint:** generated interfaces and six-direction
interoperability, followed by the full language, records, owned resources,
full ownership and resource cleanup, BTW audio execution, clean-environment
packaging, and performance comparisons. This milestone establishes no
comparative speed or memory advantage. No compiler download or application
demonstration is available yet.

## October 27, 2026 - First native Crust programs

**Implemented:** checking, building, and running small `.cru` programs within
the first scalar language subset.

**Verified:** native execution on Windows x64 with both unoptimized and
optimized output. Checks cover program results, rejection of invalid programs,
checked integer arithmetic, and source-located arithmetic failures.

**Remaining:** the full language, ownership checking, generated interfaces,
Crust interoperability in all six call directions, and BTW audio execution.
This milestone does not establish application performance or a comparative
speed advantage. No compiler download or application demonstration is available
yet.

## October 27, 2026 - Toolchain foundation

**Implemented:** developer checks for the required native tools.

**Verified:** a native-toolchain smoke test compiled, linked, and executed C,
C++, and Rust components together in the Windows development environment.
This result is limited to the native-toolchain fixture. It does not compile
Crust source or exercise generated Crust interfaces.

**Remaining:** `.cru` compilation, ownership checking, generated adapters,
Crust interoperability in all six call directions, and BTW audio execution.
No compiler download or application demonstration is available yet.

## October 27, 2026 - Design direction

**Design direction agreed; compiler implementation has not started.**

The initial direction is a native language with C-style syntax, `.cru` source
files, and first-class interoperability with C, C++, and Rust. Windows x64 is
the first target. A recorded-audio application proof for Broadcast: The Works
(BTW) will follow the compiler and interoperability foundations.

Implementation and detailed specifications will remain private. This public
journal will share dated milestone summaries and reviewed demonstrations as
they become available.

**Verification status:** no Crust native compilation, C/C++/Rust interoperability,
BTW audio execution, or host compatibility has been verified. No demonstration
or compiler download is available yet.

[Project introduction](README.md) | [Roadmap](ROADMAP.md)
