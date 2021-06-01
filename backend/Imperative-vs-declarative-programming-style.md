# Imperative and Declarative Programming Style

Given the problem:
```python3
passwords = [
   "123456",
   "password",
   "admin",
   "freecodecamp",
   "mypassword123",
]
```
We want to reject the user to sign up with a password less than 9 characters long.


## Imperative Programming Style
Imperative programming is like how you do something.

```python3
long_passwords = []
for pw in passwords:
   if len(pw) >= 9:
     long_passwords.append(pw)
```


## Declarative Programming Syle
Declarative programming is more like what you do.

```python3
long_passwords = filter(lambda x: len(x) >= 9, passwords)
```
