# Crust Progress

Crust is a planned native systems language with C-style syntax and `.cru`
source files. Its goal is first-class interoperability with C, C++, and Rust,
with Windows x64 as the initial target.

Maintained by [YahPager](https://github.com/YahPager).

## Current status

**Developer toolchain foundation implemented; Crust source compilation remains planned.**

Developer toolchain checks are implemented. A native-toolchain smoke test has
verified that C, C++, and Rust components can be compiled, linked, and executed
together in the Windows development environment.

That test does not compile `.cru` programs or validate generated interfaces.
Crust source compilation, ownership checking, symmetric Crust interoperability,
and Broadcast: The Works (BTW) audio integration remain planned. The first
application goal is a recorded-audio demonstration for BTW.

## Follow progress

- [Roadmap](ROADMAP.md): planned milestones and status definitions.
- [Progress journal](PROGRESS.md): dated updates and verified results.

This public repository contains project summaries and, when available,
reviewed screenshots and demonstration videos. Compiler source, detailed
specifications, internal development records, and binaries remain private.
No compiler download is available here.

Planned features describe goals. Compatibility and performance claims will
identify what was actually tested and any remaining limitations.
