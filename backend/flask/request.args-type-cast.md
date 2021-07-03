# Cast request.args to DateTime type


request.args is a dictionary containing the URL params of the request (the part in the URL after the question mark).
```python
year = request.args.get('year', None, type=int)
```
This allows you to get `year` param and cast it to type `int` if possible. If `year` is not included in the request URL or Flask is unable to cast it to `int` type, None is returned.


However, if you want to cast it to other type, how could you do that?
Because, `args` is `ImmutableMultiDict` and it has a method

```python
get(key, default=None, type=None)
```
If type is provided and is a callable it should convert the value, return it or raise a ValueError if that is not possible.
In this case the function will return the default as if the value was not found

But what is a callable?
A callable is anything that can be called. In other words, a Callable is an object that has the __call__ method

Consider
```python
foo()
```
as syntactic sugar for

```python
foo.__call__()
```

Back to our problem, we could define a function callable.

```python
def to_date(strtime):
    """Convert date string to UTC date in ISO 8601 format."""
    try:
        return datetime.strptime(strtime, '%Y-%m-%d').date()
    except ValueError:
        raise BadRequest(description='Invalid UTC Date in ISO-8601 Format')
```

And utilize this in the same way as before

```python
date = request.args.get('date', None, to_date)
```


## Reference
1. https://flask.palletsprojects.com/en/2.0.x/api/?highlight=request%20args#flask.Request.args  
2. https://werkzeug.palletsprojects.com/en/2.0.x/datastructures/#werkzeug.datastructures.MultiDict  
3. https://stackoverflow.com/a/25292325/8186293  