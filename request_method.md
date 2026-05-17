# HTTP Methods in Python `requests`

```python
import requests

r = requests.put(
    'https://httpbin.org/put',
    data={'key': 'value'}
)

r = requests.delete(
    'https://httpbin.org/delete'
)

r = requests.head(
    'https://httpbin.org/get'
)

r = requests.options(
    'https://httpbin.org/get'
)
```

---

# 1. PUT Request

```python
r = requests.put(
    'https://httpbin.org/put',
    data={'key': 'value'}
)
```

## Purpose

Used to **update** or **replace** data on the server.

## Data Sent

```python
{'key': 'value'}
```

## Internally Sends

```http
PUT /put HTTP/1.1

key=value
```

## Common Use Cases

* Update user profile
* Replace database record
* Update settings

## Response Example

```python
print(r.json())
```

```json
{
  "form": {
    "key": "value"
  }
}
```

---

# 2. DELETE Request

```python
r = requests.delete(
    'https://httpbin.org/delete'
)
```

## Purpose

Used to **remove/delete** a resource from server.

## Real Example

```http
DELETE /users/5
```

Means:

> Delete user with ID 5

## Common Use Cases

* Delete account
* Remove post
* Delete file

## Response Example

```python
print(r.status_code)
```

```python
200
```

---

# 3. HEAD Request

```python
r = requests.head(
    'https://httpbin.org/get'
)
```

## Purpose

Gets only **headers**, not response body.

## Useful For

* Check content type
* Check server status
* Check file size
* Verify resource exists

## Example

```python
print(r.headers)
```

## Important

```python
print(r.text)
```

returns empty output because HEAD does not return body content.

---

# 4. OPTIONS Request

```python
r = requests.options(
    'https://httpbin.org/get'
)
```

## Purpose

Checks which HTTP methods are allowed.

## Example

```python
print(r.headers['Allow'])
```

Possible Output:

```python
GET, HEAD, OPTIONS
```

Meaning server supports:

* GET
* HEAD
* OPTIONS

---

# HTTP Methods Summary

| Method  | Purpose             |
| ------- | ------------------- |
| GET     | Retrieve data       |
| POST    | Create/send data    |
| PUT     | Update/replace data |
| PATCH   | Partial update      |
| DELETE  | Remove data         |
| HEAD    | Headers only        |
| OPTIONS | Allowed methods     |

---

# Response Object (`r`)

Every request returns a Response object.

## Useful Attributes

```python
r.status_code
r.text
r.json()
r.headers
```

## Example

```python
print(r.status_code)
```

Output:

```python
200
```

Meaning:

> Request successful

---

# About `httpbin.org`

`httpbin.org` is a free API testing service.

It helps you:

* test HTTP requests
* inspect sent data
* learn APIs safely

Very useful while learning Python `requests`.


# HTTP Methods Explained Fully

HTTP methods are actions used by a client (browser/app/Python script) to communicate with a server.

Think of a server like a database or website backend.

Different HTTP methods tell the server what action to perform.

---

# 1. GET → Retrieve Data

## Purpose

Used to fetch/read data from the server.

## Real-Life Example

When you open:

```text
https://api.example.com/users
```

your browser sends a:

```http
GET /users
```

request.

The server responds with data.

---

## Python Example

```python id="sbrxtp"
import requests

r = requests.get('https://jsonplaceholder.typicode.com/users')

print(r.json())
```

---

## Characteristics

| Feature              | Value      |
| -------------------- | ---------- |
| Sends Data?          | Usually No |
| Receives Data?       | Yes        |
| Changes Server Data? | No         |
| Safe?                | Yes        |

---

## Common Uses

* Fetch users
* Load webpage
* Read products
* Search results

---

# 2. POST → Create / Send Data

## Purpose

Used to send new data to the server.

Usually creates a new resource.

---

## Real-Life Example

Creating a new account:

```http
POST /users
```

with data:

```json
{
  "name": "Aman"
}
```

Server stores new user.

---

## Python Example

```python id="6gudta"
import requests

data = {
    'name': 'Aman',
    'age': 21
}

r = requests.post(
    'https://httpbin.org/post',
    data=data
)

print(r.json())
```

---

## Characteristics

| Feature              | Value |
| -------------------- | ----- |
| Sends Data?          | Yes   |
| Receives Data?       | Yes   |
| Changes Server Data? | Yes   |
| Safe?                | No    |

---

## Common Uses

* Login forms
* Register account
* Upload file
* Submit form

