# static

Serves the files of a directory with content types, `ETag` and `Last-Modified` validators, `Range` requests, `Cache-Control`, and index files. It refuses paths that leave the root. It works as a `web` plugin and as a bare `network.serve` handler.

```lus nocheck
local static = require("https://atmosp.here/2.0/static.lus")

-- As a plugin of a web application, under a prefix.
app:register(static, { root = "public", prefix = "/assets", max_age = 3600 })

-- As a server of its own.
network.serve("0.0.0.0", 8080, static.handler({ root = "public" }))
```

The package requires Lus 2.0. It needs `fs:read` for the directory it serves. It calls no `pledge` of its own, so the program that loads it keeps control of its permissions.

The reference is in the doc comments of `static.lus`. Run `lus doc static.lus` to print it.
