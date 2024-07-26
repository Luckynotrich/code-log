```sh
npm init -y
```

```sh
npm i express
```

```sh
npm i typescript -D
```

```sh
npm i -D @types/node
```

`tsconfig.json`
```json
{
"compilerOptions": {
	"module": "nodenext",
	"moduleResolution": "nodenext",
	"target": "ESNext",
	"sourceMap": true,
	"outDir": "dist",
	"types": ["node","express"],
},
"include":[
	"src/**/*.ts"
	],
"exclude": [
	"./dist/",
	"node_modules/*"
	]
}
```

```js
import express from 'express';
import {join} from 'path';
import dotenv from 'dotenv';
dotenv.config();
const app = express();
app.use(express.static(join(import.meta.dirname,'./dist')));
app.get('/*', (req, res) => {
    //ES module syntax
    const rootFile: string = join(process.env.rootDir,"/dist/index.html");
    res.sendFile(rootFile);
  });
  const PORT = process.env.PORT || 8081
  app.listen(PORT, () => {
    console.log(`Server started on ${PORT}`)
  });

```

package.json
```json
{
  "name": "green-coast",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "type": "module",
  "scripts": {
    "tsc": "npx tsc -w ./src/index.ts",
    "watch": "nodemon ./dist/index.js",
    "dev": "run-p tsc watch"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.19.2"
  },
  "devDependencies": {
    "@types/express": "^4.17.21",
    "@types/node": "^20.14.10",
    "dotenv": "^16.4.5",
    "nodemon": "^3.1.4",
    "npm-run-all": "^4.1.5",
    "typescript": "^5.5.3"
  }
}
```