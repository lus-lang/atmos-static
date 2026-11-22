# static

`static` serves the files of a directory over HTTP with content types, `ETag` and `Last-Modified` validators, `Range` requests, `Cache-Control`, and index files, refusing any path that leaves the root. It works as a `web` plugin and as a handler for `network.serve`.

The following example serves a `public` directory under `/assets` of a web application, then as a server of its own.

```lus nocheck
local static = require("https://atmosp.here/2.0/static.lus")

-- As a plugin of a web application, under a prefix.
app:register(static, { root = "public", prefix = "/assets", max_age = 3600 })

-- As a server of its own.
network.serve("0.0.0.0", 8080, static.handler({ root = "public" }))
```

The package requires Lus 2.0 and declares the permission `fs:read`, which it uses to read the directory it serves. It never calls `pledge`, so the program that loads it keeps control of its permissions.

The reference is in the doc comments of `static.lus`, which `lus doc static.lus` prints.
