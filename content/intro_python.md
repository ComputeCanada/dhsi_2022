---
title: Introduction to Python
slug: python_intro
execute:
  error: true
format: hugo
jupyter: python3
---



## Documentation

``` python
help(round)            # In Jupyter, you can also use: ?round
```

    Help on built-in function round in module builtins:

    round(number, ndigits=None)
        Round a number to a given precision in decimal digits.
        
        The return value is an integer if ndigits is omitted or None.  Otherwise
        the return value has the same type as the number.  ndigits may be negative.

## Variables and assignments

``` python
age = 20
firstName = 'Jason'
print(firstName, 'is', age, 'years old')
```

    Jason is 20 years old

``` python
a = 1; b = 2              # You can use ; to separate multiple commands in one line
a, b = 1, 2               # You can define multiple variables at once
a = b = 10                # You can assign a value to multiple variables at the same time
b = "b is now a string"   # Variables can change type
```

``` python
age += 3                                   # Another syntax for: age = age + 3
print("Jason's age in three years:", age)  # Note that we have to use double quotes here
```

    Jason's age in three years: 23

{{<exo>}}
What is the final value of the variable `b` in the following code?
{{</exo>}}

``` python
a = "left"
b = a
a = "right"
```

## Types

``` python
print(type(52))
print(type(52.0))
print(type('52'))
```

    <class 'int'>
    <class 'float'>
    <class 'str'>

## Strings

Use square brackets to get a substring:

``` python
element = 'helium'
print(element[0])
print(element[0:3])
```

    h
    hel

``` python
name = 'Paul'
print(name+' Smith')   # You can add strings
print(name*10)         # You can replicate strings by mutliplying by a number
print(len(name))       # Strings have lengths
```

    Paul Smith
    PaulPaulPaulPaulPaulPaulPaulPaulPaulPaul
    4

## Lists

A list is a collection of multiple values. This means that multiple values are stored within a single object.

``` python
T = [27.3, 27.5, 27.7, 27.5, 27.6]
print('temperature:', T)
print('length:', len(T))
```

    temperature: [27.3, 27.5, 27.7, 27.5, 27.6]
    length: 5

Python starts indexing at `0`:

``` python
print('zeroth item of T is', T[0])
print('fourth item of T is', T[4])
```

    zeroth item of T is 27.3
    fourth item of T is 27.6

Lists are mutable (they can be modified):

``` python
T[0] = 21.3
print('temperature is now:', T)
```

    temperature is now: [21.3, 27.5, 27.7, 27.5, 27.6]

``` python
a = [2, 3, 5]
print('a is initially', a)
a.append(7)
a.append(11)
print('a has become', a)
```

    a is initially [2, 3, 5]
    a has become [2, 3, 5, 7, 11]

``` python
print('a before', a)
del a[4]                 # Remove 4th element
print('a after', a)
```

    a before [2, 3, 5, 7, 11]
    a after [2, 3, 5, 7]

You can initialize an empty list and fill it in:

``` python
a = []                   # Start with an empty list
a.append('Vancouver')
a.append('Toronto')
a.append('Kelowna')
print(a)
```

    ['Vancouver', 'Toronto', 'Kelowna']

Lists can be heterogeneous and nested:

``` python
a = [11, 21, 31]
b = ['Mercury', 'Venus', 'Earth']
c = 'hello'
nestedList = [a, b, c]
print(nestedList)
```

    [[11, 21, 31], ['Mercury', 'Venus', 'Earth'], 'hello']

You can search inside a list:

``` python
print('Venus' in b)
print('Mars' in b)
b.index('Venus')      # Returns the index
```

    True
    False

    1

And you sort lists alphabetically:

``` python
b.sort()
print(b)
```

    ['Earth', 'Mercury', 'Venus']

To delete an item from a list:

``` python
b.pop(2)              # Using its index
print(b)

b.remove('Earth')     # Using its value
print(b)
```

    ['Earth', 'Mercury']
    ['Mercury']

## Dictionaries

Dictionaries are unordered sets of key/value pairs.

``` python
favs = {'mary': 'orange', 'john': 'green', 'eric': 'blue'}
print(favs)
print(favs['john'])
print(favs['mary'])
```

    {'mary': 'orange', 'john': 'green', 'eric': 'blue'}
    green
    orange

Now let's see how to add items to a dictionary:

