# Learning Python

Python is a great language to know when working in cyber security - it gives us the means to craft our own tools.

Whilst these notes are not comprehensive - they are a start point and will be added to over time...

## Variables

A variable is a label which points to a value which is stored in memory. The values could be **mutable** or **immutable**.

We can picture this as a container (the space created in memory) being given a value (the value at the memory address) and then a label being placed onto the container (this is the variable name).

We use an **assignment operator** to assign a value to a variable.

We can assign more than one variable at once. This makes sense if the variables are related to each other in some meaningful way.

```python=
x = 5
y = x
z = x + y
print(x)
print(y)
print(z)
```

```
5
5
10
```

```python=
a, b, c = 1, 2, 3
print(a)
print(b)
print(c)
```

```
1
2
3
```

### Variable Reassignment

We can reassign new values to variables. We need to remember that in python everything is an object. Variables have **object identifiers** - we can use these to see and understand more about what is happening with variable reassignment.

When we are assigning **immutable** datatypes to variables, we cannot change the original value - it remains in memory until all references to it have been removed and the garbage collector has subsequently removed it.

```python=
x = 5
alias_x = x
print(id(x))
print(id(alias_x))
x = 10
print(x)
print(alias_x)
print(id(x))
print(id(alias_x))
```

```
139630845591920
139630845591920
10
5
139630845592080
139630845591920
```

### Varibale Naming Conventions

In python, we like to use **snake_case** for variable names. The name should be something which is related to the value which is assigned to it.

We cannot use python key words. We must use letters or underscores to start variable names. The rest of the variable name can include numbers as well as letters and underscores.

>[!IMPORTANT]
>Variable names in python are case sensitive.

**Constant variables** should be written in uppercase letters along with underscores if necessary.

Python classes should be named as **UpperCamelCase** aka **PascalCase**.

Double UNDERscore variables - **dunder** - variables which start and end with two underscores are private and are generally meant to be left as they are.

## Data Types

There are lots of **data types** in python, but some are used more than others.

- Strings are sequences of characters.
- Integers are whole numbers.
- Floats are decimal numbers but they lack precision.
- Decimals are decimal numbers with more precision - they need to be imported from the standard library.
- Booleans are True and False values - they use less memory than using values such as 0 or 1 which are integers.

There are more complex data types which contain other data types - these are known as **data structures** or **collections**.

- Lists are ordered collections of data types.
- Dictionaries are unordered key:value pairs.

There is also a `None` type which just specifies that nothing is there.

Python is **dynamically typed** - this means that variables can have different data types assigned to them.

We can **cast** data types to different data types using functions such as `str()` or `int()`

```python=
name = "Billy"
age = 12
is_adult = False
child = None

billy_l = [name, age, is_adult, child]
sarah_d = {
    name: "Sarah",
    age: 22,
    is_adult: True,
    child: "Mary"
}

print(type(name))
print(type(age))
print(type(is_adult))
print(type(child))
print(type(billy_l))
print(type(sarah_d))

name = 18
age = "Billy"
is_adult = None
child = False
billy_l = {
    name: "Billy",
    age: 12
}
sarah_d = [name, age]

print(type(name))
print(type(age))
print(type(is_adult))
print(type(child))
print(type(billy_l))
print(type(sarah_d))

a = 8
print(type(a))
b = str(a)
print(type(b))
c = int(b)
print(type(c))
```

```
<class 'str'>
<class 'int'>
<class 'bool'>
<class 'NoneType'>
<class 'list'>
<class 'dict'>
<class 'int'>
<class 'str'>
<class 'NoneType'>
<class 'bool'>
<class 'dict'>
<class 'list'>
<class 'int'>
<class 'str'>
<class 'int'>
```

### Strings

Strings are created using `""` or `''` - we need to be consistent in the open and close characters used.

Strings are sequences of characters which are enclosed in the `""` or `''`

Strings are **immutable** data types.

#### Escape Characters

We can escape strings using `\` before specific characters.

- \n creates a new line
- \t is a tab
- \" or \' for quotations
- \\ for a back-slash

```python=
print("\tHello, how are you?\n")
input()
print("He said, \"I like food.\"\n")
print("This \\ is a back-slash.")
```

```
	Hello, how are you?


He said, "I like food."

This \ is a back-slash.
```

#### String Methods

There are lots of methods which we can call on strings.

- .lower()
- .upper()
- .title()
- .split(' ')
- .rstrip('!')
- .replace('hello', 'goodbye')
- .format(name, age)

```python=
msg = "This is a message. Hello, Billy-Bob!"
print(msg)
print(msg.lower())
print(msg.upper())
print(msg.title())
print(msg.split(' '))
print(msg.rstrip('!'))
print(msg.replace('Hello', 'Goodbye'))

name = "Jimmy Boy"
age = 22
print("Hello, {} - you are {} years old.".format(name, age))
```

```
This is a message. Hello, Billy-Bob!
this is a message. hello, billy-bob!
THIS IS A MESSAGE. HELLO, BILLY-BOB!
This Is A Message. Hello, Billy-Bob!
['This', 'is', 'a', 'message.', 'Hello,', 'Billy-Bob!']
This is a message. Hello, Billy-Bob
This is a message. Goodbye, Billy-Bob!
Hello, Jimmy Boy - you are 22 years old.
```

#### Formatting Strings

The `.format()` method is one way to combine data types into a string.

The latest way is to use an **fstring** - we just put `f""` - we can then use `{}` so python will interpolate what is inside the curly brackets.

```python=
name = "Jane"
age = 18
print("Hello, {} - you are {} years old.".format(name, age))
print()
print(f"Hello, {name} - you are {age} years old.")
print(f"{name} - in ten years you will be {age + 10} years old.")
```

```
Hello, Jane - you are 18 years old.

Hello, Jane - you are 18 years old.
Jane - in ten years you will be 28 years old.
```

#### String Indexing and Slicing

We can retrieve specific parts of a string using **indexing** or **slicing**.

Strings are indexed from 0 - we can use these positive indexes. They are also negatively indexed from the last character which is at position -1 We can index this way, too.

```python=
msg = "abcdefgh"
print(msg[0])
print(msg[7])
print()
print(msg[-1])
print(msg[-8])
```

```
a
h

