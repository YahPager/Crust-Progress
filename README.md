<p align="center">
  <img src="assets/branding/crust-logo-transparent 1163x387.png" alt="Crust logo" width="420">
</p>

# Crust Progress

Crust is an experimental native systems language with C-style syntax and `.cru`
source files. Its goal is first-class interoperability with C, C++, and Rust,
with Windows x64 as the initial target.

Maintained by [YahPager](https://github.com/YahPager).

## Current status

**Selected records, checked resources, and symmetric interoperability verified on Windows x64.**

The compiler can check, build, and execute Crust programs and projects using
core numeric operations, functions, control flow, and modules. Native execution
and invalid-program rejection have been verified with both unoptimized and
optimized output, including checked arithmetic and diagnostics.

Selected generated interfaces support calls in both directions between Crust
and each of C, C++, and Rust for scalar values, borrowed primitive buffers,
records, and owned resources. All six directions were verified using synthetic
native programs on Windows x64 with both unoptimized and optimized output.

The selected resource checks cover scoped borrowing, ownership, errors,
deterministic cleanup, and explicit unsafe boundaries, including rejection of
invalid operations. These checks establish a limited interface and resource
proof. Foreign implementations still need to honor their declared contracts;
broader language safety, library compatibility, and platform support require
separate verification.

Developer toolchain checks and a separate mixed C/C++/Rust native-toolchain
smoke test are also verified in the Windows development environment.

The first application proof is now planned for a future SDR: The Works v3,
starting with a limited P25 Phase 2 framing slice. Broader v3 functionality
remains future work. No application proof, receiver, decoder, or host
compatibility has been verified.

The full language, broader compatibility, clean-environment packaging, and
broader performance evaluation remain planned. No comparative speed or memory
advantage has been established.

## Follow progress

- [Roadmap](ROADMAP.md): planned milestones and status definitions.
- [Progress journal](PROGRESS.md): dated updates and verified results.

This public repository contains project summaries, reviewed branding, and,
when available, reviewed screenshots and demonstration videos. Compiler source,
detailed specifications, internal development records, and binaries remain private.
No compiler download is available here.

Planned features describe goals. Compatibility and performance claims will
identify what was actually tested and any remaining limitations.
