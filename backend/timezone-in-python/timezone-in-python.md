## Problem Statement
Suppose you have a Flask server which expose an api endpoint `/api/now` to return the current timestamp. Consider the following cases:

- If multiple users from all over the world tries to access this endpoint to get current timestamps, 
do these users get the correct timestamps for their locations?
- If this Flask server is deployed at multiple different locations, and the same user tries to get the current timestamp from these servers, 
do you think this user could get the same timestamps?

How do you solve this timezone problem in Python?

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


## Solution





## Reference
1. https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-xii-dates-and-times
2. https://vinta.ws/code/timezone-in-python-offset-naive-and-offset-aware-datetimes.html
