# Datadog tracer import

Minimal reproducible example with failing named import of Datadog tracer for Node.js.

## Steps to reproduce

```bash
npm run build
npm start
```

Content of `build/index.js`:

```javascript
// Added automatically by VS Code
import { tracer } from "dd-trace";
tracer.init();
```

## Actual result

```
> dd-trace-import-repro@0.1.0 start
> node build/index.js

file:///.../build/index.js:2
import { tracer } from "dd-trace";
         ^^^^^^
SyntaxError: Named export 'tracer' not found. The requested module 'dd-trace' is a CommonJS module, which may not support all module.exports as named exports.
CommonJS modules can always be imported via the default export, for example using:

import pkg from 'dd-trace';
const { tracer } = pkg;

    at ModuleJob._instantiate (node:internal/modules/esm/module_job:146:21)
    at async ModuleJob.run (node:internal/modules/esm/module_job:229:5)
    at async ModuleLoader.import (node:internal/modules/esm/loader:473:24)
    at async asyncRunEntryPointWithESMLoader (node:internal/modules/run_main:123:5)

Node.js v20.18.0
```

## Expected result

Either compilation error or successful execution of the script.
