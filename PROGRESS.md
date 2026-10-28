# Crust Progress Journal

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
