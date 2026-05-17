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
