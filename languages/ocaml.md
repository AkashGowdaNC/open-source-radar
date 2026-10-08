# OCaml quickstart

How OCaml projects are usually set up, built and tested. Always prefer the project's own `CONTRIBUTING.md` when it says something different.

Open OCaml issues: [OCaml issue list](../issues/by-language/ocaml.md)

## Setup

- OCaml projects use [opam](https://opam.ocaml.org/) as the package manager and switch manager. Install it from [ocaml.org](https://ocaml.org/install) or with your system package manager.
- Create or select a switch for the project with `opam switch`, then install dependencies from the project's `.opam` file with `opam install . --deps-only --with-test`.
- Check the installation with `ocaml --version` and `opam --version`.

## Common commands

| Task | Usual command |
| --- | --- |
| Create or select a switch | `opam switch` (interactive) |
| Install dependencies | `opam install . --deps-only --with-test` |
| Build | `dune build` |
| Run tests | `dune test` |
| One test file | `dune test path/to/test_dir` |
| Check formatting | `dune fmt` (uses `ocamlformat` when configured) |
| Clean build artifacts | `dune clean` |

## Tips

- Check `dune-project` and the `dune` files for the project's build and test targets; `dune` is the standard build system and mostly replaces Makefiles.
- Formatting is driven by `.ocamlformat` at the project root. Run `dune fmt` before committing; if the project does not use `ocamlformat`, `dune fmt` may be a no-op.
- Some projects use a `Makefile` that wraps `dune` commands, so check `Makefile` for a `test` or `fmt` target before running `dune` directly.

## Before you push

- [ ] Tests for the area you changed pass locally.
- [ ] Formatter passes with the project's configuration.
- [ ] Your diff contains no unrelated formatting or lockfile changes.

Back to [all languages](README.md) · [Guide](../guide/README.md)