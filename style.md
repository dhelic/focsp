# FoCSP Style Guide

## Background
Two of the most important qualities of good code are readability and understandability. Thus, in addition to the functionality of your submitted code, the adherance to certain style rules and general cleanliness of code will be graded. In each assignment, a given amount of points is allocated for these matters. For each violation, a certain amount of points will be detucted from a maximum of the allocated points. This means, if 5 points are allocated for code quality, you can't lose more than 5 points due to these violations.

In general, we encourage you to follow the rules and guidelines from *PEP8*, the style guide created by the people who develop python ([pep8.org](https://pep8.org/)). We will not enforce every detail contained in PEP8, but put special emphasis on certain aspects of it.

To facilitate following the guidelines from PEP8, people created so called *linters* (e.g. *pylint*). They will check your code and warn you about all PEP8-infringements. Most IDEs also allow continuous linting. Keep in mind that a linter will not check for all rules that apply in this course!


## Python Style Rules


### Line length
The maximum line length is *120 characters* - **including indentation and comments**. Occasional minor violations of this rule are fine, but use common sense ;) Make use of pythons implied line continuation inside brackets.
```python=3.10
# No: 
something(foo: int, bar: str, very_long_argument: str, method=print, color="red", funny_number: int = 1337) -> List[int]:
# No: 
x = "a very long long loooong long long loong over the maximum of 120 characters long string that does not reveal any particular new information"

# Yes: 
something(foo: int, bar: str, very_long_argument: str, method=print,
          color="red", funny_number: int = 1337) -> List[int]:
# Yes: 
x = ("a very long long loooong long long loong over the maximum of 120 characters "
     "long string that does not reveal any particular new information")
```
Most IDEs allow setting a vertical ruler to simplify this.

### Indentation
Use exactly `4` spaces for each indentation level. **Do not use tabs**. Most IDEs and text editors will convert each press of <kbd>Tab</kbd> to four spaces (if yours doesn't, change the settings accordingly).

### Language
All variable names and comments have to be in English.

## PEP8 Variable Names
Follow the [PEP8 Naming Conventions](https://pep8.org/#prescriptive-naming-conventions).
* `snake_case`: variables, arguments, functions
* `CapWords`: classes, exceptions
* `CONSTANT_CASE`: constants (defined on module level)

I.e. in this course, in almost all cases you will use snake_case (lowercase with words separated by underscores).


### Semantically wrong names
All variable names should be semantically correct. Semantics involve the meaning of a statement. For variables this means that they have to make sense in the context they are used.
```python=3.10
letters = [2,4,6,8] # This is semantically wrong
even_numbers = [2,4,6,8] # This is semantically correct
```

### Non-descriptive names
Use descriptive names for all variables! This means that the purpose of a variable should become clear from its name. Examples for undescriptive names: `i,j,temp,tmp,list,dict,dic,sum,a,b,c,my_var,my_dict,my_list,val,value,key,string,str,check,flag,bool`.
If a variable serves no purpose (e.g. unused loop counters), use a `_` (single undescore).

### Excessive unwanted output
You should remove or comment out (add a `#` in front of the line you want to comment out, or select the code to comment and press <kbd>Ctrl</kbd><kbd>#</kbd>) all unnecessary `print()` statements. Of course you can use the `print()` function to test your code but comment it out before you submit your assignment.

### Unused Imports
All imports you don't use in your code must be removed before handing in the assignment. **Your IDE or linter will help you here!**


### Unused Variables
Make sure there are no unused variables in the code! This applies to function parameters as well. **Again, your linter or IDE will be a great help here!**




### Missing or incomplete comment header
Make sure to include and fill out the comment header in every source file!
```
################################################################################
# Author:      Firstname Lastname
# StudID:      01234567
# File:        assignmentX.py / assignmentX.ipynb
# Description: ... short description of the file ...
# Comments:    ... comments for the teacher ...
#              ... e.g. things that you know don't work ...
#              ... can be multiline ...
################################################################################
```


## Common Style Flaws
Try to write 'pythonic' and simple constructs. To help you with that we have collected a few common style flaws which should not appear in your code.

### Not closing files
Close a file after opening it. The `with`-Statement closes a file automatically after handling the code in the indented block.
```python=3.10
# NO! This keeps the file open
book = open(cookbook_filename, "w")
book.write("Something")

# Yes
with open(cookbook_filename, "w") as book:
    book.write("Something")
```


### If-pass-else

```python=3.10
# No
if some_condition:
    pass
else:
    do_something()
    
# Yes
if not some_condition:
    do_something()
```


### Global Variables
Avoid global variables. Since we only import your functions when testing your submission, code that relies on global variables will not work. Hence, all of your functions should be self-contained, i.e. don't rely on variables outside the function.

```python=3.10
# No
a = 5

def add_number(b):
    return a + b
    
# Yes
def add_number(a, b):
    return a + b
```

### While-/range-len-loops (in most cases)
Try to avoid `while`-loops when you can tackle the same problem with a more elegant `for`-loop. Don't use `range(len(...))`-loops in order to get the index of an iterable and then iterate over the same object using said index. You can use the elegant `in` statement. There are situations where using the index of an iterable in order to loop over multiple iterables is OK. However, in most of these cases using the `zip`-statement yields the same result.
```python=3.10
names = ["Alex", "Gerald", "Moritz", "Karin", "Katharina", "Thomas"]
studies = ["CS", "BME", "ICE", "BME", "BME", "Sound Engineering"]

# Yes
for name in names:
    print(name)
    
# No
for i in range(len(names)):
    print(names[i])

# Nooooo
i = 0
while i < len(names):
    print(names[i])
    i += 1
    
# Iterate over multiple lists using the zip-statement
for name, study in zip(names, studies):
    print(f"{name}, {study}")
    
# when you really need the index as well, use enumerate:
for index, name in enumerate(names):
    print(f"#{index}: {name}")
```



### Iterating over iterables to check for existence of an element
The `in` statement checks for existence of an element inside an iterable or string.
```python=3.10
numbers = [1,2,3,4,5]
target_number = 6

# No
for number in numbers:
    if number == target_number:
        print("found the target")        
        
# Yes
if target_number in numbers:
    print("found the target")
```



### Inappropriate comparisons with `is`
`is` compares object identity (a unique id of an object) but not values.
```python=3.10
random_number = 4 # definitely random

# No
guess = int(input("Guess a number"))
if guess is random_number:
    print("Yay")
else:
    print("Nay")
    
random_boolean = True # definitely random
if random_boolean == True: # same for False and None
    print("Yay")
else:
    print("Nay")
    
# Yes
guess = input("Guess a number")
if guess == random_number:
    print("Yay")
else:
    print("Nay")

if random_boolean is True:
    print("Yay")
else:
    print("Nay")

    
a = range(10)
b = range(10)
print(a is b) # -> False
print(a == b) # -> True
```

### Avoidable and confusing nesting
Excessive nesting makes code really hard to read.
```python=3.10
# No
if correct_type(arg1):
    if correct_type(arg2):
        if correct_type(arg3):
            do_something()
        else:
            raise TypeError("Argument 3 has the wrong type")
    else:
        raise TypeError("Argument 2 has the wrong type")
else:
    raise TypeError("Argument 1 has the wrong type")
    
# Yes
if not correct_type(arg1):
    raise TypeError("Argument 1 has the wrong type")
if not correct_type(arg2):
    raise TypeError("Argument 2 has the wrong type")
if not correct_type(arg3):
    raise TypeError("Argument 3 has the wrong type")
do_something()
```


### dict.update for single key-value-pair insertion
The `dict`-method `update` should only be used when adding multiple `key`-`value`-pairs to a dictionary.
```python=3.10
# No
cities.update({6010: "Innsbruck"})

# Yes
cities[6010] = "Innsbruck"
```



### Silent exception catching
NEVER SILENTLY CATCH AN EXCEPTION!!!
```python=3.10
# No
try:
    # anything that might fail, e.g.
    number = int(input("Enter a number: "))
except:
    pass


# Minimum, at least do _something_
try:
    # anything that might fail, e.g.
    number = int(input("Enter a number: "))
except Exception as error:
    print(f"Something happened: {error!r}")


# Better, handle specific exceptions
try:
    # anything that might fail, e.g.
    number = int(input("Enter a number: "))
except ValueError as error:
    print(f"Conversion failed, {error!r}")
```


### Pointless if/else constructs that practically do the same thing
```python=3.10
import matplotlib.pyplot as plt

# No
def plot_something(x: list, y: list, yscale: bool) -> None:
    if yscale == False:
        plt.figure()
        plt.plot(x, y, yscale=False)
        plt.title("A plot showcasing the dependence of y on x.")
        plt.show()
    elif yscale == True:
        plt.figure()
        plt.plot(x, y, yscale=True)
        plt.title("A plot showcasing the dependence of y on x.")
        plt.show()

# Yes
def plot_something(x: list, y: list, yscale: bool) -> None:
    plt.figure()
    plt.plot(x, y, yscale=yscale)
    plt.title("A plot showcasing the dependence of y on x.")
    plt.show()
```
