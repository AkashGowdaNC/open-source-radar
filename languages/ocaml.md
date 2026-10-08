# OCaml quickstart

How OCaml projects are usually set up, built and tested. Always prefer the project's own `CONTRIBUTING.md` when it says something different.

Open OCaml issues: [OCaml issue list](../issues/by-language/ocaml.md)

## Setup

- OCaml projects use [opam](https://opam.ocaml.org/) as the package manager and switch manager. Install it from [ocaml.org](https://ocaml.org/install) or with your system package manager.
- Give the project its own switch with `opam switch create . --deps-only --with-test`. That creates `_opam/` in the repo and installs the dependencies from the `.opam` files in one go. Run `eval $(opam env)` afterwards so your shell uses it.
- Check the installation with `ocaml --version` and `opam --version`.

## Common commands

| Task | Usual command |
| --- | --- |
| Create a local switch | `opam switch create . --deps-only --with-test` |
| Install dependencies | `opam install . --deps-only --with-test` |
| Build | `dune build` |
| Run tests | `dune test` |
| One test file | `dune test path/to/test_dir` |
| Check formatting | `dune build @fmt` (run `dune fmt` to fix) |
| Clean build artifacts | `dune clean` |

## Tips

- Check `dune-project` and the `dune` files for the project's build and test targets; `dune` is the standard build system and mostly replaces Makefiles.
- Formatting is driven by `.ocamlformat` at the project root. `dune build @fmt` fails on any diff, which is what CI usually runs, and `dune fmt` applies the fixes. The `ocamlformat` version is pinned in `.ocamlformat`, so install that exact version or the output won't match.
- Some projects use a `Makefile` that wraps `dune` commands, so check `Makefile` for a `test` or `fmt` target before running `dune` directly.

## Before you push

- [ ] Tests for the area you changed pass locally.
- [ ] Formatter passes with the project's configuration.
- [ ] Your diff contains no unrelated formatting or lockfile changes.

Back to [all languages](README.md) · [Guide](../guide/README.md)