h
a
```

We can **slice** strings using `:`

The slice will include the first specified index but not the last. We can slice using negative indexes, too.

>[!IMPORTANT]
>Slices **do not** include the last specified value

```python=
msg = "abcdefgh"
print(msg[0:3])
print(msg[-3:-1])
print(msg[4:6])
print(msg[4:])
print(msg[:5])
print(msg[:])
```

```
abc
fg
ef
efgh
abcde
abcdefgh
```

### Numbers and Mathematical Operations

We can use mathematical operators with **integers**, **floats** and **decimals**.

- add +
- subtract -
- multiply *
- divide (always returns a float) /
- exponent **
- floor division (always returns an integer) //
- mod (returns the remainder) %

We can round decimal numbers to a specified number of decimal places using the `round()` function.

```python=
a = 8
b = 4
print(a + b)
print(a - b)
print(a * b)
print(a / b)
print(a ** b)
print(a // b)
print(a % b)

c = 100 / 3
rounded_c = round(c, 2)
print(rounded_c)
```

```
12
4
32
2.0
4096
2
0
33.33
```

## Truthiness and Falsiness

Python objects have an inherent **truthiness** or **falsiness** to them. Examples of falsy objects are None data type, empty strings and the value 0. Examples of truthy objects are values above 0, a list of values and a string.

## Comparison Operators

We can use the following signs to make comparisons.

- `==` equal to
- `!=` not equal to
- `>=` greater than or equal to
- `<=` less than or equal to

We use `is` to check if two objects have the same place in memory.

## Assignment Operators

We can use **shorthand assignment operators** which assign new values to variables. An example is `score += 1` to replace `score = score + 1`

- +=
- -=
- *=
- /=

## Logical Operators

We can use `and`, `or` and `not`.

For a condition which uses `and` to be true, **both parts** of the condition must be true.

For a condition which uses `or` to be true, only **one part** of the condition must be true.

Using `not` makes the statement true if the opposite is true - it negates.

```python=
a = [1, 2, 3]
b = [1, 2, 3]
c = None
print(a == b)
print(a != b)
print(a is b)
print(not c)
n = 5
print(n <= 8)
n *= 8
print(n <= 8)
print(True and True)
print(False or True)
print(True or False)
print(not True)
print(not False)
```

```
True
False
False
True
True
False
True
True
True
False
True
```
## Control Flow - If Statements

We can change the flow of an algorithm's execution using **control flow** statements.

`If` statements execute a block of code if they are true. They skip the block of code if the statement (condition) is false.

We can add more cases using `elif` and we can use `else` as a final part.

We can nest `if` statements.

```python=
age = 21
if age >= 18:
    print("You are an adult.")
elif age >= 13:
    print("You are a teenager.")
else:
    print("You are a child.")
```

```
You are an adult.
```

```python=
choice = "west"
if choice == "west":
    print("You see a red door, a yellow door and a blue door.")
    choice_2 = "blue"
    if choice_2 == "red":
        print("A monster eats you!")
    elif choice_2 == "yellow":
        print("You suddently explode!")
    elif choice_2 == "blue":
        print("You escape - well done!")
    else:
        print("There is no such door - you set on fire!")
else:
    print("You went the wrong way and get lost.")
```

```
You see a red door, a yellow door and a blue door.
You escape - well done!
```

```python=
first_name = "Billy"
second_name = "Bob"
if first_name == "Billy" and second_name == "Bob":
    print("Hello, Billy Bob!")

name_1 = "Mary"
name_2 = "Susan"
if name_1 == "Mary" or name_2 == "Mary":
    print("Hello, Mary!")

if name_2 != "Mary":
    print("Sorry, I don't know who you are.")
```

```
Hello, Billy Bob!
Hello, Mary!
Sorry, I don't know who you are.
```

## Lists

Lists are one type of collection or data structure in python. There are many types of collection in python.

Collections are just collections of data types - they are needed so we can structure data - they are like bags which can have items added to them or removed from them.

Lists are *mutuable* data types. We can add and remove values to them and they remain in the same space in memory. They store objects in an ordered list. We can store other data types such as strings, integers and floats in lists. We can store lists inside lists.

We can mix data types in lists, but this is not recommended. We should use the same data type in a list.

Lists are ordered so the elements which are added to them have their order preserved.

Lists are created using `[]`

We can index and slice lists like we can strings. Lists are similar to strings because lists are sequences just like strings are. Strings are sequences of characters while lists are sequences of objects. Both strings and lists are *iterables* which means python can iterate over them.

There are *list methods* which we can use on lists. We look at ways we can grow lists below.

>[!NOTE]
>Lists take up less memory than other collections such as dictionaries, but they use more computational power to search through

```python=
names = ["charlie", "susan", "bob", "alice"]
print(names)
print(names[3])
print(names[:2])
print(id(names))

# append()
names.append("freddy") # adds an element at the end of a list
print(names)
print(id(names))

names_copy = names.copy()
print(id(names_copy))

# insert()
names_copy.insert(0, "lisa") # inserts an element at a position
print(names_copy)
print(names)

colours = ["red", "orange"]
colours_two = ["yellow", "green", "blue", "indigo", "violet"]
print(colours)
print(colours_two)

# extend() - this mutates the original list so be careful with it
# the += operator when used with lists is a shortcut for extend()
colours.extend(colours_two)
print(colours)

# we can do the same as extend() using +=
days = ["Monday", "Tuesday", "Wednesday"]
days_two = ["Thursday", "Friday", "Saturday", "Sunday"]
print(days)
print(days_two)
days += days_two
print(days)

# we can do the same as extend() but in an immutable way with +
letters = ["a", "b"]
letters_two = ["c", "d", "e"]
new_letters = letters + letters_two
print(new_letters)
print(id(letters))
print(id(letters_two))
print(id(new_letters))
```

```
['charlie', 'susan', 'bob', 'alice']
alice
['charlie', 'susan']
140558714044992
['charlie', 'susan', 'bob', 'alice', 'freddy']
140558714044992
140558714045504
['lisa', 'charlie', 'susan', 'bob', 'alice', 'freddy']
['charlie', 'susan', 'bob', 'alice', 'freddy']
['red', 'orange']
['yellow', 'green', 'blue', 'indigo', 'violet']
['red', 'orange', 'yellow', 'green', 'blue', 'indigo', 'violet']
['Monday', 'Tuesday', 'Wednesday']
['Thursday', 'Friday', 'Saturday', 'Sunday']
['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday']
['a', 'b', 'c', 'd', 'e']
140558714049984
140558714052096
140558714052736
```

### Other List Methods

There are other list methods. We can use them to remove items from lists or perform other actions on them.

```python=
# checking for membership
a = "bob" in names
b = "rupert" in names
print(a)
print(b)

# searching lists
print(names.index("susan"))
print(min(names))
print(max(names))

# sorting lists - mutable solution
names.sort() # sorts the list in place - mutable
print(names)

# sorting lists - immutable solution
unsorted_fruit = ["pineapple", "cherry", "banana", "apple"]
sorted_fruit = sorted(unsorted_fruit) # immutable solution
print(unsorted_fruit)
print(sorted_fruit)

# removing items
fish = ["tetra", "cod", "catfish", "danio", "gastro", "cod"]
print(fish)
fish.remove("cod") # we need to know the value
print(fish) # remove() only removes the first value if > 1 present

# using pop with an index
rt_fish = fish.pop(2) # pop() returns the popped value
print(fish)
print(rt_fish)
fish.pop() # pop() removes the last element by default
print(fish)
```

```
True
False
1
alice
susan
['alice', 'bob', 'charlie', 'freddy', 'susan']
['pineapple', 'cherry', 'banana', 'apple']
['apple', 'banana', 'cherry', 'pineapple']
['tetra', 'cod', 'catfish', 'danio', 'gastro', 'cod']
['tetra', 'catfish', 'danio', 'gastro', 'cod']
['tetra', 'catfish', 'gastro', 'cod']
danio
['tetra', 'catfish', 'gastro']
```

### Nested Lists

We can store lists inside lists - these are nested lists aka multi-dimensional lists. We do this when we want to store data as a table or a matrix.

We can index the list we want to use and then the item inside it.

```python=
nl1 = [["a", "b"], ["c", "d"], ["e", "f", "g", "h"]]
print(nl1[1][0])
```

```
c
```

We can iterate through items in nested lists by using nested for loops.

```python=
nl1 = [["a", "b"], ["c", "d"], ["e", "f", "g", "h"]]
for i in nl1:
    for val in i:
        print(f"List: {i} Value: {val}")
```

```
List: ['a', 'b'] Value: a
List: ['a', 'b'] Value: b
List: ['c', 'd'] Value: c
List: ['c', 'd'] Value: d
List: ['e', 'f', 'g', 'h'] Value: e
List: ['e', 'f', 'g', 'h'] Value: f
List: ['e', 'f', 'g', 'h'] Value: g
List: ['e', 'f', 'g', 'h'] Value: h
```

We can also use *list comprehension* with nested lists.

```python=
nl2 = [[val.upper() for val in i] for i in nl1]
print(nl1)
print(nl2)
nl3 = [[val for val in i] for i in nl1 if 'c' in i]
print(nl3)
nl4 = [[val.upper() for val in i] for i in nl1 if 'e' in i]
print(nl4)
```

```
[['a', 'b'], ['c', 'd'], ['e', 'f', 'g', 'h']]
[['A', 'B'], ['C', 'D'], ['E', 'F', 'G', 'H']]
[['c', 'd']]
[['E', 'F', 'G', 'H']]
```

## Functions

Functions are processes for executing tasks - they are used to save rewriting code. They can accept input and return output so they can give different results depending on the data passed to them.

Functions let us keep our code D.R.Y. - do not repeat yourself. This is the opposite of W.E.T. - write everything twice. This is because we can call the function time and time again.

Functions also let us abstract code away from development - we write the code in a function and then we don't have to see it or worry about it.

Functions let us logically order our code so it makes sense - this gets us away from spaghetti code because the functions do discrete tasks so we can organise our code better.

### Syntax

We use the `def` keyword along with `():` A block of code follows the `:` and parameters can be specified inside the `()`

We can then call the defined functions by specifying their name along with `()` and arguments included if they are needed.

```python=
def greeting():
    print("hello!")

greeting()
```

```
hello!
```

### Function Arguments

When we are writing functions we need to consider what data they will need to have in order to work as we want them to.

As an example - we might be creating a function which will work as a - very - simple calculator and return the answer to a calculation which uses two numbers. We will need to think about what it will require in order to work.

In this example our function will need the two numbers and the operation.

The whole point of this function is that different numbers and operations can be sent to it so different output will be returned.

Now we know the data it will need - we need a way to reserve memory for these data - we do this using *parameters*

The *parameters* of a function are specified inside the `()` of the function definition.

```python
def calculate(x, y, operation):
    pass
```

>[!NOTE]
>The `pass` keyword can be used when we dont have code to put into our function *yet* - it means we can still execute our programs without having python throw an error

One way to think about the parameters of a function is to think about making a sandwich.

The steps in the recipe to make the sandwich are the instructions inside the function whilst the ingredients and quantity of sandwiches needed are the parameters.

```python
def make_sandwich(bread, oil, filling, quantity):
    pass
```

This means we can use the `make_sandwich` function to make different kinds of sandwich - cheese | ham | donkey - with different kinds of bread - white | brown | stale - and in different quantities - one | two | twenty.

The point is that the *parameters* of a function allow us to get different output returned from it.

Coming back to the `calculator` function we could do something like the following:

```python
def calculate(x, y, operation):
    if operation == "add":
        return x + y
    elif operation == "subtract":
        return x - y
    elif operation == "multiply":
        return x * y
    elif operation == "divide":
        return x / y
    else:
        return "error"
```

We could then use the `calculate` function to get the answers to various binary operations - binary in that there are two numbers involved.

This is where we come to *arguments*

The *arguments* are the actual *data* we send to the function.

The *parameters* are spaces in memory which are waiting for the data from the *arguments*

An example to make this more clear:

```python
result = calculate(8, 2, "add") # we pass data as arguments which will fill the parameters
print(result) # will print 10 as 8 + 2 = 10

difference = calculate(8, 2, "subtract") # we pass data as arguments which will fill the parameters
print(difference) # the result will be 6 as 8 - 2 = 6
```

>[!NOTE]
>The same `calculate` function is called - we get different *output* because we pass different *arguments* to it

If we do something like `difference = calculate(2, 8, "subtract")` we will get a different result as the arguments we pass will match the order of the parameters in the function definition.

>[!NOTE]
>These are called *positional arguments* since the position matters - we can also have *keyword arguments* which we will look at next

#### Keyword Arguments

Sometimes - especially when we have lots of parameters for a function - we will want to make it clear what each argument refers to.

Consider the following example:

```python
savings = get_savings(3_000, 50, 1000, 500)
```

It is very hard to know what each argument means.

In cases such as this - it makes sense to use *keyword arguments* aka *named arguments*

If we use *keyword arguments* it makes our code much easier to understand:

```python
savings = get_savings(salary=3_000, energy_cost=50, rent=1000, food_cost=500)
```

The names given need to match those used in the *parameters* of the function definition:

```python
def get_savings(salary, energy_cost, rent, food_cost):
    return salary - energy_cost - rent - food_cost
```

>[!IMPORTANT]
>When we use *keyword arguments* we do not have to put them in the same order as the *parameters* of the function but it is *highly recommended* that we *do* match the order

It is possible to mix *keyword arguments* with *positional arguments* if this seems more appropriate.

In our current example, perhaps we consider it as obvious that the first and - hopefully - largest value will be the monthly salary so we might decide just to use a *positional argument* for it and then *keyword arguments* for the less obvious values.

```python
savings = get_savings(3_000, energy_cost=50, rent=1_000, food_cost=500)
```

It is up to us as programers whether or not to use *positional* or *keyword* arguments or a mixture of them.

>[!NOTE]
>We often see *keyword arguments* written as `kwargs`

#### Default Parameters

Sometimes we will define functions which most of the time will use the same value for a parameter.

If this is the case, we can make life easier for ourselves and others who are going to use our code by giving the parameter a *default* value.

In this example we are going to define a function which returns a number raised to a power - obviously a silly example but just to illustrate how to use *default parameters*

We assume that the most common exponent will be 2 so we set this value as a *default parameter* in the function definition.

```python
def power(x, power=2):
    return x ** power
```

Now we can invoke this function with just a number and it will be squared.

```python
result = power(8)
print(result) # will print 64
```

It is still possible to specify different values for the `power` parameter - we just override the default value by specifying a different value in the arguments we pass to the function.

```python
result = power(8, power=3)
print(result) # will print 512
```

## Functions as First Class Objects

Functions in python are first class objects - this means that they can be used like other objects such as *strings* and *integers*.

Here are some interesting things we can do with functions in python:

- Assign them to variables
- Pass them as parameters to other functions
- Store them in collections such as lists
- Return them from other functions

Let's see a few examples.

The first example shows how we can store functions in variables.

```python=
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

add_alias = add # we use a function as a value for a variable
add_alias(5, 8) # we can call the function add() which is the value assigned to add_alias
```

```
13
```

This second example shows how we can store functions in collections such as lists.

```python=
l1 = [add, subtract] # we store functions in a list
l1[1](8, 2) # we can use indexing to access specific functions in the list
```

```
6
```

The third example shows how we can pass functions as arguments to other functions.

```python=
def compute(a, b, operation): # this function takes a function as a parameter called operation
    return operation(a, b)

print(compute(8, 3, add)) # we pass the add function as an argument to compute()
print(compute(8, 3, subtract)) # we pass the subtract function as an argument to compute()
```

```
11
5
```

>[!NOTE]
>We do not add `()` when passing functions as arguments to other functions

This final example shows how we can return functions from other functions.

```python=
def resolve_function(name):
    if name == 'add' or name == 'sum':
        return add # we return a function
    else:
        return subtract # we return a function

fn1 = resolve_function("sum") # we store the returned function in a variable called fn1
print(fn1(8, 2))
fn2 = resolve_function("subtract") # we test the else part of resolve_function()
print(fn2(8, 2))
```

```
10
6
```

## Lambdas

Lambdas are another way to create functions - they are *expression based functions*

If we think about how we assign values to variables we can see that the right side of the `=` assignment operator is an *expression* such as in `x = 2 + 3` the `2 + 3` part is an *expression* which returns a value to be assigned to `x`

This means that with a `lambda` we can use them as an *expression* to assign to a variable.

```python=
x = lambda a, b: a + b # the lambda is an expression based function
print(x(2, 3))
```

```
5
```

Another way to see *lambdas* is as *anonymous functions* because we do not give them names. A good way to help us understand this is to look at the syntax of a regular function and a lambda side-by-side.

```python=
def add(x, y): # regular function
    return x + y
add = lambda x, y: x + y # lambda function
```

We can see that the *lambda* does not have a name whereas using *def* we do use a name.

The parameters for a *lambda* are not in parentheses whereas with *def* they are in parens.

The `:` is in both the regular function and the lambda.

There is no indentation needed for a *lambda* - we cannot use indentation with lambdas.

We do not use the `return` keyword with a *lambda* because it will always *return* the last expression given.

To sum up the syntax for a lambda we can see it as:

`lambda <PARAMS>: <RETURN VALUE>`

>[!NOTE]
>Lambdas do not allow the use of *control flow* structures such as *if* or *for* statements

### Use of lambdas

We could think that *lambdas* are useless since they do not let us write complex functions with control flow structures - but we would be wrong in thinking this.

Lambdas are important because they let us make our code more *concise* and more *expressive*

A common useage of lambdas is when we only need to use a function once - a good example of this is passing a function as an argument to another function.

We dont want to waste time and memory writing regular functions in such a situation - we can use a `lambda` instead.

We can go back to our `add()` and `subtract()` and `compute()` functions which we defined in the section on *Functions as First Class Objects*

```python=
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def compute(a, b, operation):
    return operation(a, b)
```

It seems like a waste of time and memory to define the `add()` and `subtract()` simple functions in such a way - this is because it is a waste of time and memory - it is much better to use a `lambda`

```python=
compute(2, 8, lambda x, y: x + y)
compute(8, 7, lambda x, y: x - y)
```

>[!NOTE]
>We only assigned *lambdas* to variables earlier in these notes to better illustrate how they are *expression based functions* - in reality it is redundent to do this - we just create *lambdas* on-the-fly as shown in the example above

The power of *lambdas* is in their brevity and expressiveness - they are especially useful when we are passing functions as arguments or returning them.

#### Examples of Using `lambda`

Here we go over examples which illustrate how we can use a `lambda` to make our code more concise and not clutter up the namespace.

We start with an *unordered* datatype - a *dictionary* - which contains `key:value` pairs.

```python=
d = {
    'dick': 8,
    'tom': 21,
    'harry': 16
}
```

We want to sort the data in the dictionary by the length of its keys - the length of each name in this case.

In order to sort a *dictionary* we can use the `sorted()` built-in function - the problem is that this function only accepts *sequences* so we will first of all transform our *dictionary* into a *list* of *tuples*

```python=
d_list = list(d.items())
print(d_list)
```

```
[('dick', 8), ('tom', 21), ('harry', 16)]
```

We can now use the `sorted()` function to sort the key:value pairs - this function takes an optional argument called `key` which lets us pass a *function* to `sorted()` which will determine how we want the given data to be sorted.

>[!NOTE]
>The `key` argument we pass to the `sorted()` function is itself a *function* - we could therefore use a `lambda` instead of a regular function

We will first look at how we could sort the `key:value` pairs based on the length of the keys by using a regular function - this is not the recommended way but will help us understand how the `lambda` way is better.

```python=
def length_of_name(kv_pair):
    return len(kv_pair[0])

sorted_data = sorted(d.items(), key=length_of_name)
print(sorted_data)
```

```
[('tom', 21), ('dick', 8), ('harry', 16)]
```

This works and we get the original data from the dictionary sorted by the length of the keys - but it is not the most efficient solution to the problem since we define a regular function for simple functionality which would be better coded as a `lambda`

We will now look at the better solution which uses a `lambda` as the function which is passed to `sorted()` as the value of the optional `key` function.

```python=
sorted_data_better = sorted(d.items), key=lambda kv_pair: len(kv_pair[0])
print(sorted_data_better)
```

```
[('tom', 21), ('dick', 8), ('harry', 16)]
```

In our second example we will sort the original dictionary data by the square root of the values - this again is best done using a `lambda`

```python=
import math

data_sorted_values = sorted(d.items(), key=lambda kv_pair: math.sqrt(kv_pair[1]))
print(data_sorted_values)
```

```
[('dick', 8), ('harry', 16), ('tom', 21)]
```
## Functional Programing

Functional programing is just another way to write code - it is a programing paradigm which means a way of seeing programing.

There is a lot of theory on *functional programing* but in these notes we are going to be focusing on using it in a practical way - we like to be pragmatic.

Python itself is not strictly a *functional programing* language - but we can use it to implement our code in a *functional programing* way or to borrow ideas from it.

### Simple Definition

Our simple definition of *functional programing* is that it is a programing paradigm which favors:

- Using functions as first class objects
- Using *immutable* solutions in preference to *mutable* ones to avoid *side effects*

We have gone over what it means to say that functions in python are *first class objects* - simply put it means we can do things such as pass functions as arguments to other functions and return them from functions.

We will quickly look at what an *immutable* solution means.

Most of the time in python we will have a *mutable* and an *immutable* solution to a problem - we as developers have the choice - we will tend to use the *immutable* solution if we are working with a *functional programing* approach to our code.

>[!IMPORTANT]
>We are not saying that *immutable* solutions are better than *mutable* ones - both are useful at some point - but we are saying that if we are leaning towards a *functional programing* approach we will favor the *immutable* solutions

A simple example could be a user of a web app adding items to a shopping cart. For this our code uses a *list* data structure.

```python=
items = ["spam", "eggs"]
```

The user then adds another item to their cart - the *mutable* solution is this:

```python=
items.append("ham")
```

If we look at items before and after this line of code we will see that it has *mutated* - we have changed the data in the original *list object*

```python=
items = ["spam", "eggs"]
print(items)
items.append("ham")
print(items)
```

```
['spam', 'eggs']
['spam', 'eggs', 'ham']
```

The *immutable* solution will not change the data in the original list.

```python=
items = ["spam", "eggs"]
print(items)
new_items = items + ["ham"]
print(new_items) # same result as the mutable solution
print(items) # but the original list has not mutated - this helps prevent side effects
```

```
['spam', 'eggs']
['spam', 'eggs', 'ham']
['spam', 'eggs']
```

### Progression

We have seen how we can define a *functional programing* approach simply as favoring the use of functions as first class objects and immutable solutions.

As *functional programing* evolved over time programers developed three functions which form the backbone of this approach - they are useful to know and be able to use. The functions are:

- map()
- filter()
- reduce()

All of these functions take two arguments - the first is a *function* and the second is an *iterable object* such as a *list*

The given function will be applied to each element in the iterable and a new object will be returned which means we are using an *immutable* solution to transforming data.

>[!NOTE]
>`map()` and `filter()` return a *collection* whereas `reduce()` returns a single element

### map()

The idea behind `map()` is that we give it data and we receive back a transformed version of that data.

This is achieved by specifying a *function* which we want `map()` to apply to every element in an *iterable* object such as a *list* which we also specify.

A *map object* will be returned - we tend to convert this into a *list* object.

The following diagram will hopefully help with conceptual understanding.

![map](/images/1.png)

Here is an example which shows how we can use `map()` to transform a list of names into a list of their lengths - the *string* datatypes are *transformed* into *integer* datatypes.

```python=
names = ["tom", "dick", "harry"]
names_mapped = map(lambda name: len(name), names) # we use a lambda as the function to pass to map()
print(names_mapped) # a map object has been returned
name_lengths = list(names_mapped) # we convert the map object into a list
print(name_lengths)
print(names) # not mutated
```

```
<map object at 0x7f480418bc70>
[3, 4, 5]
['tom', 'dick', 'harry']
```

Another way to understand what is happening is to think about how `map()` is working on each element.

```
Collection: [x0, x1, x2 ... xj]
Function: f(x) => y
Result: [y0, y1, y2 ... yj]

x0 => f(x0) => y0
x1 => f(x1) => y1
x2 => f(x2) => y2
...
xj => f(xj) => yj
```

In this next example we see how we can create a new *list* of squared numbers based on a *list* of numbers we want to square.

```python=
numbers = [3, 4, 5]
squared = list(map(lambda num: num ** 2, numbers)) # create a list from the returned map object
print(squared)
print(numbers) # not mutated
```

```
[9, 16, 25]
[3, 4, 5]
```

### filter()

This function takes input from an *iterable* object and applies a specified function to each element in it. The function needs to return either `True` or `False`

If the returned value is `True` the `filter()` function will keep that element - it will filter it out if the returned value is `False`

The following diagram will hopefully help with conceptual understanding.

![filter](/images/2.png)

The function given as the first argument in `filter()` is once again often a `lambda`

```python=
names = ["Harry", "Tom", "Dick"]
filtered_names = filter(lambda name: len(name) >= 4, names) # keeps names which have at least 4 chars
print(list(filtered_names))
```

```
['Harry', 'Dick']
```

A more formal way of looking at `filter()` is given below.

```
Collection: [x0, x1 ... xj]
Function: f(x) => y (bool, True|False)
Result: [x0 if y0 is True, x1 if y1 is True ... xj if yj is True]
```

>[!NOTE]
>As seen above - the returned *filter object* includes the original objects not transformed versions of them

Another example here shows how we can filter the original list of names so only names which have an odd number of characters in them are kept.

```python=
names = ["Tom", "Dick", "Harry"]
odd_names = list(filter(lambda name: len(name) % 2 == 1, names))
print(odd_names)
print(names) # note how this is still not mutated
```

```
['Tom', 'Harry']
['Tom', 'Dick', 'Harry']
```

### reduce()

>[!IMPORTANT]
>`reduce()` is rarely seen in python code - Guido van Rossum hates it and it was dropped from the python standard library for python3

The `reduce()` function will only be mentioned in these notes rather than gone into in detail since it is not pythonic but we feel it should at least be mentioned.

Essentialy, the `reduce()` function takes the original elements passed to it from the *iterable* and then combines them into one element which is returned.

It was dropped from python3 because it gets very complicated very quickly. Developers using python tend to switch to using a `for` loop instead of using `reduce()` since the code is easier to follow and the results are the same.

This brings us back to a point we made at the start of our notes on *functional programing* - python is not strictly a *functional programing* language.

>[!NOTE]
>If we insist on using `reduce()` for some weird reason - we can `import functools` to get it when using python3

For some more context as to why `reduce()` was dropped - please [read here](https://www.artima.com/weblogs/viewpost.jsp?thread=98196)

### Conclusion

We can use python in a *functional programing* way but we do not have to - we can mix different ways of coding.

`map()` and `filter()` are used in python but `reduce()` is rarely seen - use a `for` loop instead.

There is a more pythonic way to go about things - this is called *list comprehension* and is *much* more common in python code than `map()` and `filter()` - we will be looking at *list comprehension* and how we can make our code more pythonic in the next section of these notes :smiley:

## List Comprehension

List comprehension is a more pythonic way of doing `map()` and `filter()` - it is syntactic sugar for these two functions which is why it is useful to understand them before learning list comprehension.

The syntax for list comprehension can be summed up as `<EXPRESSION> for elem in <ITERABLE COLLECTION>` which looks much better and is easier to understand than what we saw with `map()` using *lambdas*

The `<EXPRESSION>` part is the same as the *lambda* function we used with `map()`

The `for` part is the same as a regular `for` loop.

The `<ITERABLE COLLECTION>` is the same as when we passed an *iterable object* to `map()`

If we go back to our example of transforming names into their lengths we can see how the more pythonic list comprehension goes about it.

```python=
names = ["Tom", "Dick", "Harry"]
name_lengths = [len(name) for name in names] # a list is returned from this list comprehension
print(name_lengths) # same result as when we used map() with a lambda
print(names) # still not mutated - this is an immutable solution
```

```
[3, 4, 5]
['Tom', 'Dick', 'Harry']
```

>[!NOTE]
>The name we give to the element - in this case `name` - needs to be the same in the *expression* - in this case `len(name)`

Another example given here will show list comprehension solving the same problem we had in the `map()` section of these notes where we wanted to create a new list of squared numbers.

```python=
numbers = [2, 3, 4, 5]
squared_numbers = [n ** 2 for n in numbers] # the list comprehension
print(numbers) # not mutated
print(squared_numbers) # same output as before
```

```
[2, 3, 4, 5]
[4, 9, 16, 25]
```

We can see that list comprehensions are:

- Immutable
- Concise
- Do not need us to use *imperative* procedures

Regarding the last point we can consider what the *imperative procedure* would be for solving the problem of squaring the numbers.

```python=
numbers = [2, 3, 4, 5]
squared_numbers = []
for n in numbers:
    squared_numbers.append(n ** 2)
print(numbers)
print(squared_numbers)
```

Whilst the *imperative* way of solving this problem as shown above works - it is not as concise as using a list comprehension | it is not immutable - the `.append()` method mutates `squared_numbers` - and it is not pythonic.

### Conditional List Comprehension

So far we have seen how using a list comprehension can help us solve the same problems as we solved using `map()` but more concisely and more pythonically.

We can use list comprehensions which include a condition to solve the same problems as we solved using the `filter()` function.

The syntax can be summed up as `<EXPRESSION> for elem in <ITERABLE COLLECTION> if <CONDITION>`

Coming back to our example of using `filter()` to create a list of names which had four or more characters we can solve it using a list comprehension as seen below.

```python=
names = ["Tom", "Dick", "Harry"]
long_names = [name for name in names if len(name) >= 4] # list comprehension with condition
print(names) # not mutated
print(long_names) # same result - a filtered list
```

```
['Tom', 'Dick', 'Harry']
['Dick', 'Harry']
```

We can now look at using a conditional list comprehension to solve the problem we looked at earlier in the `filter()` section of creating a list of names which have an odd number of letters.

```python=
names = ["Tom", "Dick", "Harry"]
odd_names = [name for name in names if len(name) % 2 == 1] # conditional list comprehension
print(names) # not mutated
print(odd_names) # same result as with filter() and a lambda
```

```
['Tom', 'Dick', 'Harry']
['Tom', 'Harry']
```

### True Power of List Comprehension

In some other languages - :eyes: we are looking at *you* javascript :eyes: - the syntax to combine `map()` and `filter()` can get quite ugly.

An example in python which replicates this mess is shown below for an example which uses `map()` to transform a name into its length and `filter()` to make sure only names which have more than three characters in them are included in the new list.

```python=
names = ["Tom", "Dick", "Harry", "Steven"]
# what a mess this is
long_new_names = list(
    map(
        lambda name: len(name),
        filter(lambda name: len(name) > 3, names)
    )
)
print(names)
print(long_new_names)
```

```
['Tom', 'Dick', 'Harry', 'Steven']
[4, 5, 6]
```

Fortunately we are learning to be pythonic so we can ignore that mess and use list comprehensions instead - we will see their true beauty and power here.

```python=
names = ["Tom", "Dick", "Harry", "Steven"]
long_new_names = [len(name) for name in names if len(name) > 3] # what a relief this is
print(names) # not mutated
print(long_new_names) # same result as before
```

```
['Tom', 'Dick', 'Harry', 'Steven']
[4, 5, 6]
```

To more clearly see the beauty and power of pythonic list comprehension - if not convinced already - we will look at a different example in which we have created a - much better - version of twitter.

We want to get a list of usernames for users who have never tweeted so we can send them ~~spam~~ emails letting them know the benefits of tweeting and why it is wonderful.

We will use the pythonic way in the example.

```python=
# we generate the data
users = [
    {"username": "dduck", "tweets": ["puddles are great"]},
    {"username": "ysam", "tweets": []},
    {"username": "mmouse", "tweets": ["i love minnie", "cheese is nice"]},
    {"username": "tcat", "tweets": []},
    {"username": "tpie", "tweets": ["i did i did", "hello pussycat"]}
]

# we use a pythonic list comprehension to extract the data we want
users_to_spam = [user["username"] for user in users if not user["tweets"]]

# job done - we now print the usernames of those users who have never tweeted
print(users_to_spam)
```

```
['ysam', 'tcat']
```

We can see how easy this is to understand and code when we use the list comprehension - it is completed on one line and is human friendly - it is also immutable :smiley:

## Object Oriented Programming

OOP is a way of doing programming - it is a paradigm related to how we go about writing code and developing projects.

OOP lets us *encapsulate* data and behaviour in one object. This way of programming developed to let us model the real world in our code. Alan Kay was involved in this - he saw how organisms could communicate with one another without knowing much about the internal workings of each other. We do this all of the time. I communicate with my television without knowing how it works inside. I need a clearly defined interface (a remote control in this example) in order to do this. The interface is very important. Once an object has been created, its internal workings can be hidden from the programmer - they just need to know how to interact with it (use it in their programs).

OOP uses code to represent things from the real world such as a car, a deck of cards, a song, a schedule etc.

We use classes and objects in OOP.

We can see OOP as being like a factory - the *class* - from which we can create *instances* of it which are independent *objects* which are seperate from the class. Each instance of a class can be unique and different to the other instances.

### Classes

A class is essentialy a blueprint - a template - for how instances (objects) created from it are. The class contains *attributes* for its objects and *methods* which they can use.

>[!NOTE]
>A *method* is a *function* which is attached to an *object*

A class is like a cookie cutter - the objects created using it can be different even though they have the same attributes and methods.

### Instances (Objects)

Objects are constructed from a class blueprint - they contain the class properties and methods.

### Encapsulation

We aim to *encapsulate* (group) public and private attributes and methods into a class. Private just means it is only supposed to be used and referenced inside the class itself whereas public means it can be referenced and used elsewhere. This lets us represent different things which we need in our program. If we are making a poker game, for example, we could encapsulate attributes and methods to do with a user into one class, a deck of cards into another class, a card into another class and so on. We will then be able to better understand our code and work with it to create the game of poker.

### Abstraction

This means we hide the internal workings of objects and provide an interface to work with them.

```python
# a simple example of how objects are individual and unique
class Cookie(object): # no need to use object here in Python3
    pass

c1 = Cookie()
c2 = Cookie()
c3 = Cookie()

print(id(c1))
print(id(c2))
print(id(c3))
```

```
140581476118784
140581476114992
140581476121232
```

### Attributes

Attributes are the properties of objects - they are the data part of our classes.

We could see attributes as variables which belong to the local namespace of objects.

```python
# setting object attributes for c1
c1.buttons = "blue"
c1.scarf = "green"
# getting c1 attributes
print(c1.buttons)
print(c1.scarf)
# setting attributes for c2
c2.buttons = "red"
c2.scarf = "orange"
# getting c2 attributes
print(c2.buttons)
print(c2.scarf)
# setting attributes for c3
c3.buttons = "yellow"
c3.scarf = "purple"
# getting c3 attributes
print(c3.buttons)
print(c3.scarf)
```

```
blue
green
red
orange
yellow
purple
```

### Methods

Methods are functions which are attached to objects. They define the behaviours which objects can perform.

Methods are the interface - how we can interact with the object.

In order to define a method, we define a function inside a class. We use the *self* keyword to reference the object we are calling it on and we use dot notation to call it `mary.fullname()` for example.

```python
# working with methods - simple
class User(object):
    def full_name(self):
        return f"{self.first_name} {self.last_name}"
    def can_drive(self, min_age):
        return self.age >= min_age

mary = User()
mary.age = 20
mary.first_name = "Mary"
mary.last_name = "Brown"
print(mary.full_name())
print(mary.can_drive(18))
```

```
Mary Brown
True
```

```python
john = User()
john.age = 16
john.first_name = "John"
john.last_name = "Jones"
print(john.full_name())
print(john.can_drive(18))
```

```
John Jones
False
```

### Initializing

We can use the `__init__` method to set attributes on objects when they are instansiated from a class.

This is useful because we usually want instances of a class to have lots of attributes which are the same but with different values.

Using the __init__ method to initialise objects is a good way to make sure that they are instantiated correctly and consistently.

__init__ is a *dunder* method - these are also known as *magic methods* because we do not call it explicitly - python calls it itself.

>[!IMPORTANT]
>We should include an __init__ method in every class we create

```python
# using the __init__ method to initialise objects
class Fish(object):
    def __init__(self, order, colour, length):
        self.order = order
        self.colour = colour
        self.length = length
```

```python
billybob = Fish("catfish", "brown", 5)
print(billybob.order)
print(billybob.colour)
print(billybob.length)
```

```
catfish
brown
5
```

### Class Attributes

These are attributes which are linked with a class rather than individual objects which have been instantiated from the class. This means that all the objects created from the class can get the class attributes.

```python
class Bike(object):
    DEFAULT_COLOUR = "blue"
    def __init__(self, color):
        self.color = color

bike_1 = Bike("red")
print(bike_1.DEFAULT_COLOUR)
print(id(bike_1.DEFAULT_COLOUR))
bike_2 = Bike("red")
print(id(bike_2.DEFAULT_COLOUR))
print(bike_1.color)
print(id(bike_1.color))
print(bike_2.color)
print(id(bike_2.color))
bike_1.color = "yellow"
print(bike_1.color)
print(id(bike_1.color))
print(bike_2.color)
print(id(bike_2.color))
Bike.DEFAULT_COLOUR = "green"
print(bike_1.DEFAULT_COLOUR)
print(bike_2.DEFAULT_COLOUR)
print(id(bike_1.DEFAULT_COLOUR))
print(id(bike_2.DEFAULT_COLOUR))
```

```
blue
140572951488944
140572951488944
red
140572951488752
red
140572951488752
yellow
140572951488880
red
140572951488752
green
green
140572951488816
140572951488816
```

### Get and Set

In the example above, both `Bike` objects are getting the class attribute `DEFAULT_COLOUR` from the class. Python first of all looks into the object itself for the variable `DEFAULT_COLOUR` but does not find it so bubbles up to the *class memory space* and does find it.

If we try to set `DEFAULT_COLOUR` from an instance of `Bike` it will not work - Python will create a variable called `DEFAULT_COLOUR` in the *object memory space* and it will find this one first before the class attribute each subsequent time.

```python
bike_1.DEFAULT_COLOUR = "red"
print(bike_1.DEFAULT_COLOUR)
print(id(bike_1.DEFAULT_COLOUR))
print(Bike.DEFAULT_COLOUR)
print(id(Bike.DEFAULT_COLOUR))
print(bike_2.DEFAULT_COLOUR)
print(id(bike_2.DEFAULT_COLOUR))
```

```
red
140134846294256
blue
140134846294448
blue
140134846294448
```

### Accessing Class Attributes from Methods

We tend to access class attributes from methods. An example is to set default values if a value is not passed to the init method. We can reference the class attribute from inside methods using the self keyword or the name of the class.

```python
class Car(object):
    DEFAULT_COLOUR = "black"
    def __init__(self, make, colour=None):
        self.make = make
        if colour:
            self.colour = colour
        else:
            # self.colour = Car.DEFAULT_COLOUR
            self.colour = self.DEFAULT_COLOUR

car_1 = Car("bmw")
print(car_1.colour)
car_2 = Car("honda", "red")
print(car_2.colour)
```

```
black
red
```

### Keeping an Instance ID

One use case of a class attribute is having an id variable which keeps track of how many instances have been created. We could use something like this to keep track of how many players are in a game or to give each instance a unique id.

>[!NOTE]
>We need to use the *class name* when *setting* values to class attributes from within methods - self will not work

```python
class Player(object):
    ACTIVE_PLAYERS = 0
    DEFAULT_NAME = "anon"
    def __init__(self, name=None):
        if name:
            self.name = name
        else:
            self.name = self.DEFAULT_NAME
        Player.ACTIVE_PLAYERS += 1 # use the class name
    
    def logout(self):
        Player.ACTIVE_PLAYERS -= 1 # use the class name
        return(f"{self.name} logged out.")
    
p1 = Player("Barry")
p2 = Player()
print(Player.ACTIVE_PLAYERS)
print(p1.logout())
print(Player.ACTIVE_PLAYERS)
```

```
2
Barry logged out.
1
```

### Class Methods

Class methods are methods which are linked to a class rather than an instance of a class. We use them when the method does not need to know anything about the specifics of an instance whereas we use instance methods when the method does need to know something about the instance which is calling it.

>[!NOTE]
>Class methods often end up being used when a developer can not think of anywhere else to put the method - even though this is not ideal it happens

Class methods are defined following the `@classmethod` *decorator* and they use `cls` as the first passed argument rather than `self`.

```python
class Pets(object):
    PETS_CREATED = 0
    @classmethod
    def get_pet_number(cls):
        return cls.PETS_CREATED
    
    def __init__(self, species, name="Billybob"):
        self.name = name
        self.species = species
        Pets.PETS_CREATED += 1
    
cat_1 = Pets("cat")
print(Pets.get_pet_number())
fish_1 = Pets("catfish", "mobydick")
print(Pets.get_pet_number())
print(cat_1.name)
print(fish_1.name)
```

```
1
2
Billybob
mobydick
```

#### Class Method Example

Another example of when a class method could be used is when we want to turn data from one format to another before it is sent to the `__init__` method.

This example shows data which is in the form of a csv list coming into the method and then being unpacked into different data types before being sent to the `__init__` method to create an instance.

```python
class Book(object):
    @classmethod
    def from_str(cls, data_str):
        title, pages, price = data_str.split(",")
        # we pass the unpacked data to __init__
        return Book(title, pages, price)
    
    def __init__(self, title, pages, price):
        self.title = title
        self.pages = int(pages)
        self.price = float(price)

# we unpack csv data using a class method
book_1 = Book.from_str("Matilda,382,2.99")
print(book_1.title)
```

```
Matilda
```

### Magic Methods

Magic methods simply refers to methods which we do not invoke directly - python invokes them for us.

The most common magic method is `__init__` becuase we use it in every class we create. This method is magic because we do not directly invoke it - python invokes it when we instantiate a new object from a class.

>[!NOTE]
>Magic methods are also known as *dunder methods* because of the double underscore at the start and end of them

#### __str__

The `__str__` magic method returns a human readable string representation of an object. This is used so we know more easily what each object is. We could see this as a human way to refer to objects - in the example below we will be thinking about motorcycles - the human way to refer to one is something like *honda fireblade*

```python
class Motorcycle():
    def __init__(self, make, model, cc, year):
        self.make = make
        self.model = model
        self.cc = cc
        self.year = year
    
    def __str__(self):
        return f"{self.cc}cc {self.make} {self.model} ({self.year})"

bike_1 = Motorcycle("honda", "fireblade", 650, 2008)
print(bike_1) # without the __str__ magic method we could get a memory address returned
```

```
650cc honda fireblade (2008)
```

>[!NOTE]
>Without the `__str__` magic method we would get a memory address returned - for example: `<__main__.Motorcycle object at 0x7f6e04e27850>`

#### __repr__

The `__repr__` magic method is like the `__str__` magic method but it is more for machines rather than humans.

It will look more like code than regular human language.

```python
class Motorcycle():
    def __init__(self, make, model, cc, year):
        self.make = make
        self.model = model
        self.cc = cc
        self.year = year
    
    def __repr__(self):
        return f"Motorcycle(make={self.make}, model={self.model}, cc={self.cc}, year={self.year})"
bike_1 = Motorcycle("honda", "fireblade", 650, 2008)
bike_1 # if we use print() we will invoke __str__
```

```
Motorcycle(make=honda, model=fireblade, cc=650, year=2008)
```

>[!TIP]
>The returned value of `__repr__` should ideally be able to be used to instantiate a new object from a class

### Interfaces and Magic Methods

Interfaces are ways which we can interact with the attributes and methods of objects.

Python uses the same interfaces for lots of different things.

An example of this is the `+` operator which can be used to add integers, concatanate strings, join lists and more.

Another example is the `in` keyword for testing membership. This can be used to check if characters are in strings, objects are in lists, integers are in ranges and more.

One more example is how we can use `[]` to access elements in lists, items in dictionaries, characters in strings and more.

We can implement these interfaces - and many more - by using *magic methods* in our own classes.

>[!IMPORTANT]
>We want to make interaction with objects instantiated from our own classes as intuitive as possible - we therefore like to use interfaces which are consistent

An example of this is given below.

We can imagine that we are creating card games and in order to do so we have created a class for card objects.

The card objects have a value attribute which we intend to be used to add the values of cards together.

```python
class Card():
    def __init__(self, value, suit):
        self.value = value
        self.suit = suit

hearts_5 = Card(5, "hearts")
diamonds_8 = Card(8, "diamonds")

print(hearts_5.value)
print(diamonds_8.value)
```

```
5
8
```

For somebody who has not seen the code inside our class, the most intuitive way to add the values of `Card` objects together would be to use the commonly used `+` operator as the interface. This, however, does not work at the current time. If we try `hearts_5 + diamonds_8` we will receive a `TypeError`

One way to implement the functionality of being able to add `Card` objects would be to define an `add` method in the class.

```python
def add(self, other_card):
    return self.value + other_card.value
```

This works but in order to use it a developer would need to code: `total = hearts_5.add(diamonds_8)` which is not at all intuitive since it does not follow a consistent approach.

There is a better way.

We can use the `__add__` magic method which python gives us. This will allow developers to use the `+` operator as an interface to add together the values of `Card` objects. We simply need to make our current `add` method a *dunder* magic method: `__add__`

```python
def __add__(self, other_card):
    return self.value + other_card.value
```

The full code of the class and an example of how a developer can now use `+` to add the values of `Card` objects is given below.

```python
class Card():
    def __init__(self, value, suit):
        self.value = value
        self.suit = suit
    
    def __add__(self, other_card):
        return self.value + other_card.value

hearts_5 = Card(5, "hearts")
diamonds_8 = Card(8, "diamonds")

total = hearts_5 + diamonds_8

print(total)
```

By using magic methods in this way, we can make working with classes which we create a lot more intuitive. The reason for this is that as humans we will use what we already know when we approach new things. In this case, if a developer wants to add together two cards in a game they are creating which uses objects instantiated from our `Card` class, they will naturally try `+` first of all and they will expect it to work as intended - we can make this happen using the `__add__` magic method.

>[!IMPORTANT]
>Using *magic methods* makes our python code clean and easy to work with

### Equality and Magic Methods

Before we consider how we can use the `__eq__` magic method in python, it is worth taking the time to reflect on what it means to say that things are *equal*.

Let us take two shirts as an example. We might say that they are equal if they are the same colour and same size. This works for everyday use - for example when buying a shirt we will generally consider all of the small white shirts to be the same and therefore choose any of them off the rack.

But some people might be more picky and realise that some of the shirts have imperfections such as small holes in them or a thread of coton sticking out somewhere. In this view of being equal, we might consider 7 of the 10 shirts on the rack as being equal because we cannot see imperfections but the other three as not being equal because they have some kind of problem. We would then choose one of the seven shirts which we consider to be equal.

Somebody else might think about it more and realise that on an atomic level of course none of the shirts are equal - each one has a different atomic configuration.

We therefore define equality in a relative way which suits the needs of the context we are working in.

#### Equality in Python Using ==

By default, when python checks equality using `==` it performs a strict check which means it is checking if the two objects have the same space in memory. It will return `True` if they do and `False` if they do not.

```python
clubs_3 = Card(3, "clubs")
spades_3 = Card(3, "spades")

print(clubs_3 == spades_3)
print(id(clubs_3))
print(id(spades_3))
```

```
False
0x7f58c9477f70
0x7f58c9477f10
```

##### __eq__

We can define in our own classes what we want equality to mean. This can be achieved by using the `__eq__` magic method which will then let developers use `==` to check equality of objects instantiated from our class in a specified way.

>[!CAUTION]
>Before using `__eq__` we need to very carefully consider what equality means in our class and whether or not that will ever change

We could, for example, decide that for `Card` objects we want their equality to be based on their values. In this case, we could use the `__eq__` magic method as shown below.

```python
def __eq__(self, other_card):
    return self.value == other_card.value

clubs_3 = Card(3, "clubs")
spades_3 = Card(3, "spades")

print(clubs_3 == spades_3)
print(hearts_5 == spades_3)
```

```
True
False
```

We need to be careful before we use `__eq__` What if in this example we need equality to be based on the suit rather than the value? Problems such as this could lead to lots of work refactoring code.

>[!NOTE]
>We do not lose the ability to perform strict memory location equality checks if we implement our own version of `__add__` because the `is` keyword still does it

There are other comparison magic methods available such as `__lt__` for less than and `__gt__` for greater than.

### Inheritance

Classes can *inherit* attributes and methods from other classes - this is known as *inheritance*. Methods are inherited and anything else which has been defined at a *class level* such as *class attributes*. Attributes defined in an `__init__()` method are not inherited though there is a way to achieve this - covered below in the `super()` section.

This is useful because we might want to use the same attributes and / or methods which are already in a class. We can also modify these things once a class has inherited them.

An example might be we have a parent class which defines what a vehicle can do, and we then want to create a class to specify what a motorcycle can do and one which specifies what a car can do. Since both are vehicles they will need to inherit from the Vehicle class - we can then add methods and attributes which are specific to motorcycles and cars. In this way, we build on parent classes.

If we modify a parent method in a child class, python will look in the child class first and use that method rather than the one in the parent class. If the method does not exist in the child class, python will bubble up and look for it in the parent class.

In order to use inheritance, we pass the *parent* class to the *child* class as an argument to its definition.

A good way to understand *inheritance* is to think: *child is a / an parent* for example *`Fish` is an `Animal`*

```python
class Animal:
    plant = False
    def __init__(self):
        self.eyes = 2
        
    def breathe(self):
        return "I am breathing."
    
    def defending(self):
        return "I am defending my territory."
    
class Fish(Animal):
    def __init__(self, species):
        self.species = species
    
    def breathe(self):
        return "I am breathing underwater."
    
    def swim(self):
        return "I am swimming."

nemo = Fish("clownfish")
print(nemo.species) # this attribute is found in the Fish class
print(nemo.defending()) # this method is inherited from Animal()
print(nemo.breathe()) # this is modified in Fish()
print(nemo.swim()) # this is added in Fish()
print(nemo.plant) # class attributes are inherited
# attributes from Animal __init__ are not inherited
# so the below line of code will throw an error

# print(nemo.eyes)

# checking classes the nemo object belongs to
print(isinstance(nemo, Fish)) # True
print(isinstance(nemo, Animal)) # True
```

```
clownfish
I am defending my territory.
I am breathing underwater.
I am swimming.
False
True
True
```

### Polymorphism

This is simply the idea that one thing can take many forms. In Python, this relates to the concept of what `self` is.

The following code shows how we could define the `__str__` magic method in several related classes.

```python
class Vehicle(object):
    def __str__(self):
        return "Object: Vehicle"

class Car(Vehicle):
    def __str__(self):
        return "Object: Car"
    
class Airplane(Vehicle):
    def __str__(self):
        return "Object: Airplane"
```

There is a lot of repetition - there must be an easier way to do this.

We could just define one `__str__` method at the top level class and use polymorphism to dynamically alter the returned values.

>[!TIP]
>When we notice common patterns in methods we tend to define one method at the top level class

In the example below we define `__str__` at the top level class which is `Vehicle` and code it so that it dynamically retrieves the class name of `self` - the question arises - what is `self`?

```python
class Vehicle(object):
    def __str__(self):
        return "Object: {}".format(self.__class__.__name__)

class Car(Vehicle):
    pass
    
class Airplane(Vehicle):
    pass
```

The value of `self` will depend on the type of object which called the `__str__` method. For an `Airplane` object `self` will be `Airplane` whilst for a `Car` object `self` will be `Car`

The resulting output is shown below.

```python
a = Airplane()
c = Car()

print(a)
print(c)
```

```
Object: Airplane
Object: Car
```

The above example shows us *polymorphism* in action - Python is determining the value of `self` at runtime.

Another example is given below.

```python
class Vehicle(object):
    def move(self):
        my_sound = self.sound()
        print("I'm moving, and I sound: {}".format(my_sound))

class Car(Vehicle):
    def sound(self):
        return "Brooooom"
    
class Airplane(Vehicle):
    def sound(self):
        return "Nnneeaoowww"

a = Airplane()
a.move()
c = Car()
c.move()
```

```
I'm moving, and I sound: Nnneeaoowww
I'm moving, and I sound: Brooooom
```

### super()

We can use `super()` from a child class to have access to anything we specify from the parent aka super class.

Coming back to the example above, we can get the initialization attributes from the `Animal()` class into the `Fish()` class by using `super().__init__()` in the `Fish()` class `_init__(self)` method. The example below shows this for a different `Animal()` subclass.

```python
class Bird(Animal):
    def __init__(self):
        super().__init__()
    
duck = Bird()
print(duck.eyes) # this can now be accessed
```

```
2
```

>[!NOTE]
>We can use `super()` to access *anything* from the super class - another example is provided below

#### super() example

Sometimes, subclasses need to "override" a method to provide its own functionality. Example - in our company we have two different types of Employee - Developers and Managers.

Each employee has a salary method, which returns the yearly salary of the employee as a function of her base salary + an extra based on years of experience. It works similarly for both Manager and Developers so we put all that common functionality in a super class called `Employee`

```python
class Employee:
    def __init__(self, name, base_salary, years):
        self.name = name
        self.base_salary = base_salary
        self.years = years
        
    def salary(self):
        return self.base_salary + (self.years * 1000)
```

Developers are regular employees, so they just extend directly from `Employee` without making any modifications.

```python
class Developer(Employee):
    pass

mary = Developer('Mary Smith', 70_000, 6)
print(mary.salary())
```

```
76000
```

Managers make a little bit extra money - because they are clearly more important than the deveoplers who are actually doing the work :roll_eyes: - they make 10% more of the computed salary.

We need to rewrite the `salary()` method with a modification in the `Manager` class, but this wastes time since we are repeating code.

```python
class Manager(Employee):
    def salary(self):
        return (self.base_salary + (self.years * 1000)) * 1.1

jane = Manager('Jane Sanchez', 70_000, 6)
print(jane.salary())
```

```
83600.0
```

As we can see, with the same parameters, Jane is making more money.

Repeating the whole method again is not a great idea, though. We just need the regular salary defined in the class `Employee` and then we can add an extra 10% on top of that.

We can use `super()` in order to do this - it will allow us to reference methods implemented in parent classes.

```python
class Manager(Employee):
    def salary(self):
        return super().salary() * 1.1 # uses super()

jane = Manager('Jane Sanchez', 70_000, 6)
print(jane.salary())
```

```
83600.0
```

`super()` gives us access to the *super* class and from there we can access *anything* from that *parent* class.

## Working with Files

Working with files is easy in python but it does pose problems in that we are not just working with python - we are working with files which might contain bad data and we are interacting with operating systems which might cause problems - maybe the file cant be opened not because of incorrect python code but because the user python is running as does not have the necessary permissions to work with the specified file. We also need to consider the user of our program - they might make mistakes such as choosing to try to save their file in a directory they dont have write access to. Even a working environment or hardware itself can mess things up when we are working with files since the files are stored in secondary memory such as a hard drive - hard drives fail sometimes.

>[!IMPORTANT]
>We need to consider how we can manage errors gracefully to help the users of our programs if and when errors occur - this is especially important when working with files since the user | the OS or even a working environment can mess up our programs

### Interactions

Python does not interact *directly* with files. The files are stored in secondary memory such as a hard drive whilst python is a running process. Python interacts with the *Operating System* which in turn interacts with the files.

The OS therefore acts as a guardian of the files - this is important because it is possible to destroy operating systems or applications when we work with files - the security of files is also important - we dont want unauthorized users accessing sensitive data.

>[!IMPORTANT]
>The OS manages the files and our python code interacts with the OS

>[!NOTE]
>The OS creates a *file descriptor* when we open a file using python - this is simply an integer which points to an entry in the kernels global file table where data about the open file is stored

As an example of this, if we want to read eight bytes of a .txt file our python codes lets the OS know that we want to do this. The OS checks and if it can get those eight bytes it copies them into memory in a shared space where the python process can retrieve them - the bytes in the original file are not accessed directyly by our python code.

### Important Concepts

The two important concepts to know about when we are working with files in python are the *open mode* and *file cursors*.

#### Open Mode

We can open a file in python using the `open()` function. This returns a *file object* which can be captured in a variable.

The *open()* function accepts lots of arguments - the only necessary one is the path to the file which we want to open - this can be an *absolute* or *relative* path.

When we open a file with the `open()` function we can specify a mode as an optional argument. This is important because if we specify a mode such as *read* and then try to *write* to the file we will encounter an error. The most common modes are:

- `r` which opens the file for reading
- `w` which opens the file for writing - it will overwrite the entire file
- `a` which opens the file with the *cursor* at the end of the file contents so we will append to it
- `r+` which opens the file for *reading* and *writing* with the cursor at the beginning

>[!NOTE]
>The default mode which is used if no other is specified - this is done as the second argument - is *read*

```python=
file = open("test.txt") # the default open mode of r is used
>>>>>>> 99285ca41e473cdee5c77b8ec7a1ec9ce28b17ac
print(file) # file contains a file object
contents = file.read()
print(contents) # we now see the contents of the file
```

```
<_io.TextIOWrapper name='test.txt' mode='r' encoding='UTF-8'>
This is line one.
This is line two.
This is line three.
```

#### Cursor or Pointer

The *cursor* essentialy points to a location in the data of the file. We can picture a file as a sequence of *bytes* and the cursor points to which byte we are on.

The cursor determines where in the file we are reading or writing from.

If the file has been completely read, the cursor will be at the end of the file so if we read it again we will have an empty string returned. If we add changes to the file and then read it again the cursor will read the changes as it was at the end of the original contents.

In order to send the cursor back to the beginning of a file we can use `seek(0)` and of course we can specify other positions as the argument.

```python=
contents_2 = file.read() # returns empty as cursor is at end
print(f"Nothing here: {contents_2}")
file.seek(0) # resets the cursor to index 0
contents_3 = file.read() # returns all data
print(contents_3)
```

```
Nothing here: 
This is line one.
This is line two.
This is line three.
```

>[!TIP]
>To find where the cursor is we can use the `.tell()` method

### More on Reading Files

We can specify how many *bytes* we want to read by adding the number as an argument for the `.read()` method.

```python=
file.seek(0)
contents_4 = file.read(12)
print(contents_4)
```

```
This is line
```

>[!IMPORTANT]
>It is dangerous to read the *entire* contents of large files - remember - the OS copies the bytes from the original file into *primary memory* which is not as large as *secondary memory* and can quickly become full

#### Using readline()

To get around the problem of reading large .txt files we can use the `readline()` function which will only get the data from the file up to a `\n`

>[!NOTE]
>The `readline()` function returns the `\n` as well as other data

Reading one line of a large file at a time is common - there is a better way to do this than using the `readline()` function.

#### File Objects and the Iterator Pattern

Remember - a *file object* is returned from the `open()` function.

These *file objects* are *iterable* - this means we can iterate over them using a `for` loop.

The result of this is very similar to `readline()` in that we get the contents of the file line by line.

```python=
f = open('massive_book.txt')
massive_contents = ''
for line in f:
    massive_contents += line
print(massive_contents)
```

```
This is line one.
This is line two.
This is line three.
This is line four.
This is line five.
Okay - not massive but just to illustrate a point.
```

#### Close

We are using system resources by having a file open. This is because the OS has to allocate resources to keep track of what is happening with the open files. The OS needs to monitor everything we are doing with open files - this means that resources are used to do the monitoring.

If we open too many files without closing them we can run out of memory and our system could crash.

We need therefore to *close* the file once we have finished working with it. We just need to call the `close()` method on the *file object* we have open.

>[!TIP]
>We can check if a file has been closed by using the `.closed` attribute

```python=
print(file.closed)
file.close()
print(file.closed)
f.close()
print(f.closed)
```

```
False
True
True
```

### Writing

We can use the `w` *open mode* if we want to write to a file - if the file does not already exist it will be created.

```python=
f = open("new_book.txt", "w") # we specify the open mode to be w for write
f.write("hello world!")
f.close()
f = open("new_book.txt", "r")
contents = f.readline()
print(contents)
f.close()
```

```
hello world!
```

>[!CAUTION]
>As soon as we open a file using the `w` open mode the entire contents of the file will be truncated and therefore lost

```python=
f = open("new_book.txt", "w")
f.close() # we didnt do anything but the contents have now gone
f = open("new_book.txt", "r")
contents = f.read()
print(f"Nothing here: {contents}")
f.close()
```

```
Nothing here: 
```

#### Flushing Data

We need to remember that we are not working *directly* with the data stored on the hard drive - we are interacting with the OS.

The OS does not write the data we specify to be written immediately - that would cause a loss of performance as it would need to keep accessing the hard drive which is slow.

The OS stores the data we want it to write to the file - it stores it in *primary memory* in a buffer. After some time - this will depend on the OS configuration - the data is flushed drom the buffer to the hard drive. This means that we will not see changes taking place in real time.

If we want to force the transfer of the data to the hard drive we can use the `.flush()` method.

>[!NOTE]
>The buffer is flushed when the `.close()` method is called.

```python=
f = open("new_book.txt", "w")
f.write("this is some new writing\n") # this does not appear immediately - it is buffered
f.flush() # this forces the data to be written to the hard drive
f.write("here is some more writing") # not written to the hard drive immediately
f.close() # flushes the data to the hard drive

f = open("new_book.txt", "r")
contents = f.read()
print(contents)
```

```
this is some new writing
here is some more writing
```

#### Appending Data

If we dont want to lose the original data in a file which already exists, we can use the `a` method which places the cursor at the end of the original data and then lets us *append* data to it.

>[!TIP]
>We can use the `.tell()` method to see where the cursor is

```python=
f = open("new_book.txt", "a") # the data will not be lost
print(f.tell()) # shows the cursor is at the end of the data
f.write("\nlook at this - it is yet more writing\n")
f.close()

f = open("new_book.txt", "r")
contents = f.read()
f.close()
print(contents)
```

```
50
this is some new writing
here is some more writing
look at this - it is yet more writing
```

>[!IMPORTANT]
>We cannot control the cursor position using `seek()` in *append mode* - the data will *always* be added at the end even if we use `seek(0)`

#### Read and Write

We can read and write using the `r+` open mode.

>[!TIP]
>We can check if a file is *readable* or *writeable* using the `.readable()` and `.writeable()` methods which return `True` or `False`

This mode will let us read the data and write data - the cursor is moved to the beginning when we use this mode.

>[!CAUTION]
>The data we write to the file will always replace the original data - it will not shift data across - this is similar to the pain in the :horse: *insert* key on our keyboard

### Using the `with` Context Manager

The `with` context manager gives us a great way to work with files - and other tasks which involve an entry and exit - since it *closes* the resources for us.

This is important because as we have seen every time we open a file the OS has to allocate resources to monitor our interaction with it. If we open too many files without closing them then the system could crash.

We might think that we are able to remember to *close* files once we have finished working with them - but the reality is that when we are working with lots of open files we may well forget to do so.

In addition to this, we need to consider what happens if an *exception* occurs during the file management process. In this case if we are not working in the `with` context manager then the file will *not* be closed because the exception occurs before that happens.

```python=
f = open("./test.txt", "a")
f.write(hello) # this throws an error
f.close() # the file is never closed
print(f.closed) # this is False
```

```
False
```

To help avoid files remaining open without our knowing it due to exceptions occuring during their management we can use a `try | except | finally` block.

```python=
f = open("./test.txt", "a")
try:
    f.write(hello) # file management logic goes here
except:
    print("Error")
finally:
    f.close() # this happens no matter exception or not
print(f.closed) # this is now True
```

```
True
```

The problem with the `try | except | finally` block is that even though it works it can be tricky to remember to use it all of the time.

Python makes this closure of open resources even if they encounter errors much easier - it implements the `with` context manager.

It is quite simple - the `with` block contains the code to manage the file and it will automatically close the file no matter its state once the block is exited.

```python=
with open("./test.txt", "a") as f:
    # we put all the file management logic in the with block
    print(f.closed) # shows the file is open
    f.write(hello) # throws the error
print(f.closed) # True as the file has been closed despite its state
```

```
False
True
```

>[!NOTE]
>We still need to specify the *open mode* when we are using `with` and a cursor is still used

## Working with HTTP

We can *install* the *requests* library using `pip install requests`

The *requests* library lets us work with *http* using python.

Once we have installed the *requests* library we will need to *import* it into our python code using `import requests`

>[!NOTE]
>When we *import* non-standard python libraries we do so at the start of our code

### GET Request

We can use the *requests* library to perform different operations using *HTTP* verbs.

The first one to think about is the *GET* request. We can *get* a resource using the `.get()` method. This method takes various arguments - we must include the *path* of the resource we want to *get*

>[!NOTE]
>For these examples we will be using [httpbin](https://httpbin.org) which lets us test different types of http request

```python
import requests

resp = requests.get("https://httpbin.org/html")
print(type(resp))
```

We see that we get a *requests Response* object returned. These objects contain lots of methods and attributes which are useful for when we are working with http

In this first example we are getting a simple piece of *html* returned to replicate what would be returned by an http request to a website.

We can take a look at the *html* which has been returned by the server using `print(resp.text)`

This will show us what is in the http *body* of the server response.

We can have a look at the *headers* of the server response by using `print(resp.headers)`

#### JSON GET Request

We can get json data returned from servers. This is usually the case when we are requesting data from an *API*

```python
import requests

resp = requests.get("https://httpbin.org/get")
print(resp.headers) # shows that the Content-Type is now application/json
```

We can access more specific data from the response by using `[]` to specify the *header* we are interested in `print(resp.headers["Content-Type"]`

When we get *json* data returned we can use the `.json()` method to have it returned and then parsed into a python *dictionary* data-type which will make it easier to work with.

```python
import requests

resp = requests.get("https://httpbin.org/get")
data = resp.json()
print(type(data)) # shows a dict type
```

#### GET Parameters

Since http get requests do not take a body like post requests do, if we need to pass arguments with them we do so in the url itself as a *query string*

To send arguments with our get requests using the python requests library we can use the `params=` keyword argument of the `.get()` method.

In the example below we send `fish` as the value of a parameter called `q` - the google search engine uses a parameter called `q` to handle the query it has been sent - this is what we are imitating here.

```python
import requests

# create a dictionary which contains the names of the arguments we are sending along with their values
params = {
    "q": "fish"
}

resp = requests.get("https://httpbin.org/get",
                    params=params) # sends the dictionary of arguments and their values

print(resp.json()["args"])
```

>[!IMPORTANT]
>When we want to send arguments using *GET* it is best to put them into a *dictionary* and then pass the dictionary as the value for the `params=` keyword argument rather than putting them into the *URL* directly as a *query string*

#### Setting Headers

We can set the values of our request headers and we can set custom headers.

The best way is to create a dictionary which contains the header names along with their values and then send this dictionary as the value of the `headers=` keyword argument of the `.get()` method.

```python
import requests

# create a dictionary which contains the names of the headers we are sending along with their values
headers = {
    "Accept": "application/json",
    "X-USER": "anonymous"
}

resp = requests.get("https://httpbin.org/get",
                    headers=headers) # sends the dictionary of headers and their values

print(resp.json())
```

>[!NOTE]
>Custom headers often begin with `X` as in the example above `X-USER`

### Response Status Code

We can check if a request was successful or not by checking the value of the `.ok` attribute of our returned *requests Response* object like so `print(resp.ok)`

If we see `True` we know our request was successful - this could be a 3XX server response status code as well as a 2XX response status code.

If we see `False` it means our request was not successful.

>[!NOTE]
>We can check the exact response status code using `print(resp.status_code)`

#### Summary of HTTP Response Status Codes

We will quickly summarize http response status codes here just in case 2XX and 3XX make no sense.

The XX part represent other digits - we can generalize what responses mean by going off their first digit - the rest of the digits give us more detail.

- 2XX | successful request
- 3XX | redirection
- 4XX | client side error
- 5XX | server-side error

### POST Requests

When we use an http *POST* request we are posting data to an online resource. An example of this would be sending login credentials to a login form.

We can use the `.post()` method from the *requests* library to do this.

A common way to post data online is via a form - we can see an example of replicating this below.

```python
import requests

# create a dictionary which contains the data we want to post
data = {
    "username": "dduck",
    "password": "duckyduckduckducker"
}

resp = requests.post("https://httpbin.org/post", data=data)

print(resp.json())
```

#### POST JSON

If we are posting data to an *API* we tend to use a serialized language such as *JSON* or *XML*

To do this we can simply use `json=` instead of `data=`

```python
import requests

# create a dictionary which contains the data we want to post
data = {
    "username": "dduck",
    "password": "duckyduckduckducker"
}

resp = requests.post("https://httpbin.org/post", json=data) # we send the data using json encoding

print(resp.json())
```
### Application Programing Interfaces

An *API* lets us interact with external resources - we use them to get data which we want to use in our programs.

The api is essentially a way to get data from a web app - it will be set up to have rules in place regarding how we can get the data and which data we can get. If we follow these rules we will be able to get what we want.

An abstraction is to see an api as a menu which specifies what we can get from the kitchen of a restaurant.

A more traditional way of developing a web app is to create a *user interface* using html and css on the server - this web app is then requested by clients and the *html code* is sent along with the *data*.

We might however already have the user interface developed - this could be the case with a mobile app which has been built in something like android studio. The user interface in this case has already been developed, so html is not needed from the server - just the data - so a rest api is used.

A single page web app also just needs data to work with as it will use javascript on the frontend to develop the user interface.

We might also just want data from an api to include in our web app such as location data from google maps or moon rise and set times from a weather api - we don't want a load of html as well as the data in these cases.

Fancy user interfaces with lots of html and css are for humans not machines - we could see an api as a web app for web apps - they are more machine friendly because the unnecessary html and css is not sent - just the requested data.

Essentialy with an api we transfer data instead of user interfaces.

#### API Endpoints

An api endpoint is a location which is usually a url such as [ISS Location](http://api.open-notify.org/iss-now.json)

We need to make a request for data - this will be sent to the api endpoint.

>[!NOTE]
>Data returned from apis is usually JSON but sometimes it will be XML

```python
import requests

url = "http://api.open-notify.org/iss-now.json"

resp = requests.get(url=url)
data = resp.json()
print(data)
```

As an example of working with data returned from an api we can consider this example in which we extract the *latitude* and *longitude* of the ISS at the current time and store it in a *tuple*

```python
import requests

url = "http://api.open-notify.org/iss-now.json"

resp = requests.get(url=url)
data = resp.json()

# extract just the latitude and longitude
lat = data["iss_position"]["latitude"]
long = data["iss_position"]["longitude"]

# store the data in a tuple
iss_location = (lat, long)

print(iss_location)
```

#### API Parameters

Some apis require us to specify parameterss - the documentation will let us know the format needed including datatypes to send.

Some parameters are required whilst others are optional. The optional params will have default values.

The api [sunrise-sunset](https://api.sunrise-sunset.org/json) takes parameters such as *latitude* and *longitude*

Here is an example of getting the sunrise and sunset times for a specified location - %00 Island - by sending latitude and longitude as parameters to the aforementioned api

```python
import requests

url = "https://api.sunrise-sunset.org/json"

params = {
    "lat": 0,
    "lng": 0
}

resp = requests.get(url=url,
                    params=params
                    )

data = resp.json()
sunrise = data["results"]["sunrise"]
sunset = data["results"]["sunset"]
sun_data = (sunrise, sunset)
print(sun_data)
```
