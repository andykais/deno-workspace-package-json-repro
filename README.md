## Repro
```bash
cd ./packages/test-package-json
deno install
```

Observe the error:
```
error: npm package '@jsr/std__datetime' does not exist.
```

This error is consistent if dependencies are installed with `deno install` or `npm install`


Note that npm depednencies work fine within a package.json project in a workspace (like the `lodash` dependency). You can prove this by removing the `@std/datetime` dependency and seeing that things will function fine.


Also note that the deno.json associated repo breaks as well _after_ the package-json-test project attempts to install the jsr dependency
```bash
cd ./packages/test-deno-json
deno install
```
Observe the error:
```
error: npm package '@jsr/std__datetime' does not exist.
```

The deno error will stop appearing if you drop the ./packages/test-package-json from the top level workspace
