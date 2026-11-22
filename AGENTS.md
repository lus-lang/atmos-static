# AGENTS.md

This repository, `lus-lang/atmos-static`, is the `static` package of the atmosphere registry. Programs load it with `require("https://atmosp.here/2.0/static.lus")`.

## Scope

Serves the files of a directory with content types, `ETag` and `Last-Modified` validators, `Range` requests, `Cache-Control`, and index files. It refuses paths that leave the root. It works as a `web` plugin and as a bare `network.serve` handler. The public API is every function that `static.lus` returns in its module table. A change to that API needs a new entry in `CHANGELOG.md` and a version change in the header.

## Layout

- `static.lus` is the whole package. Its header doc comment carries the package metadata and the declared permissions.
- `tests/*_test.lus` are the tests. They load the package from the parent directory through `TEST_DIR`.

The tests load `web` from a checkout of `lus-lang/atmos-web` next to this repository, so clone it into the same parent directory first.

## Commands

```sh
lus test tests          # run the tests
lus check static.lus     # lint, including the package codes
lus doc static.lus       # print the reference
```

## Rules

- Every public function has a doc comment that states each result and each error, following `spec/design/style.md` of the Lus repository.
- The package never calls `pledge`. A new permission is declared in the header and in the README.
- Prose has no dashes and no semicolons, and never names the Roblox Lua dialect.
- Every bug fix comes with a test that fails without it.
