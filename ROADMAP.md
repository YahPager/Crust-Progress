# Crust Roadmap

This roadmap describes the initial direction. Status applies only to the
stated result; planned milestones are not completed features or release-date
promises.

| Milestone | Intended result | Status |
|---|---|---|
| Developer toolchain foundation | Check required native tools and run a mixed C/C++/Rust native-toolchain smoke test | Verified, limited to the Windows development environment |
| Native compiler | Compile and run Crust programs and projects on Windows x64 | Core subset verified; full language remains planned |
| C, C++, and Rust interoperability | Call selected library interfaces and expose Crust functions to each language | Selected scalar, borrowed-buffer, record, and owned-resource interfaces verified in all six call directions on Windows x64 |
| Checked resources | Demonstrate records, scoped borrowing, ownership, errors, cleanup, and explicit unsafe boundaries | Selected checks verified on Windows x64 with unoptimized and optimized output |
| SDR: The Works v3 application proof | Exercise a bounded offline P25 Phase 2 framing slice | Selected synthetic framing verified on Windows x64; full receiver and host compatibility remain unverified |
| Broader SDR: The Works v3 | Rebuild broader receiver behavior and add future features | Planned |
| Private prerelease | Verify the compiler and application proof in a clean Windows environment | Planned |

The interoperability, resource, and framing results are limited to selected
synthetic interfaces and checks in the Windows development environment. A
Crust-native P25 decoder, voice and security correctness, live hardware,
full receiver behavior, host compatibility, clean-environment packaging, and
broader language and platform coverage remain unverified. No comparative speed
or memory advantage has been established.

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
