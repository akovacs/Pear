# Change Log
All notable changes to this fork of the project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/)
and this project adheres to [Semantic Versioning](https://semver.org/).

Changelog notes for each version may be split into:

 - Breaking changes: user-visible changes which may require updates in downstream components.
 - Compatibility: which compiler and dependency versions are supported.
 - Features: new functionality, or backwards-compatible changes in existing functionality.
 - Fixes: bugfixes, security fixes, removing sharp edges.
 - Performance: performance-oriented improvements: memory-usage, cpu usage, etc.
 - Releases: ready-to-run compiled binaries which may be distributed via Github Releases
    or other distribution systems.

## [0.1.5-Stable-WIP] - 2026-10-23

### Features
This is currently still broken, but some compilation issues (specifically those related to
::proc_macro::Diagnostic) have been resolved.

Remove nightly requirements and check for features which require nightly compiler
1. Add proc-macro2-diagnostics dep, remove unstable feature proc_macro_diagnostic
2. Use externally-defined proc-macro2-diagnostics = 0.11 dep and import it as
     use proc_macro2_diagnostics::{SpanDiagnosticExt, Diagnostic};
     rather than defining Diagnostic.

### Compatibility: Compiled using
 - cargo 1.85.0 (
 - rustc 1.85.0 ( rust-toolchain.toml: [toolchain] channel = "1.85.0" )

with 


Requires modified proc-macro2 0.4.5 built using stable 1.85.0 compiler without nightly features

git clone https://github.com/akovacs/proc-macro2
cd proc-macro2
git checkout v0.4.5-on-1.85.0-stable-compiler-attempt-wip

Be sure to use the stable rust-toolchain.toml channel = "1.85.0"

https://github.com/rust-lang/futures-rs/issues/1564

Build using:
RUSTFLAGS='--cfg procmacro2_semver_exempt' cargo build

https://github.com/akovacs/proc-macro2/tree/v0.4.5-on-1.85.0-stable-compiler-attempt-wip#unstable-features


## [0.1.5-Nightly] - 2026-10-22

Tested that compilation is successful using the following nightly compiler.

### Compatibility: Compiled using
 - cargo 1.85.0-nightly (769f622e1 2024-12-14)
 - rustc 1.85.0-nightly (0aeaa5eb2 2024-12-14)
