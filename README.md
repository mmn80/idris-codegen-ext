# idris-codegen-ext

NOTE: depends on a PR on `idris` which has not been merged; postponed...

A version of the `idris` executable extended with a new (embedded) code generator.

The codegen is just a clone of the built in C codegen, with the only difference
being the addition of the `register` and `getRTSDir` functions to `IRTS.MyCodegenC`,
the call to `register` in `main`, and renaming of `libidris_rts.a` to
`libmyidris_rts.a` in the `Makefile` inside the `rts` dir.
The `Setup.hs` is just a clone of `idris`s `Setup.hs` with irrelevent parts removed.

This executable can be used in place of the normal `idris` in order to have
access to this new codegen from the REPL or from IDE mode, with the overhead
associated with loading IBC files of the prelude or other dependencies
being eliminated.

It is suited for interactive code generation, eg. compiling one module at a time
from the REPL/IDE mode server process.

## How to use

`idris-ext --codegen X ./SomeModule.idr -o SomeExecutable`

From the REPL: `:c X SomeExecutable`
