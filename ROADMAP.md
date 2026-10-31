# Crust Roadmap

This roadmap describes the initial direction. Status applies only to the
stated result; planned milestones are not completed features or release-date
promises.

| Milestone | Intended result | Status |
|---|---|---|
| Developer toolchain foundation | Check required native tools and run a mixed C/C++/Rust native-toolchain smoke test | Verified, limited to the Windows development environment |
| Native compiler | Compile and run Crust programs and projects on Windows x64 | Core Windows subset verified; Linux support withdrawn |
| Optional JIT execution | Execute checked Crust programs and tests through an opt-in native JIT path | Selected Windows x64 execution, interface and lifecycle checks verified; AOT remains the default |
| C, C++, and Rust interoperability | Call selected library interfaces and expose Crust functions to each language | Selected interfaces verified on Windows AOT/JIT in all six call directions, including scalar/span and exact resource cleanup checks |
| Checked resources | Demonstrate records, scoped borrowing, ownership, errors, cleanup, and explicit unsafe boundaries | Selected checks verified on Windows x64 with unoptimized and optimized output |
| SDR: The Works v3 application proof | Exercise a bounded offline P25 Phase 2 framing slice | Selected synthetic framing verified on Windows x64; full receiver and host compatibility remain unverified |
| Broader SDR: The Works v3 | Rebuild broader receiver behavior and add future features | Planned |
| Private prerelease | Verify the compiler and application proof in a clean Windows environment | Planned |

The interoperability and resource results are limited to selected synthetic
interfaces and checks in the documented Windows environment. Earlier Fedora
results remain historical; Linux support was withdrawn on October 31, 2026.
Framing remains verified on Windows. A
Crust-native P25 decoder, voice and security correctness, live hardware,
full receiver behavior, host compatibility, clean-environment packaging, and
broader language and platform coverage remain unverified. Published
[comparisons across languages](README.md#measured-comparisons-across-languages)
cover named workloads and show both strengths and remaining gaps. They do not
establish a general language-wide speed or memory advantage.

## General-purpose language growth

Direction agreed October 28, 2026. Crust is intended for eventual public use
across native systems applications. The roadmap now separates language maturity
from the needs of any one application. Establishing this roadmap adds no new
compiler or library behavior.

| Area | Intended result | Status |
| --- | --- | --- |
| Composable application data | Owned records, methods, tagged variants, optional values and returned views | Selected subset verified on Windows x64 in AOT/JIT; explicit private record fields and encapsulated public types verified on Windows AOT/JIT with unoptimized and optimized output |
| Reusable abstractions | Generic algorithms and data types with static constraints | Selected subset verified on Windows x64 in AOT/JIT with unoptimized and optimized output |
| Reusable libraries | Library/dependency workflows and useful standard facilities | Local packages, static/shared builds and the Phase 5 standard-library subset verified on Windows x64 in AOT/JIT with unoptimized and optimized output |
| Windows host projects | Separate explicit host-target locks and build outputs | Windows x64 verified; Linux support removed |
| General-purpose standard library | Collections, UTF-8 text, formatting, bounded JSON, files, clocks and synchronous TCP | Phase 5 supported Windows subset verified in AOT/JIT, including independent file-processing and TCP/JSON programs, allocation failures, cleanup and selected native interfaces |
| Concurrency | Safe threads, communication and native integration lifetimes | Phase 6 in progress; selected function references, owned workers, cooperative stop and shared/weak ownership verified on Windows AOT/JIT; atomics, locks, communication and callbacks remain planned |
| Processing libraries | Selected reusable numerical and protocol components | Planned |
| General usability | Developer tools, documentation and independent CLI, network-service and streaming demonstrations | Planned |
| Measured optimization (Phase 9) | Improve demonstrated compiler, runtime and library bottlenecks | Planned; preserve correctness and safety checks |
| Independent performance validation (Phase 10) | Target runtime within 2.5% of each test's fastest qualifying competitor on this same machine | Planned; repeated local results determine acceptance, with other-machine results shown separately as references |

The full SDRTW v3 rebuild stays deferred while Crust matures and v2e development
continues. Receiver work is one future test of the language. Readiness for
general-purpose public use will also need evidence from independent programs.
The existing public-readiness review remains a separate decision; this roadmap
does not select a license, announce a release date, publish implementation or
binaries, or establish a completion percentage.

The first application proof changed from BTW recorded audio to the bounded
SDR: The Works v3 framing slice. Earlier progress entries retain the previous
direction as a historical record. Broader v3 features remain future work.

## Status definitions

- **Planned:** agreed direction; no implementation or verification claim.
- **Implemented:** code exists; acceptance verification remains incomplete.
- **Verified:** the stated checks passed in a documented environment, with
  limitations recorded in the progress journal.

Public updates will focus on verified milestones and reviewed demonstrations.
There is no public compiler or binary release at this stage.

[Project introduction](README.md) | [Progress journal](PROGRESS.md)
