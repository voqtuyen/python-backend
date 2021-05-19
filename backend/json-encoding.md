## Description
Sometimes, you see that the output of json.dumps looks like this:
```python3
{"foo": "[{\"bar\": 1}, {\"baz\": 2}]"}
```
This is likely to be caused by double encoding your JSON strings, data is already a JSON string and does not need to be encoded again.
```python3
>>> import json
>>> not_encoded = {"created_at":"Fri Aug 08 11:04:40 +0000 2014"}
>>> encoded_data = json.dumps(not_encoded)
>>> print encoded_data
{"created_at": "Fri Aug 08 11:04:40 +0000 2014"}
>>> double_encode = json.dumps(encoded_data)
>>> print double_encode
"{\"created_at\": \"Fri Aug 08 11:04:40 +0000 2014\"}"
```

## Reference
1. https://stackoverflow.com/questions/25242262/dump-to-json-adds-additional-double-quotes-and-escaping-of-quotes
