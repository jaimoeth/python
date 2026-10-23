<div align="center">

---
# Python Basics
[![MIT OCW](https://img.shields.io/badge/MIT%20OCW-6.0001-green?style=flat-square&logo=massachusettsinstituteoftechnology)](https://ocw.mit.edu/courses/6-0001-introduction-to-computer-science-and-programming-in-python-fall-2016/)
[![Instructors](https://img.shields.io/badge/Instructors-Bell%20%7C%20Grimson%20%7C%20Guttag-green?style=flat-square)](https://ocw.mit.edu/courses/6-0001-introduction-to-computer-science-and-programming-in-python-fall-2016/)
[![LICENSE](https://img.shields.io/badge/LICENSE-CC%20BY--NC--SA-green?style=flat-square)](https://github.com/jaimoeth/python/blob/main/LICENSE)
[![GitHub](https://img.shields.io/badge/GitHub-python--basics-green?style=flat-square&logo=github)](https://github.com/jaimoeth/python/blob/main/01-python-basics.ipynb)

---
</div>

## 1. Function and Calculation
### 1.1 Comment
```python
# This is a single-line comment.

# Multi-line comments can be written using multiple '#'.
# In many code editors, select multiple lines and press
# Ctrl + / to comment or uncomment them.

"""
This is a multi-line string, not a comment.
It can be used as a docstring when placed at the beginning
of a module, function, or class.
"""
```
### 1.2 Function
```python
# 1. Define a function
def fun_name(input_value):
    """
    This is the docstring of the function.
    It describes what the function does.
    Returns the input value.
    """
    # This is the body of the function.
    output_value = input_value
    return output_value

# 2. Call the function and print the result
print("This is the function value:", fun_name(1))
```
### 1.3 Calculation
```python
# User Input
# The default input is "string".
input_num = input("This is a prompt text.")

# Cast the type to "int"
int_num = int(input_num)

# Cast the type to "float"
float_num = float(input_num)

# Keep 2 decimal places
round_num = round(float_num, 2)

# Mathematical symbols
# +     | addition
# -     | subtraction
# *     | multiplication
# /     | division
# //    | integer division
# %     | modulo
# **    | exponentiation
```
### 1.4 Exercise
Calculate the difference in area:
* Ask the user to input a value for `length`, 
* which serves as both the radius of a circle and the side length of a square. 
* Calculate the difference in area between the two shapes.
---
> Round the result to 2 decimal places.
```python
# 1. Define a function
def area_difference(input_length):
    """
    Calculate the difference in area
    """
    pi = 3.1415926535897932384
    area_circle = pi * input_length ** 2
    area_square = input_length ** 2
    difference = round(area_circle - area_square, 2)
    return difference

# 2. # Main Program
# User Input
length = float(input("Please enter the length: "))

# Calculate the difference in area
area_diff = area_difference(length)

# Print the difference
print("The difference in area is: ", area_diff)
```
## 2. Branching and Iteration
### 2.1 Conditional Branching
```python
# User Input
int_num = int(input("Please enter an int number: "))

# Conditional Branching
# "and" signifies the intersection of two conditions.
# "or" signifies the union of two conditions.
if -10 <= int_num <= 10 and int_num == 0:
    print("This is zero.")
elif int_num == -1 or int_num == 1:
    print("The absolute value of this number is one.")
else:
    print("I don't recognize this number.")
```
### 2.2 While Loop
```python
# Initialize Counter
n = 0

# While Loop
# Execute if the condition is met.
# "break" is used to exit the current loop.
while n <= 5:
    n += 1
    print("I'm number", n)
    if n == 4:
        break
```
### 2.3 For Loop
```python
# For Loop

# range(5)
# Execute 5 times, starting from 0
# range(1, 7, 2)
# Starting from 1, count every 2 units, 
# up to (but not including) 7.
for n in range(4):
    print("I'm number", n+1)

# String Index
word = "example"
print(word[3])

# Alphabetical Indexing Format
# Use len() to calculate the length of a variable.
for index in range(len(word)):
    if word[index] == "m":
        print("This word contains an 'm'.")
        break

# Standard Format
for search in word:
    if search == "m":
        print("This word contains an 'm'.")
        break
```
### 2.4 Exercise
Escape the Lost Forest:

The game interface is a 20x7 grid, with the top and bottom two rows representing a forest, and the middle three rows representing a path.

Define the input range such that the user’s starting position is located on the path.

Allow the user to choose a direction to move. 

If the user turns right, the game should indicate that they are still in the forest. 

If the user turns right two or more times, any subsequent right turn will cause the player to have an emotional breakdown; a single left turn, however, will allow the player to successfully escape the forest.
```python
# 1. Define all functions
def range_check (input_num, min_value, max_value):
    """
    Check whether the input value "input_num" 
    falls within the range [min_value, max_value];
    if it is outside this range,
    prompt for input again 
    until the value falls within the range;
    return the final input value that lies within the range.
    """
    while True:
        if min_value <= input_num <= max_value:
            output_num = input_num
            break
        else:
            print(
                "Please ensure the input is between", 
                min_value, "and", max_value, "."
            )
            input_num = int(input("Please re-enter: "))
    return output_num

def forest_create (map_role, length, width):
    """
    Input the forest location and character coordinates, 
    then render the images of the forest and the character.
    The letter "o" represents a road.
    """
    for index in range(len(map_role)):
        if map_role[index] != "o":
            print(20 * "*")
        else:
            if width == index + 1:
                print((length - 1) * " " + "O")
            else:
                print(" ")

def path_check (input_path):
    """
    Check whether the input "input_path" is "left";
    if it is "right", prompt for re-entry, 
    and trigger a crash after two such attempts;
    if it is any other string, 
    display a prompt indicating that the input is invalid.
    """
    n = 0
    while True:
        if input_path == "left":
            output_str = "Congratulations on your departure!"
            break
        elif input_path == "right":
            n += 1
            print(
                "You failed to leave the forest; "
                "please enter a direction again!"
            )
            if n > 2:
                print("Aaaaaaaaaaaaa!!!!")
            input_path = input(
                "Please choose your direction: left or right"
            )
        else:
            input_path = input(
                "Please enter a valid path: left or right"
            )
    return output_str

# 2. # Main Program
# Initial User Coordinate Input
people_length = range_check(
    int(input("Please enter the x-coordinate: ")), 
    1, 
    20
)
people_width = range_check(
    int(input("Please enter the y-coordinate: ")), 
    3, 
    5
)

# Plotting of initial user coordinates
forest_create("xxoooxx", people_length, people_width)

# Escape the Lost Forest
people_path = path_check(
    input("Please choose your direction: left or right")
)
print(people_path)
```