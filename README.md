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
