# Introduction to Using APIs

APIs (Application Programming Interfaces) allow different software systems to
communicate with each other. They define a set of rules and endpoints that a
client (your script, app, or browser) can use to request data or trigger
actions on a server.

APIs are commonly used to:
- Retrieve data (weather, stock prices, user profiles, etc.)
- Send data (form submissions, uploads)
- Control services (start a job, send a message)
- Integrate external services into your own applications

Most modern APIs use HTTP and return data in JSON format.


## Basic Structure of an API Call

A typical API call includes:
- Endpoint: the URL
- Method: GET, POST, PUT, DELETE
- Headers: metadata (like Content-Type or Authorization)
- Body: data sent with POST/PUT requests

Example endpoint: `GET https://api.example.com/v1/users`

## Example 1 - Using cURL (Command Line)
GET example:
```sh
curl -X GET "https://api.example.com/v1/weather?city=London" \
  -H "Authorization: Bearer YOUR_API_KEY"
```
POST example:
```sh
curl -X POST "https://api.example.com/v1/messages" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{"message": "Hello API!"}'
```


## Example 2 - Using Python (requests)
GET example:
```py
import requests

url = "https://api.example.com/v1/weather"
params = {"city": "London"}
headers = {"Authorization": "Bearer YOUR_API_KEY"}

response = requests.get(url, params=params, headers=headers)
data = response.json()

print("Temperature:", data["temperature"])
```
POST example:
```py
import requests

url = "https://api.example.com/v1/messages"
payload = {"message": "Hello API!"}
headers = {
    "Content-Type": "application/json",
    "Authorization": "Bearer YOUR_API_KEY",
}

response = requests.post(url, json=payload, headers=headers)
print(response.json())
```

## Example 3 - Using JavaScript (Node.js / fetch)
GET example:
```js
import fetch from "node-fetch";

const url = "https://api.example.com/v1/weather?city=London";

const response = await fetch(url, {
  method: "GET",
  headers: {
    "Authorization": "Bearer YOUR_API_KEY"
  }
});

const data = await response.json();
console.log("Weather:", data);
```

POST example:
```js
import fetch from "node-fetch";

const response = await fetch("https://api.example.com/v1/messages", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
    "Authorization": "Bearer YOUR_API_KEY"
  },
  body: JSON.stringify({ message: "Hello API!" })
});

console.log(await response.json());
```
