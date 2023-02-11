# Data Classes

`Dataclasses` are python classes, but are suited for storing data objects. This module provides a decorator and functions for automatically adding generated special methods such as `__init__()` and `__repr__()` to user-defined classes.


## Customize Python dataclass fields with the `field` function

```python
from dataclasses import dataclass, field

class Person:    
    name: str
    age: int 
    city: str
    cash: float = field(default=0, compare=True)
```

These are the most commonly used parameters for `field`:

- `default`- Sets the default value for the field. 
- `default_factory` - Provides the name of a function, which takes no parameters, that returns some object to serve as the default value for the field. 
- `repr` - By default (True), controls if the field in question shows up in the automatically generated __repr__ for the dataclass.
- `compare` - By default (True), includes the field in the comparison methods automatically generated for the dataclass. 


## Controlling Python dataclass initialization


The `__post_init__` method in your dataclass definition, you can provide instructions for modifying fields or other instance data:

```python
from dataclasses import dataclass, field


@dataclass(order=True)
class Person:    
    name: str
    age: int 
    city: str
    cash: float = field(default=0, compare=True)
    
    def __post_init__(self):
        self.sorted_index = self.cash
```

## InitVar

`InitVar` lets you specify a field that will be passed to `__init__` and then to `__post_init__`, but won’t be stored in the class instance.By using `InitVar`, you can take in parameters when setting up the dataclass that are only used during initialization.


## Inheritance

```python

@dataclass
class Student(Person):
    grade: int
    subjects: list
```

