// JS can be used to fetch data over the internet (AJAX)

// Fetch API (built-in)
let response = fetch(url,[options])

// getting the response is a two stage process
1. An obejct of response is returned with class containg the "Status" and "ok"
>Common HTTP Status Codes:

>1xx - Informational responses
>100: Continue
>102: Processing

>2xx - Successful responses
>200: OK - Request succeeded
>201: Created - Resource created
>204: No Content - Request succeeded but no content returned

>3xx - Redirection messages
>301: Moved Permanently
>302: Found (Temporary Redirect)
>304: Not Modified

>4xx - Client error responses
>400: Bad Request
>401: Unauthorized
>403: Forbidden
>404: Not Found
>429: Too Many Requests

>5xx - Server error responses
>500: Internal Server Error
>502: Bad Gateway
>503: Service Unavailable
>504: Gateway Timeout


Ok -> boolean value

2. After that we need to call another method to acces the body in diffrent format

response.text() -> returns the text
response.json() -> return the json object

there are also other methods like reponse.blob(), .formdata(), .arraybuffer()....
But only one of them will work, after that we can't apply another response.<anyFunc>()

### Response Header -> jo humko API deta h
response.headers()

### Request Header -> jo hum API ko dete h
let response = fetch(url, {
    headers: {
        'Content-Type': 'application/json',
        'Authorization': 'Bearer YOUR_ACCESS_TOKEN',
        'Accept': 'application/json'
    }
})

<!-- Exaple with promise -->
<!-- Example of fetch with POST method using promises -->

```javascript
let response = await fetch('https://api.example.com/data', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
    },
    body: JSON.stringify({
        title: 'Example Post',
        body: 'This is a post request example',
        userId: 1
    })
});

let result = await response.json();
```

JSON.stringify -> The fetch() API requires the request body to be in string format or specific data formats like FormData, Blob, ArrayBuffer, etc. It cannot directly accept JavaScript objects.


