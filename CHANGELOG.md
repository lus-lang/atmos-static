# Changelog

## 1.0.0

**Release date:** TBD

Version 1.0.0 is the first release of `static`.

- Added the `static` package.
  - `static.handler`: Returns a handler for `network.serve` that serves the files of a directory.
  - `static.register`: Registers the file server on a `web` scope under a prefix.
  - `static.mime`: Returns the content type for a file name, a path, or an extension.
  - `static.types`: The content type of each file extension, which a program may extend.
