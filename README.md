<p align="center">
  <img src="assets/branding/crust-logo-transparent 1163x387.png" alt="Crust logo" width="420">
</p>

# Crust Progress

Crust is an experimental native systems language with C-style syntax and `.cru`
source files. Its goal is first-class interoperability with C, C++, and Rust,
with Windows x64 as the initial target.

Maintained by [YahPager](https://github.com/YahPager).

## Current status

**Core compiler and selected C/C++/Rust interoperability verified on Windows x64.**

The compiler can check, build, and execute Crust programs and projects using
core numeric operations, functions, control flow, and modules. Native execution
and invalid-program rejection have been verified with both unoptimized and
optimized output, including checked arithmetic and diagnostics.

Selected generated interfaces now support calls in both directions between
Crust and each of C, C++, and Rust for scalar values and borrowed primitive
buffers. All six directions were verified using synthetic native programs on
Windows x64, including selected failure handling and native cleanup paths.
This remains a limited interface proof; broader library and platform
compatibility requires separate verification.

Developer toolchain checks and a separate mixed C/C++/Rust native-toolchain
smoke test are also verified in the Windows development environment.

The full language, records, owned resources, full ownership and resource cleanup,
Broadcast: The Works (BTW) audio integration, clean-environment packaging, and
performance comparisons remain planned. The first application goal is a
recorded-audio demonstration for BTW. These milestones establish no comparative
speed or memory advantage.

## Follow progress

- [Roadmap](ROADMAP.md): planned milestones and status definitions.
- [Progress journal](PROGRESS.md): dated updates and verified results.

This public repository contains project summaries, reviewed branding, and,
when available, reviewed screenshots and demonstration videos. Compiler source,
detailed specifications, internal development records, and binaries remain private.
No compiler download is available here.

Planned features describe goals. Compatibility and performance claims will
identify what was actually tested and any remaining limitations.
