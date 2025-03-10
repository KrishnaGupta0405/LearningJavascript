# JavaScript Callbacks and Promises

## Callbacks
1.  A callback function is a function that is passed as an argument to another function, commonly used in asynchronous operations like handling API responses, event handling, reading files etc.
2. and is executed after the main function has finished its execution.

```javascript
function loadscript(src, callback) {
    let script = document.createElement("script");
    script.src = src;
    script.onload = () => {
        callback(script);
    }
}
loadscript("https://cdn.harry.com", (script) => {
    alert("script loaded ");
    alert(script.src);
});
```

### Handling Errors in Callbacks

```javascript
function loadscript(src, callback) {
    let script = document.createElement("script");
    script.src = src;
    script.onload = () => {
        callback(null, script);
    }
    script.onerror = () => {
        callback(new Error("failed to load script"), null);
    }
}
loadscript("https://cdn.harry.com", (error, script) => {
    if(error) {
        console.log("The error->", error);
    }
    else {
        console.log("The script->", script);
    }
});
```

---

## Promises

Pyramid of Doom / Callback Hell,
Solution to callback hell is Promises, also used in parallel execution of code.


```javascript
let promise = new Promise((resolve, reject) => {
    // ...
});
promise.then((value) => {...})
        .catch((error) => {...});
```

Resolve and reject are the two parameters of the Promise constructor:
- Resolve is used to resolve the Promise, which is followed as `.then()` method
- Reject is used to reject the Promise, which is followed as `.catch()` method

### Creating Promises

```javascript

let promise2 = new promise((resolve,reject)=>{
    setTimeout(resolve("Promise Resovled Successfully"),3000)
});

// Or using arrow fucntion

let promise2 = new Promise((resolve, reject) => {
    setTimeout(() => resolve("Promise Resolved Successfully"), 3000);
});

```
### We can attach multiple handlers, each runs independently
```javascript
promise2.then(console.log("First handler"));
promise2.then(console.log("Second handler"));
promise2.then(console.log("Third handler"));
```

---

## Promise API- 6 static methods are-> 

### Promise.all()

Waits for all promises to resolve and returns array of results. If any promise rejects, Promise.all rejects immediately with that error.

```javascript
let promise_all = Promise.all([
    new Promise(resolve => setTimeout(() => resolve(1), 3000)),
    new Promise(resolve => setTimeout(() => resolve(2), 2000)),
    new Promise(resolve => setTimeout(() => resolve(3), 1000))
]).then(console.log); // [1,2,3] after 3 seconds
```

### Promise.allSettled()

Waits for all promises to settle and returns array of their results. Contains both fulfilled and rejected promises.

```javascript
let promise_allSettled = Promise.allSettled([
    Promise.resolve(1),
    Promise.reject(new Error('Error')),
    Promise.resolve(3)
]).then(console.log); 
// [{status:"fulfilled", value:1}, {status:"rejected", reason:Error}, {status:"fulfilled", value:3}]
```

### Promise.race()

Waits for first promise only to settle and returns its result. Can be either resolved value or rejection error.

```javascript
let promise_race = Promise.race([
    new Promise(resolve => setTimeout(() => resolve(1), 3000)),
    new Promise(resolve => setTimeout(() => resolve(2), 2000)),
    new Promise(resolve => setTimeout(() => resolve(3), 1000))
]).then(console.log); // 3 (after 1 second)
```

### Promise.any()

Waits for first promise to fulfill and returns its result. Ignores rejections, waits for first success.

```javascript
let promise_any = Promise.any([
    Promise.reject(new Error('Error')),
    new Promise(resolve => setTimeout(() => resolve(1), 3000)),
    new Promise(resolve => setTimeout(() => resolve(2), 2000))
]).then(console.log); // 2 (after 2 seconds)
```

### Promise.resolve() and Promise.reject()

Create resolved or rejected promises with a given value or error.

```javascript
let promise_resolve = Promise.resolve("Success").then(console.log); // "Success"

let promise_reject = Promise.reject(new Error("Failed"))
    .catch(error => console.log(error.message)); // "Failed"
``` 