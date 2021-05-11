## Problem Statement
Suppose you have a Flask server which exposes an api endpoint `/api/now` to allow users to get the current datetime. Consider the following cases:

- If multiple users from different locations all over the world tries to access this endpoint to get current datetimes, 
will these users get the correct timestamps for their specific locations?
- If this Flask server is deployed at multiple different locations, and the same user tries to get the current datetimes from these servers, 
do you think this user could get the same datetimes?

How do you solve these timezone problems in Python?

## Description
Let's experiment timezone in Python with `datetime` package

```python3
from datetime import datetime
# Return the correct time for your location
print(datetime.now())
# Return the time in the UTC timezone
print(datetime.utcnow())
```
If different users from different locations all over the world run the above code at the same time, `datetime.now()` will always return different results 
for each person, but `datetime.utcnow()` will always return the same time, regardless of the location.

Thus you should always store datetimes in UTC to server database and convert to proper timezone on display. However, the clients which use these datetimes need to convert to their local time. 

## Solution
The solution here is to always store datetimes in UTC and let the conversion from UTC to local timezone happen in the client, using Javascript.

- Datetime storage in database
  ```python3
  created_at = db.Column(db.DateTime, default=datetime.utcnow)
  ```
- Send datetime string to client in ISO format
  ```python3
  created_at.isoformat() + 'Z'
  ```

## Advanced Stuff
Offset-naive and offset-aware datetimes


## Reference
1. https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-xii-dates-and-times
2. https://vinta.ws/code/timezone-in-python-offset-naive-and-offset-aware-datetimes.html
3. https://stackoverflow.com/questions/19654578/python-utc-datetime-objects-iso-format-doesnt-include-z-zulu-or-zero-offset
4. https://julien.danjou.info/python-and-timezones/