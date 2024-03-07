# Cython property converter
Convert properties in Cython extension classes from the deprecated legacy syntax to the decorator syntax.


===  Under construction  ===


Convert from this:
```
    property cheese:
        "A doc string can go here."
        def __get__(self):
            ...
        def __set__(self, value):
            ...
        def __del__(self):
            ...
```
to this:
```
    @property
    def cheese(self):
        "A doc string can go here."
        ...
    @cheese.setter
    def cheese(self, value):
        ...
    @cheese.deleter
    def cheese(self):
        ...
```


<br><br>
Since there cannot be a docstring between the decorator and the def statement, the docstrings will be moved from here:
```
    property cheese:
        "A doc string can go here."
        def __get__(self):
            ...
```
to here:
```
    @property
    def cheese(self):
        "A doc string can go here."
        ...
```


<br><br>
Choose a class declaration syntax

Pure Python
```
@cython.cclass
class Spam:
    @property
    def cheese(self):
```
Cython
```
cdef class Spam:
    @property
    def cheese(self):
```



Indents must not contain both tabs and spaces.

Requires Python 3.10 +

