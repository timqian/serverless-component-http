# http-component

Deploy any Node.js http server serverlessly to Tencent Cloud. Use any framework you like - Vanilla HTTP server, express, koa, apollo-server...

## Quick Start

### 1. Install Serverless Framework:

```bash
npm i serverless -g
```

### 2. Write you server

Code structure
```
|- app.js
|- serverless.yml
```

```js
// app.js
const http = require('http');

http
  .createServer((req, res) => {
    res.end('Hello World\n')
  })
  .listen(8080);

// The only thing required is to export your server in the entryFile
module.exports = http;
```

```yml
# serverless.yml
component: http
name: test

inputs:
  src: ./
  entryFile: app.js
  region: ap-guangzhou
  domain: slite.dev
```

### 3. deployment

```bash
serverless deploy
```