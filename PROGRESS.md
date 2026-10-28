# Crust Progress Journal

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
