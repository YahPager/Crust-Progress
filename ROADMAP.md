# Crust Roadmap

This roadmap describes the initial direction. Status applies only to the
stated result; planned milestones are not completed features or release-date
promises.

| Milestone | Intended result | Status |
|---|---|---|
| Developer toolchain foundation | Check required native tools and run a mixed C/C++/Rust native-toolchain smoke test | Verified, limited to the Windows development environment |
| Native compiler | Compile and run Crust programs and projects on Windows x64 | Core subset verified; full language remains planned |
| C, C++, and Rust interoperability | Call selected library interfaces and expose Crust functions to each language | Selected scalar and borrowed-buffer interfaces verified in all six call directions on Windows x64 |
| Checked resources | Demonstrate compiler checks and predictable resource cleanup | Planned |
| BTW application proof | Process recorded audio in a useful Broadcast: The Works demonstration | Planned |
| Private prerelease | Verify the compiler and application proof in a clean Windows environment | Planned |

The interoperability result is limited to selected synthetic interfaces in the
Windows development environment. Broader library compatibility, records, owned
resources, full ownership and cleanup, audio integration, clean-environment
packaging, and performance comparisons remain planned.

## Status definitions

- **Planned:** agreed direction; no implementation or verification claim.
- **Implemented:** code exists; acceptance verification remains incomplete.
- **Verified:** the stated checks passed in a documented environment, with
  limitations recorded in the progress journal.

Public updates will focus on verified milestones and reviewed demonstrations.
There is no public compiler or binary release at this stage.

[Project introduction](README.md) | [Progress journal](PROGRESS.md)
