@braitsch/express

Simple boilerplate for setting up an Express.js app

```javascript
const express = require("@braitsch/express");

// create app //

const app = express();

// enable logging & set log directory //

express.log('./logs');

// create a server //

express.createServer(app);

// initialize app //
1. path to project root (required)
2. app instance (optional)
2. database name (optional)
2. enable sessions (optional)

express.init(__dirname, app, 'my-database', true);

// start the server //

express.startServer(app);
```

