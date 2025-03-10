## Try-Catch Block
```javascript
try{
    // ...
}
catch(error){
    // ...
}
finally{
    // ...
}
```

---


# JavaScript Async/Await

## Async Functions
1. functions are a modern way to handle asynchronous operations in JavaScript
2. They allow us to write asynchronous code that looks like synchronous code
3. Async functions return promises !!!! , which means that theycan be handled using .then() or await

```javascript
async function harry() {
    console.log("I am harry");
}
harry().then(() => {
    console.log("and i am resolved");
});
```

---

## Await Keyword
1. Await-> It is used to wait for a promise to resolve or reject
2. It can only be used inside async functions
3. It is just an elegant syntax of getting the promise and then then result + its easie to read and write

```javascript
async function getData() {
    let p1 = new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve("Data fetched successfully!");
        }, 2000);
    });

    console.log("Fetching data...");
    let result = await p1;
    console.log(result);
}

getData();
console.log("This will print before data is fetched");
``` 