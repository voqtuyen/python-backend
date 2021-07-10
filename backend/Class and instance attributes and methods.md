```python

class Person:
  family_name = 'Donald'

  def __init__(self, name, age):
    self._name = name
    self._age = age


######################################################################
# Define instances of Person class
######################################################################
peter = Person(name='Peter', age=30)
louis = Person(name='Louis', age=28)

print('*'*20 + '__dict__' + '*'*20)

# __dict__ A dictionary or other mapping object used to store an object’s (writable) attributes.

"""__dict__ of instances peter, luis do not have family_name, when we access it from instances, it actually get accessed from Person.__dict__['family_name']
"""
print(Person.__dict__)
print(peter.__dict__)
print(louis.__dict__)


######################################################################
# Modify Person class attribute
######################################################################
print('\n')
print('*'*20 + 'Modify class attribute' + '*'*20)
Person.family_name = 'Alexander'
# Validate family_name attributes of class and instances
print(Person.__dict__)
print(Person.family_name)
print('-'*30)
print(peter.family_name)
print(peter.__dict__)
print('-'*30)
print(louis.family_name)
print(louis.__dict__)


######################################################################
# Modify instance attributes
######################################################################
print('\n')
print('*'*20 + 'Modify attribute at instances' + '*'*20)
"""When we assign a new value to family_name at instances, new item is created in __dict__ for each instances to hold the new values for each instance."""
peter.family_name = 'PETER'
louis.family_name = 'LOUIS'

# Validate family_name attributes of class and instances
print(Person.family_name)
print(Person.__dict__)
print(peter.family_name)
print(peter.__dict__)
print(louis.family_name)
print(louis.__dict__)


######################################################################
# Modify Person class attributes
######################################################################
print('\n')
print('*'*20 + 'Modify class attribute again' + '*'*20)
"""Class attribute is changed, but not the instance attributes."""
Person.family_name = 'ALEXANDER'
# Validate family_name attributes of class and instances
print(Person.__dict__)
print(Person.family_name)
print('-'*30)
print(peter.__dict__)
print(peter.family_name)
print('-'*30)
print(louis.__dict__)
print(louis.family_name)

print('\n\n\n\n\n')
######################################################################
# Same experiment except family_name is not a list
######################################################################
print('#'*50)

class Person:
  family_name = ['Donald', 'Alexander']

  def __init__(self, name, age):
    self._name = name
    self._age = age


######################################################################
# Define instances of Person class
######################################################################
peter = Person(name='Peter', age=30)
louis = Person(name='Louis', age=28)

print('*'*20 + '__dict__' + '*'*20)

# __dict__ A dictionary or other mapping object used to store an object’s (writable) attributes.

"""__dict__ of instances peter, luis do not have family_name, when we access it from instances, it actually get accessed from Person.__dict__['family_name']
"""
print(Person.__dict__)
print(peter.__dict__)
print(louis.__dict__)


######################################################################
# Modify Person class attribute
######################################################################
print('\n')
print('*'*20 + 'Modify class attribute' + '*'*20)
Person.family_name.append('Barrack')
# Validate family_name attributes of class and instances
print(Person.__dict__)
print(Person.family_name)
print('-'*30)
print(peter.family_name)
print(peter.__dict__)
print('-'*30)
print(louis.family_name)
print(louis.__dict__)

######################################################################
# Modify instance attributes
######################################################################
print('\n')
print('*'*20 + 'Modify attribute at instances' + '*'*20)
"""Instance attribute now access a reference to the list and modify the list object, thus the changes can be seen at instances and class."""
peter.family_name[0] = 'DONALD'

# Validate family_name attributes of class and instances
print(Person.family_name)
print(Person.__dict__)
print(peter.family_name)
print(peter.__dict__)
print(louis.family_name)
print(louis.__dict__)
```
