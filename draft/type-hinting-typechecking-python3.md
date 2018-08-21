
## Type Hinting/Type Checking/Type Enforcement

* An optional feature in python, and even when used is not a strict enforcement.
* Reveals issues when checked with python pip package tool `mypy`
* Helps to do quick unit-tests.
* you can use `typing` module for importing few types

```
#! python3
# filename: test.py

def add_these(a: int, b: int) -> int:
    return a + b
    
add_these(1, 2)
add_these('1', '2')
```

Terminal
``` bash
$ pip install mypy
$ mypy test.py
```
