## Cookie are the small string of data, directly stored in the browser
#### cookie are set by a web server using the set-cookie HTTP-header
#### So that the nest time you visit the same domain your browser will send the cookie to the server so that the server will know who send the request

```javascript
alert(document.cookie)  //It contains the key=value pair delimited by a
```

## Writing a cookie
```javascript
document.cookie = "user= Harry", "Password = 123abc@"
```
is user = harry exits, it will re-write the exiting one

## encodeURIComponent
- Used to encode special characters in URLs and cookies
- Ensures values with spaces, symbols etc. are properly formatted
- Important when storing data that may contain special characters

```javascript
let cookie = "name=John Smith; location=São Paulo";
document.cookie = encodeURIComponent(cookie);
// Result: name%3DJohn%20Smith%3B%20location%3DS%C3%A3o%20Paulo

let decodedCookie = decodeURIComponent(document.cookie);
console.log("Decoded Cookie: ", decodedCookie);

// Split and read the cookies manually (optional)
let allCookies = decodedCookie.split("; ");
allCookies.forEach(cookie => {
    console.log("Individual Cookie: ", cookie);
});

// Set a new cookie with an expiry date
document.cookie = "age=25; expires=Fri, 31 Dec 2025 23:59:59 GMT";
document.cookie = "city=New York; expires=Fri, 31 Dec 2025 23:59:59 GMT";

console.log("All Cookies Now: ", document.cookie);
```

### Note -> 
1. Total length of the cookie should not exceed 4kb
2. The total no. of cookie per domain is limited to 20+ only (Exactly browser dependent)

## LocalStorage 
Both the key and the value should of format string only, stays in the browser evem when the browser or the domain is closed

```javascript
// .setItem()
localStorage.setItem("username", "JohnDoe");
// .getItem
let user = localStorage.getItem("username");
// .clear()
localStorage.clear();
// .key
let firstKey = localStorage.key(0);
// .length
let totalItems = localStorage.length;
``` 

## SesionStorgae- 
all the functions are same as the localStorage, but it remains in the bowser till the domain is open

## Json 

```javascript
json.stringfy(object);
jsong.parse(string)
```
