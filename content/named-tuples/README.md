# Named Tuples

`Named tuple` container datatype is an alternative to the built-in `tuple`. This extension type enhances standard `tuples` so that their elements can be accessed by both **their attribute name and the positional index**.

`Named tuples` are available in Python’s standard library collections module under the namedtuple utility.

```python
from collections import namedtuple

Employee = namedtuple(
  'Employee',
  ['first_name', 'last_name', 'country', 'jobs']
)

andrew = Employee('Andrew', 'Brown', 'US', ['Developer', 'Manager'])
print(andrew)

# Employee(first_name='Andrew', last_name='Brown', country='US', jobs=['Developer', 'Manager'])
```

You can access the elements in the named tuples through their attributes or positions

```python
# Access by index
print((andrew[0], andrew[2]))
# ('Andrew', 'US')

# Access by named attributes
print((andrew.first_name, andrew.country))
# ('Andrew', 'US')
```

`Named Tuple`s are very useful in context where we need to create a data structure that can be accessed by **both the positional index and the named attribute of the elements**.

## More Operations with Named Tuples

When converted to dictionaries, named tuples can also support key lookup. `_as_dict()` method will return an `OrderedDict()` where keys are the attributes of the `named tuple`. 


```python
employee = andrew._asdict()

print(employee)
# OrderedDict([('first_name', 'Andrew'), ('last_name', 'Brown'), ('country', 'US'), ('jobs', ['Developer', 'Manager'])])

# Key-based operations
print(employee['first_name'], employee['jobs'])
# Andrew, ['Developer', 'Manager']
```
## Iterable

`Named tuples` are iterable too. Iterables in Pyhton implement `__iter__` and return an iterator that is capable of returning one element of its members at a time.

```python
for attr in andrew: 
  print(attr)
  
# Andrew
# Brown
# US
# ['Developer', 'Manager']
```
## Unpacking

Additionally, `named tuples` support unpacking tuple assignment.

```python
# Unpacking named attributes using tuple assignment
first_name, last_name, country, jobs = andrew
```
## Repr

`Named tuples` also provide by default a readable `__repr__` that denotes the typename of the tuple along with its key-value attributes:
```python
>>> andrew
Employee(first_name='Andrew', last_name='Brown', country='US', jobs=['Developer', 'Manager'])
```

## Typing 

You can use `typing package offers `typing.NamedTuple` which is a typed version of `collections.namedtuple`.

```python
class Employee(typing.NamedTuple):
    first_name: str
    last_name: str
    country: str
    jobs: list
```


## Conclusion 

`Named tuples` are usually useful when we need to build data structures that can be accessed both by positional indices or attribute names. They are also `immutable` which means that their elements cannot be changed in-place.
