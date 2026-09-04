# Contributing to Hyper

Thanks for contributing. This is a short getting-started guide. For a full toolchain walkthrough, see [Building from source](doc/building.md). What CI runs on every PR is in [`.github/workflows/ci.yml`](.github/workflows/ci.yml).

## Prerequisites

- [Rust](https://www.rust-lang.org/tools/install) (stable) — `cargo` and `rustc`
- Git
- A C compiler (`cc`, `clang`, or `gcc`) if you use `compile --emit-exe`

On Windows, [WSL](https://learn.microsoft.com/en-us/windows/wsl/) is the smoothest path; native Windows can `cargo build`, but AOT linking may need MSVC or MinGW.

## Build

```bash
git clone https://github.com/muhammadyusufpov/hyper.git
cd hyper
cargo build
```

The debug binary is `target/debug/hyper`. Use `cargo build --release` for a release binary.

## Run tests

```bash
cargo test
```

## Run smoke tests

Interpreter and compiler JIT on the core smoke program:

```bash
cargo run -- run ci/smoke.hyp
cargo run -- compile ci/smoke.hyp
```

CI also runs other programs under `ci/` (I/O, JSON, `break` / `continue`, `--emit-exe`, and run/compile output parity). See [`.github/workflows/ci.yml`](.github/workflows/ci.yml).

## Code style

```bash
cargo fmt
cargo clippy
```

Use the standard Rust toolchain formatters. Keep interpreter and compiler code readable; match the style of the file you are editing.

## Commit messages

Use [conventional commits](doc/COMMIT_CONVENTION.md). Start the subject with a prefix and no trailing period:

- `feat:` — new feature
- `fix:` — bug fix
- `docs:` — documentation
- `ci:` — CI, GitHub Actions, or smoke programs under `ci/`
- `test:`, `refactor:`, `style:`, `chore:` — also allowed; see the convention doc

## How to open a PR

1. Fork the repository.
2. Create a branch for your change.
3. Make the change, run `cargo test` and the smoke commands above, then commit with a conventional prefix.
4. Push the branch to your fork.
5. Open a pull request against `main`.

Before filing a bug, search existing [issues](https://github.com/Yusupov-Muhammadyusuf/hyperlang/issues). Include OS, steps to reproduce, and expected vs actual behavior.

Discuss large architectural or syntax changes in an issue before opening a PR.
