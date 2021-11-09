# ocaml-lsp inner dune-workspace repo project

## Installation

    git clone https://github.com/actionshrimp/lsp-dune-test-repo
    cd lsp-dune-test-repo
    opam switch create . --empty
    opam switch set-invariant ocaml-base-compiler.4.12.1
    opam install ocaml-lsp-server dune
    opam exec -- dune build

## Repro

At this point ocaml-lsp doesn't seem to like symbols in `vendor/inner-a/src/inner_a_main.ml`. Inside `vendor/inner-a/src/inner_a_lib.ml` I get this error message:

    No config found for file "inner_a_lib.ml" in "src". Try calling `dune build`.

However, the Inner_a reference from `src/lib.ml` functions correctly.

If you rename `vendor/inner-a/dune-workspace` to `dune-workspace.bak`, restart the LSP process, and run `dune build` again, everything seems to function as expected.
