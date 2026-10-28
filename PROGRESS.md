# Crust Progress Journal

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
