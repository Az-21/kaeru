# Speckit Constitution

## Rust

```
Write clean, readable Rust. Prioritise clarity over cleverness — if a simpler approach is 0.1% slower, use the simpler approach. Document the intent of functions (why they exist, what decisions they make, what the invariants are), not a paraphrase of their name. Keep files under 200 lines and separate concerns into distinct module folders — no catch-all utils.rs. After every change, run cargo fmt, cargo clippy, cargo check, cargo build, and cargo test in order, and fix all issues before moving on. Write unit tests for every piece of logic, with test names and comments that describe the behaviour being guarded against regression. Never use .unwrap() outside of tests. Prefer concrete implementations over premature abstractions. Use well-established crates from the ecosystem rather than reinventing the wheel — reach for tokio, serde, thiserror, anyhow, reqwest, axum, clap, and similar battle-tested libraries where they fit. Always use the latest stable version of any dependency.
```
