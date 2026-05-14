````md
# Python Requests API Example Explanation

This Python script uses the `requests` library to fetch user data from a REST API and save the response into a JSON file.
````

```python
import requests

url = 'https://fake-json-api.mock.beeceptor.com/users'
res = requests.get(url)

print(res.headers['Content-Type'])
print(res.headers)
if res.status_code != 200:
    raise Exception('API call failed with status code: {}'.format(res.status_code))
# print(type(res.text))
# print(type(res.json()))
# print(res.json())
for index ,i  in enumerate(res.json(),start=1):
    # print(f"{index} : {i['name']}")
     pass
with open('index.json','w') as f:
    f.write(res.text)
````

The `requests` module is imported to send HTTP requests like GET, POST, PUT, and DELETE in Python.

```python
url = 'https://fake-json-api.mock.beeceptor.com/users'
res = requests.get(url)
```

A URL is stored in the `url` variable.
`requests.get(url)` sends an HTTP GET request to the API endpoint and stores the server response in the `res` variable.

```python
print(res.headers['Content-Type'])
print(res.headers)
```

`res.headers` contains metadata returned by the server, such as content type, server details, encoding, and caching information.

`res.headers['Content-Type']` prints the response format, for example:

```python
application/json
```

This means the API response data is in JSON format.

```python
if res.status_code != 200:
    raise Exception('API call failed with status code: {}'.format(res.status_code))
```

`res.status_code` checks whether the API request was successful.

* `200` means success
* `404` means not found
* `500` means server error

If the status code is not `200`, the script raises an exception with an error message.

```python
# print(type(res.text))
# print(type(res.json()))
# print(res.json())
```

These commented lines are used for debugging and understanding the response.

* `res.text` returns response data as a string
* `res.json()` converts JSON response into Python objects like list or dictionary

```python
for index ,i  in enumerate(res.json(),start=1):
    # print(f"{index} : {i['name']}")
     pass
```

`res.json()` returns a list of user objects from the API.

`enumerate(..., start=1)` is used to loop through the list with numbering starting from 1.

Example:

```python
1 : John Doe
2 : Alice
```

Currently, `pass` does nothing because the print statement is commented out.

```python
with open('index.json','w') as f:
    f.write(res.text)
```

This block creates a file named `index.json` in write mode (`w`).

`f.write(res.text)` writes the API response into the file as plain JSON text.

The `with open()` statement automatically closes the file after writing.

```
```
