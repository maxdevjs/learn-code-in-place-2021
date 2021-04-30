# Lesson 5: Expressions April 28th

<details open>
<summary>Learning Goals</summary>
<br />
Learn how to calculate arithmetic (math) expressions using python. Learn how to use constants and learn how to use the random number generator!
</details>

 ## Videos

- [x] Intro
- [x] Expressions
    - arithmetic stuff: (), **, - (negation) *, /, //, %, + and -
- [x] CONSTANTS 🤭
- [x] Math Library
- [x] Random Numbers
- [x] dicesimulator

<details>

`helloworld.py`
```python
def main():
    print("hello, world!")

if __name__ == '__main__':
    main()
```
</details>

## Assignments Problems

<details>
<summary>Q1: Hello <name>!</summary>
<details open>
<summary>Description</summary>
We write a customizable version of the classic "hello world!", prompting the user to input the name.
</details>
<details>
<summary>Code</summary>

`hello.py`
```python
"""
Prompts the user for their name and then says hello!
"""


def main():
    # print("Hello", input("What is your name? "), "\b!")
    name = input("What is your name? ")
    print("Hello " + name + "!")


if __name__ == '__main__':
    main()
```
</details>
</details>
<hr />

<details>
<summary>Q2: Mad Libs</summary>
<details open>
<summary>Description</summary>
In this assignment we add one line of code to complete the story of Karel the Omniscient.

Mad Libs is a word game where players are prompted for one word at a time, and the words are eventually filled into the blanks of a word template to make an entertaining story!

No idea about it 🤔
</details>
<details>
<summary>Code</summary>

`madlibs.py`
```python
"""
Uses constants to tell a mad libs story.
"""

# Fun fact: 6174 is known as Kaprekar's constant,
# and it's a pretty mysterious number :)

WIZARD = 'Karel the Omniscient'
NUMBER_OF = 6174
FRUIT = 'mangoes'
PRICE = 2.99
YEARS = 300


def main():
    print("There once was a wizard by the name of " + WIZARD + " who loved to eat " + FRUIT + ".")
    print(WIZARD + " always kept a stash of " + str(NUMBER_OF) + " " + FRUIT + " in their mini fridge!")
    print(WIZARD + " realized they couldn't keep all those " + FRUIT + " to themselves,")
    print("so they sold them at the market for $" + str(PRICE) + " apiece,")
    print("and with the earnings bought fruit to share with the entire village!")
    # Added line:
    print("Legend says", YEARS, "years later,", WIZARD, "is still eating fruit.")


if __name__ == '__main__':
    main()
```

</details>
</details>
<hr />

<details>
<summary>Q3: Subtract Numbers</summary>
<details open>
<summary>Description</summary>
We read two real numbers from the user and prints the first number minus the second number.
</details>
<details>
<summary>Code</summary>

`subtract_numbers.py`
```python
"""
Asks the user for two numbers and prints the result
of the first number minus the second number.
"""


def main():
    print("This program subtracts one number from another.")
    n1 = float(input("Enter first number: "))
    n2 = float(input("Enter second number: "))
    print("The result is", n1 - n2)


if __name__ == '__main__':
    main()
```
</details>
</details>
<hr />

<details>
<summary>Q4: Random Numbers</summary>
<details open>
<summary>Description</summary>
Let's print 10 random integers (each random integer should have a value between 0 and 100, inclusive).
</details>
<details>
<summary>Code</summary>

`random_numbers.py`
```python
"""
Prints out 10 random numbers between 0 and 100.
"""

import random

NUM_RANDOM = 10
MIN_RANDOM = 0
MAX_RANDOM = 100


def main():
    for i in range(NUM_RANDOM):
        print(random.randint(MIN_RANDOM, MAX_RANDOM))


if __name__ == '__main__':
    main()
```
</details>
</details>
<hr />

<details>
<summary>Q5: Liftoff!</summary>
<details open>
<summary>Description</summary>
Countdown from 10 to 1 and then output `Liftoff` to the 🚀!
</details>
<details>
<summary>Code</summary>

`liftoff.py`
```python
"""
Prints out a spaceship launch sequence.
"""

NUM = 11


def main():
    for i in range(NUM):
        if i == 0:
            pass
        else:
            print(NUM - i)
    print("Liftoff!")


if __name__ == '__main__':
    main()
```
</details>
</details>
<hr />

## Optional Worked Examples

- [ ] Console Examples (a few billions)

 ## Optonal Related Reading

- [ ] [Lecture Slides](https://codeinplace2020.github.io/faqs/5-Expressions.pdf)
- [x] [Expressions](https://codeinplace2021.github.io/pythonreader/en/math/)
- [x] [Constants](https://codeinplace2021.github.io/pythonreader/en/constants/)
- [x] [Random](https://codeinplace2021.github.io/pythonreader/en/random/)
