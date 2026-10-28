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
| SDR: The Works v3 application proof | Begin a future v3 proof with a limited P25 Phase 2 framing slice | Planned; no application or host compatibility verified |
| Private prerelease | Verify the compiler and application proof in a clean Windows environment | Planned |

The interoperability and resource results are limited to selected synthetic
interfaces and checks in the Windows development environment. Broader language
safety, library and platform compatibility, application behavior,
clean-environment packaging, and broader performance evaluation remain planned.
No comparative speed or memory advantage has been established.

The planned first application proof has changed from BTW recorded audio to
future SDR: The Works v3 framing. Earlier progress entries retain the previous
direction as a historical record. Broader v3 features remain future work.

## Status definitions

- **Planned:** agreed direction; no implementation or verification claim.
- **Implemented:** code exists; acceptance verification remains incomplete.
- **Verified:** the stated checks passed in a documented environment, with
  limitations recorded in the progress journal.

Public updates will focus on verified milestones and reviewed demonstrations.
There is no public compiler or binary release at this stage.

[Project introduction](README.md) | [Progress journal](PROGRESS.md)
