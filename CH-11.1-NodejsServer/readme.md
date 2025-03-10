# Creating a Basic Node.js Server
> Basic Server
```javascript
const http = require('http');
const port = 3000;

const server = http.createServer((req, res) => {
    res.statusCode = 200;
    res.setHeader('Content-Type', 'text/text');
    res.end('Hello World');
});

server.listen(port, () => {
    console.log(`Server running at http://localhost:${port}/`);
});
```

To run this server:
1. Save the code in a file (e.g., `server.js`)
2. Open terminal/command prompt
3. Navigate to the file's directory
4. Run `node server.js`
5. Visit `http://localhost:3000` in your browser

This creates a basic server that:
- Listens on port 3000
- Responds with Hello World to all requests
- serves the content in plain text

### Another example 

```javascript
const http = require('http');
const fs = require('fs');

// Read files synchronously. Ensure these files exist in your working directory.
const homeContent = fs.readFileSync('home.html', 'utf8');
const aboutContent = fs.readFileSync('about.html', 'utf8');
const serviceContent = fs.readFileSync('services.html', 'utf8');

const port = 3000;

const server = http.createServer((req, res) => {

    res.statusCode = 200;
    res.setHeader('Content-type','text/html')

    if (req.url === '/' || req.url === '/home') {
        // res.writeHead(200, { 'Content-Type': 'text/html' });
        res.end(homeContent);
    } else if (req.url === '/about') {
        // res.writeHead(200, { 'Content-Type': 'text/html' });
        res.end(aboutContent);
    } else if (req.url === '/services') {
        // res.writeHead(200, { 'Content-Type': 'text/html' });
        res.end(serviceContent);
    } else {
        res.writeHead(404, { 'Content-Type': 'text/html' });
        res.end('<h1>404 Not Found</h1>');
    }
});

server.listen(port, () => {
    console.log(`Server running at http://localhost:${port}/`);
});
```