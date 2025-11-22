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

### multer

req.file object 
```
{
  fieldname: 'uploaded_file',
  originalname: 'p04-icon-teru_teru_bozu.gif',
  encoding: '7bit',
  mimetype: 'image/gif',
  destination: './public/uploads/',
  filename: '9b6d8cb5d83c270624d13b8c8d1d11f2',
  path: 'public/uploads/9b6d8cb5d83c270624d13b8c8d1d11f2',
  size: 171
}
```

## deployment on cloudpanel

[https://www.cloudpanel.io/docs/v2/nodejs/deployment/pm2/](https://www.cloudpanel.io/docs/v2/nodejs/deployment/pm2/)