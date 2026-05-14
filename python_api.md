This example shows how Python’s Requests library is used to call a REST API.

```python
r = requests.get('https://api.github.com/user', auth=('user', 'pass'))
```

* Sends a GET request to the [GitHub API](https://api.github.com?utm_source=chatgpt.com)
* `auth=('user', 'pass')` sends username and password for authentication.
* The response is stored in variable `r`.

```python
r.status_code
200
```

* `200` means the request was successful.

```python
r.headers['content-type']
'application/json; charset=utf8'
```

* Shows the response type is JSON data encoded in UTF-8.

```python
r.encoding
'utf-8'
```

* Tells how the response text is encoded.

```python
r.text
'{"type":"User"...'
```

* Returns the response as a plain string.

```python
r.json()
{'private_gists': 419, 'total_private_repos': 77, ...}
```

* Converts the JSON response into a Python dictionary so data can be accessed easily.
`res.headers` is used to get the response headers returned by the server after making an API request.

Headers contain extra information about the response, like:

* content type
* server details
* authentication info
* caching rules

Example:

```python
import requests

res = requests.get("https://api.github.com")

print(res.headers)
```

Output may look like:

```python
{
  'Content-Type': 'application/json',
  'Server': 'GitHub.com',
  'Content-Length': '5262'
}
```

Access a specific header:

```python
print(res.headers['Content-Type'])
```

This tells the response data format, such as JSON, HTML, etc.