---

# 3. PUT → Update / Replace Data

## Purpose

Used to completely replace existing data.

---

## Real-Life Example

Existing user:

```json
{
  "name": "Aman",
  "age": 20
}
```

PUT request:

```json
{
  "name": "Aman",
  "age": 21
}
```

Old data gets replaced.

---

## Python Example

```python id="s9zh8s"
import requests

data = {
    'name': 'Aman',
    'age': 21
}

r = requests.put(
    'https://httpbin.org/put',
    data=data
)

print(r.json())
```

---

## Characteristics

| Feature              | Value |
| -------------------- | ----- |
| Sends Data?          | Yes   |
| Receives Data?       | Yes   |
| Changes Server Data? | Yes   |

---

## Common Uses

* Update profile
* Replace document
* Update settings

---

# 4. PATCH → Partial Update

## Purpose

Updates only specific fields.

Unlike PUT, PATCH does NOT replace everything.

---

## Example

Existing user:

```json
{
  "name": "Aman",
  "age": 20,
  "city": "Mumbai"
}
```

PATCH request:

```json
{
  "age": 21
}
```

Only age changes.

Other fields remain same.

---

## Python Example

```python id="2oxcc4"
import requests

data = {
    'age': 21
}

r = requests.patch(
    'https://httpbin.org/patch',
    data=data
)

print(r.json())
```

---

## Difference Between PUT and PATCH

| PUT                 | PATCH                     |
| ------------------- | ------------------------- |
| Replaces full data  | Updates partial data      |
| Sends entire object | Sends changed fields only |

---

# 5. DELETE → Remove Data

## Purpose

Deletes resource from server.

---

## Real-Life Example

```http
DELETE /users/5
```

Means:

> Delete user with ID 5

---

## Python Example

```python id="lq9c8y"
import requests

r = requests.delete(
    'https://httpbin.org/delete'
)

print(r.status_code)
```

---

## Characteristics

| Feature       | Value     |
| ------------- | --------- |
| Sends Data?   | Sometimes |
| Removes Data? | Yes       |

---

## Common Uses

* Delete account
* Remove product
* Delete comment

---

# 6. HEAD → Headers Only

## Purpose

Same as GET but returns only headers.

No response body/content.

---

## Why Useful?

You can check:

* file size
* content type
* server status
* last modified date

without downloading full content.

---

## Python Example

```python id="k2ldd9"
import requests

r = requests.head(
    'https://httpbin.org/get'
)

print(r.headers)
```

---

## Important

```python id="q3mjlwm"
print(r.text)
```

returns empty output.

Because HEAD returns no body.

---

# 7. OPTIONS → Allowed Methods

## Purpose

Checks what operations server supports.

---

## Example

```http
OPTIONS /users
```

Server may reply:

```text
GET, POST, PUT, DELETE
```

---

## Python Example

```python id="nqj4ee"
import requests

r = requests.options(
    'https://httpbin.org/get'
)

print(r.headers['Allow'])
```

---

# Complete HTTP Flow

## Example: Instagram App

| Action            | HTTP Method |
| ----------------- | ----------- |
| Open feed         | GET         |
| Create post       | POST        |
| Edit profile      | PUT/PATCH   |
| Delete comment    | DELETE      |
| Check image info  | HEAD        |
| Check API support | OPTIONS     |

---

# Visual Understanding

```text
Client (Browser/Python)
        |
        | HTTP Request
        v
Server/API
        |
        | HTTP Response
        v
Client Receives Data
```

---

# Status Codes

| Code | Meaning      |
| ---- | ------------ |
| 200  | Success      |
| 201  | Created      |
| 400  | Bad Request  |
| 401  | Unauthorized |
| 404  | Not Found    |
| 500  | Server Error |

---

# Summary Table

| Method  | Main Purpose     |
| ------- | ---------------- |
| GET     | Read data        |
| POST    | Create/send data |
| PUT     | Replace data     |
| PATCH   | Partial update   |
| DELETE  | Remove data      |
| HEAD    | Headers only     |
| OPTIONS | Allowed methods  |

---

# Easy Memory Trick

| Method  | Think Like         |
| ------- | ------------------ |
| GET     | "Give me data"     |
| POST    | "Create this"      |
| PUT     | "Replace this"     |
| PATCH   | "Change this part" |
| DELETE  | "Remove this"      |
| HEAD    | "Show info only"   |
| OPTIONS | "What can I do?"   |

