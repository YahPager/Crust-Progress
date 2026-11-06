# Crust Roadmap

This roadmap describes the initial direction. Status applies only to the
stated result; planned milestones are not completed features or release-date
promises.

| Milestone | Intended result | Status |
|---|---|---|
| Developer toolchain foundation | Check required native tools and run a mixed C/C++/Rust native-toolchain smoke test | Verified, limited to the Windows development environment |
| Native compiler | Compile and run Crust programs and projects on Windows x64 | Core Windows subset verified; Linux support withdrawn |
| Optional JIT execution | Execute checked Crust programs and tests through an opt-in native JIT path | Selected Windows x64 execution, interface and lifecycle checks verified; AOT remains the default |
| C, C++, and Rust interoperability | Call selected library interfaces and expose Crust functions to each language | Selected interfaces verified on Windows in all six call directions |
| Checked resources | Demonstrate records, ownership, errors and cleanup | Selected checks verified on Windows x64 with unoptimized and optimized output |
| SDR: The Works v3 application proof | Exercise a bounded offline P25 Phase 2 framing slice | Selected synthetic framing verified on Windows x64; full receiver and host compatibility remain unverified |
| Broader SDR: The Works v3 | Build a separate application with features implemented in Crust wherever practical and minimal third-party dependencies | In progress on Windows. Offline synthetic reception, no-hardware Airspy checks and prepared playback consumption have passed. Intelligibility and live hardware remain unverified |
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
| Composable application data | Owned records, methods, variants and optional values | Selected subset verified on Windows x64 |
| Reusable abstractions | Generic algorithms and data types with static constraints | Selected subset verified on Windows x64 in AOT/JIT with unoptimized and optimized output |
| Reusable libraries | Library/dependency workflows and useful standard facilities | Selected subset verified on Windows x64 |
| Windows host projects | Separate explicit host-target locks and build outputs | Windows x64 verified; Linux support removed |
| General-purpose standard library | Collections, UTF-8 text, formatting, bounded JSON, files, clocks and synchronous TCP | Selected Windows subset verified |
| Concurrency | Safe threads, communication and native integration | Selected Windows scope verified |
| Processing libraries | Selected reusable numerical and protocol components | Selected components verified on Windows x64; performance campaigns planned |
| General usability | Developer tools, documentation and independent CLI, network-service and streaming demonstrations | Verified on Windows x64 |
| Measured optimization | Improve demonstrated compiler, runtime and library bottlenecks | Planned; preserve correctness and safety checks |
| Independent performance validation | Target runtime within 2.5% of each test's fastest qualifying competitor on this same machine | Planned; repeated local results determine acceptance, with other-machine results shown separately as references |

The separate SDRTW v3 application is in progress on Windows. Crust's
general-purpose work remains independent of that receiver. Readiness for
general-purpose public use will also need evidence from independent programs.
The existing public-readiness review remains a separate decision; this roadmap
does not select a license, announce a release date, publish implementation or
binaries, or establish a completion percentage.

The first application proof changed from BTW recorded audio to the bounded
SDR: The Works v3 framing slice. Earlier progress entries retain the previous
direction as a historical record. Broader v3 features are underway. Live
hardware and a finished receiver remain future work.

## Status definitions

- **Planned:** agreed direction; no implementation or verification claim.
- **Implemented:** code exists; acceptance verification remains incomplete.
- **Verified:** the stated checks passed in a documented environment, with
  limitations recorded in the progress journal.

Public updates will focus on verified milestones and reviewed demonstrations.
There is no public compiler or binary release at this stage.

[Project introduction](README.md) | [Progress journal](PROGRESS.md)
