# Crust Progress Journal

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
