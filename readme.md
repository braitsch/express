## @braitsch/express

Simple boilerplate for setting up an Express.js app

**Installation**

`npm i @braitsch/express`

**Usage**

Create two files in your project's root directory: `app.js` to initialize your app using this module and config.js to configure it with project specific settings.

**App.js**

```javascript
const express = require("@braitsch/express");

// create an app //

const app = express();

// enable logging & set log directory //

express.log('./logs');

// enable https (optional) //

express.https(app);

// initialize app //
// 1. path to project root (required)
// 2. app instance (optional)
// 3. database name (optional)
// 4. enable sessions (optional)

express.init(__dirname, app, 'my-database', true);

// start the server //

express.start(app);
```

**Config.js**

```
// add your project specific settings here //

const busboy = require('connect-busboy');

module.exports = function(app) {

	app.locals.cdn = 'https://storage.googleapis.com/braitsch';
	app.use(busboy());
	require(__dirname + '/server/model/database')(app);
	require(__dirname + '/server/routes/public')(app);

// watch and autocompile js/css if running locally

	if (process.env.NODE_ENV == 'localhost') require('./gulpfile').watch();

}
```

