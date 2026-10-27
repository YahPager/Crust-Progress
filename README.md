<p align="center">
  <img src="assets/branding/crust-logo-transparent 1163x387.png" alt="Crust logo" width="420">
</p>

# Crust Progress

Crust is an experimental native systems language with C-style syntax and `.cru`
source files. Its goal is first-class interoperability with C, C++, and Rust,
with Windows x64 as the initial target.

Maintained by [YahPager](https://github.com/YahPager).

## Current status

**First native Crust programs verified on Windows x64, within a small scalar subset.**

The compiler can check, build, and execute small `.cru` programs. This first
subset has been verified with both unoptimized and optimized output, including
checked integer arithmetic and diagnostics for invalid programs and arithmetic
failures.

Developer toolchain checks and a separate mixed C/C++/Rust native-toolchain
smoke test are also verified in the Windows development environment.

The full language, ownership checking, generated interfaces, Crust interoperability
in all six call directions, and Broadcast: The Works (BTW) audio integration
remain planned. The first application goal is a recorded-audio demonstration
for BTW. This milestone does not establish application performance or a
comparative speed advantage.

## Follow progress

- [Roadmap](ROADMAP.md): planned milestones and status definitions.
- [Progress journal](PROGRESS.md): dated updates and verified results.

This public repository contains project summaries, reviewed branding, and,
when available, reviewed screenshots and demonstration videos. Compiler source,
detailed specifications, internal development records, and binaries remain private.
No compiler download is available here.

Planned features describe goals. Compatibility and performance claims will
identify what was actually tested and any remaining limitations.
