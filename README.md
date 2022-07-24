# express-generator to typescript sample

https://github.com/expressjs/generator

## Action

### 1.create project

```
npm install -g pnpm
pnpx express-generator --git express-generator-to-typescript-sample

cd express-generator-to-typescript-sample

rem git init
rem git add .
rem git commit -m "init project"
```

### 2.config typescript

```
pnpm install typescript
pnpm tsc --init

pnpm install -D @types/node
pnpm install -D @types/express
pnpm install ts-node
pnpm install -D ts-node-dev

pnpm install

mkdir src
mkdir src\routes

move routes\index.js src\routes\index.ts
move routes\users.js src\routes\users.ts
move app.js src\app.ts
move bin\www src\main.ts

rmdir bin
rmdir routes

echo build/ >> .gitignore

rem git add .
rem git commit -m "init typescript"
```

### 3.config typescript

Edit package.json.
```
  "scripts": {
    "start": "node ./build/main.js",
    "debug": "ts-node-dev ./src/main.ts",
    "build": "tsc"
  },
```

Edit tsconfig.json.
```
    "rootDir": "./src/",
    "baseUrl": "./src/",
    "outDir": "./build/",
```

Edit require to import.
* src/app.ts
* src/routes/index.ts
* src/routes/users.ts

```
import express = require('express');
``` 

edit require path in src/main.ts.

```
//var app = require('../app');
var app = require('./app');
```

edit view setting in app.ts.
```
// view engine setup
//app.set('views', path.join(__dirname, 'views'));
app.use(express.static(path.join(__dirname, 'public')));
```

### 4.test server

Build and start express.

```
pnpm build && pnpm start
```

Open http://localhost:3000/ in browser.

## Command

```
pnpm start     # start express server for javascript.
pnpm debug     # start express server for typescript in development.
pnpm build     # build typescript.
```
