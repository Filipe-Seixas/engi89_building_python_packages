# Building Python Packages
## What is a Python Package and benefits
### Structure

- Step 1: `create an app folder`
- Step 2: inside app folder`__init__.py` empty
- Step 3: inside app folder `fizzbuzz.py` and `calculator.py`
- Step 4: `program.py` on dir level - to use as our run file
- Step 5: `setup.py` on a dir level - to describe our module details such as version, author, contact details

```
building_python_packages (directory structure)
/app
  --> __init__.py
  --> fizzbuzz.py
  --> calculator.py
program.py
setup.py
```

- Start building the package starting with `setup.py`
```python
from setuptools import setup

# Let's add some information about your package
setup(name="app")
version = "1.0"
description = "Python app"
author = "Filipe Seixas"
author_email = "abc@cba.com"
url = "https://spartaglobal.com"
```
- Code for `fizzbuzz.py`
```python
class Fizzbuzz:

    def __init__(self, start_of_range, end_of_range):
        self.fizzrange = range(start_of_range, end_of_range)
        self.fizzbuzz_list = []
        self._fizzbuzz_iterator()

    def _divisible_by(self, num1, num2):
        if num1 % num2 == 0:
            return True
        else:
            return False

    def _fizzbuzz_iterator(self):

        for num in self.fizzrange:
            if self._divisible_by(num, 15):
                self.fizzbuzz_list.append("fizzbuzz")
            elif self._divisible_by(num, 5):
                self.fizzbuzz_list.append("buzz")
            elif self._divisible_by(num, 3):
                self.fizzbuzz_list.append("fizz")
            else:
                self.fizzbuzz_list.append(num)
```
- Code for `calculator.py`
```python
class Calculator:

    def Add(self, num1, num2):
        return num1 + num2

    def Subtract(self, num1, num2):
        return num1 - num2

    def Multiply(self, num1, num2):
        return num1 * num2

    def Divide(self, num1, num2):
        return num1 / num2
```
- Code for `program.py`
```python
from app.fizzbuzz import Fizzbuzz
from app.calculator import Calculator

one_to_100 = Fizzbuzz(1, 100)
print(one_to_100.fizzbuzz_list)

five_plus_ten = Calculator()
print(five_plus_ten.Add(5, 10))
```
- `pip install .` to install our package using the `pip` package manager