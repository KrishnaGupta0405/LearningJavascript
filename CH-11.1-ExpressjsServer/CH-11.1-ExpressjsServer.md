## Expressjs

```shell
npm install express@latest
npm install nodemon --save-dev
npm i nodemon --global
```
*nodemon restarts the server automatically when some changes as saved*

---

## Basic server in Express.js

```javascript
const express = require('express');
const app = express();
const port = 80;

app.get('/', (req, res) => {
    res.send('Hello from Express!');
});

app.listen(port, () => {
    console.log(`Server running at http://localhost:${port}`);
});
```
to run this file 
1. npm install express@latest
2. node CH-11.1-ExpressjsServer.js

### More comprehensive server with Express.js
```javascript
const express = require('express');
const fs = require('fs');
const app = express();
const port = 3000;

// Read files synchronously. Ensure these files exist in your working directory.
const homeContent = fs.readFileSync('home.html', 'utf8');
const aboutContent = fs.readFileSync('about.html', 'utf8');
const serviceContent = fs.readFileSync('services.html', 'utf8');

app.get(['/', '/home'], (req, res) => {
    res.status(200).contentType('text/html').send(homeContent);
});

app.get('/about', (req, res) => {
    res.status(200).contentType('text/html').send(aboutContent);
});

app.get('/services', (req, res) => {
    res.status(200).contentType('text/html').send(serviceContent);
});

// If no route matches, return a 404 error.
app.use((req, res) => {
    res.status(404).contentType('text/html').send('<h1>404 Not Found</h1>');
});

app.listen(port, () => {
    console.log(`Server running at http://localhost:${port}/`);
});
```

### Simple exaple about html in Express.js
```javascript
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
    res.send(`
        <html>
            <head>
                <title>Simple Inline HTML</title>
            </head>
            <body>
                <h1>Hello from Express!</h1>
                <p>This HTML is written directly in the server file.</p>
            </body>
        </html>
    `);
});

app.listen(port, () => {
    console.log(`Server running at http://localhost:${port}`);
});
```