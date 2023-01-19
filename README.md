# ts-node-unknown-file-extension-binaries

This repo is a minimal reproduction of this issue ERR_UNKNOWN_FILE_EXTENSION for binaries without extension.

## Steps

1. Clone the repo
2. Install nvm
3. Install node 18: `nvm install`
4. Install deps: `npm install`
5. Run the start script: `npm start`
6. The following error should appear:
```bash
$ npm start

> ts-node-error@1.0.0 start
> ts-node --esm $(npm bin)/uuid

/Users/enrq/Workspace/tests/ts-node-error/node_modules/ts-node/dist-raw/node-internal-modules-esm-get_format.js:93
        throw new ERR_UNKNOWN_FILE_EXTENSION(ext, fileURLToPath(url));
              ^
CustomError: ERR_UNKNOWN_FILE_EXTENSION  /Users/enrq/Workspace/tests/ts-node-error/node_modules/uuid/dist/bin/uuid
    at defaultGetFormat (/Users/enrq/Workspace/tests/ts-node-error/node_modules/ts-node/dist-raw/node-internal-modules-esm-get_format.js:93:15)
    at defer (/Users/enrq/Workspace/tests/ts-node-error/node_modules/ts-node/src/esm.ts:296:7)
    at entrypointFallback (/Users/enrq/Workspace/tests/ts-node-error/node_modules/ts-node/src/esm.ts:304:22)
    at getFormat (/Users/enrq/Workspace/tests/ts-node-error/node_modules/ts-node/src/esm.ts:338:26)
    at /Users/enrq/Workspace/tests/ts-node-error/node_modules/ts-node/src/esm.ts:245:17
    at addShortCircuitFlag (/Users/enrq/Workspace/tests/ts-node-error/node_modules/ts-node/src/esm.ts:409:21)
    at load (/Users/enrq/Workspace/tests/ts-node-error/node_modules/ts-node/src/esm.ts:239:12)
    at load (/Users/enrq/Workspace/tests/ts-node-error/node_modules/ts-node/src/child/child-loader.ts:18:36)
    at nextLoad (node:internal/modules/esm/loader:163:28)
    at ESMLoader.load (node:internal/modules/esm/loader:605:26)
```
7. Install node 16 (`nvm install 16`) and use it (`nvm use 16`)
8. Run again the start script: `npm start`
9. Now it works:
```bash
$ npm start

> ts-node-error@1.0.0 start
> ts-node --esm $(npm bin)/uuid

345f5060-40a8-4d04-bf48-c8680aa901f2
```