``` python
concepts = {}
concepts['list'] = 'An ordered collection of values'
concepts['dictionary'] = 'A collection of key-value pairs'
print(concepts)
```

    {'list': 'An ordered collection of values', 'dictionary': 'A collection of key-value pairs'}

We can modify the values:

``` python
concepts['list'] = 'Simple: ' + concepts['list']
concepts['dictionary'] = 'Complex: ' + concepts['dictionary']
print(concepts)
```

    {'list': 'Simple: An ordered collection of values', 'dictionary': 'Complex: A collection of key-value pairs'}

Deleting dictionary pairs:

``` python
del concepts['list']      # Removes the key 'list' and its value
print(concepts)
```

    {'dictionary': 'Complex: A collection of key-value pairs'}

Values can be numerical:

``` python
grades = {}
grades['mary'] = 5
grades['john'] = 4.5
print(grades)
```

    {'mary': 5, 'john': 4.5}

The keys can also be numerical:

``` python
grades[1] = 2
print(grades)
```

    {'mary': 5, 'john': 4.5, 1: 2}

## Conditionals

Python implements conditionals via *if*, *elif* (short for "else if") and *else*. Use an *if* statement to control
whether some block of code is executed or not.

``` python
mass = 3.54
if mass > 3.0:
    print(mass, 'is large')  # The indentation is important!
```

    3.54 is large

Let's modify the mass:

``` python
mass = 2.07
if mass > 3.0:
    print (mass, 'is large')
```

{{<notes>}}
Note that we don't get any output.
{{</notes>}}

Add an *else* statement:

``` python
mass = 2.07
if mass > 3.0:
    print(mass, 'is large')
else:
    print(mass, 'is small')
```

    2.07 is small

Add an *elif* statement:

``` python
x = 5
if x > 0:
    print(x, 'is positive')
elif x < 0:
    print(x, 'is negative')
else:
    print(x, 'is zero')
```

    5 is positive

{{<exo>}}
What is the problem with the following code?
{{</exo>}}

``` python
grade = 85
if grade >= 70:
    print('grade is C')
elif grade >= 80:
    print('grade is B')
elif grade >= 90:
    print('grade is A')
```

    grade is C

## Loops

### For loops

``` python
for number in [2, 3, 5]:
    print(number)          # The indentation is important!
```

    2
    3
    5

This is equivalent to:

``` python
print(2)
print(3)
print(5)
```

    2
    3
    5

{{<exo>}}
What do you think that this will print?
{{</exo>}}

``` python
for number in [2, 3, 5]:
    print(number)
print(number)
```

    2
    3
    5
    5

The loop variable could be called anything:

``` python
for i in 'hello':
    print(i)
```

    h
    e
    l
    l
    o

Use `range` to iterate over a sequence of numbers:

``` python
for i in range(0, 3):
    print(i)
```

    0
    1
    2

Let's add numbers 1 to 10:

``` python
total = 0
for number in range(10):
    total += number + 1
print(total)
```

    55

### While loops

``` python
x = 2
while x > 1.0:
    x /= 1.1
    print(x)
```

    1.8181818181818181
    1.652892561983471
    1.5026296018031553
    1.366026910730141
    1.2418426461183099
    1.1289478601075542
    1.026316236461413
    0.9330147604194662

## Functions

Python comes with many built-in functions. You can also install packages that contain additional functions. But you can also write your own functions:

``` python
def greeting():
    print('Hello!')
```

Let's run our new function:

``` python
greeting()
```

    Hello!

``` python
def printDate(year, month, day):
    joined = str(year) + '-' + str(month) + '-' + str(day)
    print(joined)
printDate(1871, 3, 19)
```

    1871-3-19

## Packages

When you launch Python, you can access many functions.

But Python also comes with a *standard library* of several modules. Each module contains additional functions that can be loaded in a session.

{{<ex>}}
Example: the `math` module.
{{</ex>}}
{{<br size="1">}}

``` python
print('pi is', pi)
```

    NameError: name 'pi' is not defined

``` python
import math
print('pi is', math.pi)
```

    pi is 3.141592653589793

You can create an alias from the library:

``` python
import math as m
print(m.pi)
```

    3.141592653589793

You can also import `math`'s items directly:

``` python
from math import pi, sin
print(sin(pi/6))
```

    0.49999999999999994

``` python
help(math)   # Help for libraries works just like help for functions
```

{{<br size="2">}}

*[Back to Day 2](/day2)*
