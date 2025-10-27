Node.js
========================

## Attach chrome debugger

https://frontendmasters.com/blog/node-js-debugging-in-chrome-devtools/

1. open debugger at [chrome://inspect/#devices](chrome://inspect/#devices)
2. run `node --inspect-brk app.js` in terminal
3. profit

## Misc meanings

`process.cwd()` - shows current local working directory, example output - `/home/user/repos/node-project`

## Express 

### npm  install checklist
- express
- express-validator
- pg
- pg-format
- dotenv
- ejs

### __dirname

`__dirname` is only for commonJS

if `type` is `module` (i.e. using ES Module) in package.json, add this to the top of app.js

```
import path from "path";
import { fileURLToPath } from "url";

const __dirname = path.dirname(fileURLToPath(import.meta.url));
```