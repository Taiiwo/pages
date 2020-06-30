Quick Guide to The Basics of Programming with Python
=======================

Introduction
----------
This is a guide that will attempt bring everyone that reads it up to a base level of knowledge on programming, before you can start learning higher concepts. I'd recommend you read this guide, even if you already know a bit about programming, just to make sure there aren't any gaps in your base understanding. I've tried to write the guide so that it can be understood by anyone at any level, but if you get stuck, don't hesitate to ask!

How to Run Python Code
--------------------------------
Python is a programming language. You can download Python for your operating system (Probably windows) from the [python website](https://www.python.org/). Once you have it installed, you will be able to write your code into a text file (with the .py extension) and double click it to run. This isn't the best way to run Python code, but it's a simple way to understand.

Another simple way to run python code is from the command line. Installing Python will add a new command to the command line (If you select the PATH option on install) which lets you run `python filename.py`. In windows, you can open a new Command Prompt window by typing "cmd" into the address bar of the folder you want to run code in:

![](https://thumbs.gfycat.com/OddReflectingIndigowingedparrot-size_restricted.gif)

Writing Code
----------------
Code works like a list of instructions kind of like a recipe, and Python is no exception. The very basic purpose of each instruction is to move bits of data between variables. In Python, we can store data inside a variable like this:

```python
some_string = "Hello!"
a_list = ["a", "list", "of", "strings"]
my_integer = 1 + 1 # stores 2
a_float = my_integer - 0.5 # stores 1.5
```

Now storing data inside of variables is very important, but it's not how the work gets done! Code is only useful when we process the data, and we have many tools that help us to do this. The main tools are conditions, loops, and functions.

Conditions
-------------
A conditional statement allows you to control the flow of execution based on the outcome of an expression. In Python we can use `if` statements like this:
```python
if 1 + 1 == 2:
	print("It works!")
else:
	print("How did this happen?")
```
Notice how the sections of the statements have whitespace before them, creating blocks. This allows us to easily see which bits of code belong to which statement.

Here we are directing the flow of the program between two paths. Now obviously in this statement, 1 + 1 is always going to be equal to 2, but imagine what other things this could be useful for when we don't know the outcome of the condition:

```python
if is_raining:
	bring_umbrella()

if door.is_open:
	walk_through_door()
else:
	open_door()
	walk_through_door()
```
Note that `if` statements don't require an `else` block.

Loops
-------
Loops are what allow us to save a lot of time in programming. Computers are able to run loops very quickly, and we should try and use this to our advantage. The following is a for loop:

```python
words = ["This", "is", "an", "example"]
for word in words:
	print(word)
```
The above code is a much shorter way of writing:
```python
print("This")
print("is")
print("an")
print("example")
```
It allows us to go quickly through a list of things, and do something with each of them. For example, closing all the doors in a house:
```python
for door in house.doors:
	door.close()
```

Functions
------------
Writing code can quickly become complicated and repetitive, even when using loops! We can do ourselves a favour by putting code neatly into functions. They allow us to simplify actions so they can be used later:
```python
def add(a, b):
	return a + b
```
The above function takes 2 arguments, `a` and `b`, and returns their sum. Notice the `return` keyword. The `return` keyword submits the output of the function so that it can be used:
```python
output = add(1, 1)
```

Functions allow us to abstract actions, for example:
```python
def close_all_doors(house):
	for door in house.doors:
		door.close()
```
Now we can close all the doors of a given house by running:
```python
close_all_doors(house)
```

Classes / Objects
---------------------
Python is an object oriented language. This means that it implements objects, which are an abstraction used to organise data and functions into easy to understand code. We've actually been using objects throughout this guide already. `house` and `door` are examples of objects that I've used to abstract more complicated concepts such as actually interacting with the world.

Let's say we have a servo motor that controls the opening and closing of a door. At position 0, the servo motor closes the door, and at position 10, the door is open. We could open the door by typing something like:
```python
servo.move_to(10)
```
Which is a nice abstraction of the movement of a servo, but could be a bit confusing in the context of trying to open and close a door. So let's create our own door object that makes a bit more sense.

A Class is a constructor that is used to create objects. To start making our door objects, we need to define a door class.
```python
class Door:
	def __init__(self, servo):
		self.servo = servo
```
Within our new door class is a function called `__init__`. This function is run when a new object is created, and in this case, is used to store the `servo` argument internally, for use later.

The next thing we need to to is give our objects some `methods`. A method is a function that runs within the context of an object. Here's an example:

```python
class Door:
	def __init__(self, servo):
		self.servo = servo

	def open(self):
		self.servo.move_to(10)
```
Here we've added an `open` method to our door, containing the code we wrote earlier to use the servo to open the door.

Notice that each method has the `self` variable as it's first argument. This is to give each method a reference to it's parent object.

We can test out our object like this:
```python
door = Door(servo)
door.open()
```
Here we pass the servo object into our Door class to construct a door object. We can then use our `open` method to open the door in a more understandable way.

Modules and Libraries
---------------------------
Python comes with a rich library of Modules, that contain useful abtractions of actions that can be performed by the language. Modules are installed using the `pip` command:
```batch
python -m pip install some-module
or
pip install some-module
```
Or you can write them yourself, and include them from the working directory of your script. A module is created by making a folder containing the `__init__.py` file. Code in that file will be run when the module is imported, and other files in the module can be imported as attributes.

But how do I make it do stuff?
------------------------------------
This was my main question when I started learning programming. Yea, adding number together is interesting, but how to I make code that's actually useful? One of the best things to help you create useful applications is to try to implement an API. API stands for Application Programming Interface, and there are thousands of them for just about everything. Most of the websites and applications you use will have an API. Social media and instant messengers almost always have an API, for example. APIs sometimes have wrapper modules you can get from pip, so it can be really easy to get started. You should pick something simple to start with, but get creative!
