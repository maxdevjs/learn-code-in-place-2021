# Lesson 6: Control Flow Revisited April 30th

<details open>
<summary>Learning Goals</summary>
<br />
The dance of variables with control flow.
</details>

 ## Videos

- [x] Recap

<details>
<summary>Code</summary>

`carbondate.py`
```python
K = -8266.64258429376


def main():
    calculate_age_single_sample():


def calculate_age_single_sample():
    # ask the user to enter the percent of c14 left in their sample
    pct_left = float(input(% of natural c14: ))
    # calc the age
    age = K + math.log(pct_left / 100)
    # print the result
    print("Sample is", str(age), "years old.")
```
</details>

- [x] While/If
- [x] Guess My Number

<details>
<summary>Code</summary>

`carbondate.py`
```python
import random


def main():
    secret_number = random.randint(1, 99)
    guess = int(input("Guess a number between 1 and 99..."))
    while guess != secret_number:
        if guess < secret_number:
            print("Too low")
        else:
            print("Too high")
        print("")
        guess = int(input("Guess a number between 1 and 99..."))
    print("Congrats! The number was:", str(secret_number))


if __name__ == '__main__':
    main()
```
</details>

- [ ] Sentinel

<details>
<summary>Code</summary>

`carbondate.py`
```python
def main():
    number = int(input("Enter a number, -1 to stop: "))
    tot = 0
    while number != -1:
        tot += number
        number = int(input("Enter a number, -1 to stop: "))
    print("Tot:", tot)


if __name__ == '__main__':
    main()
```
</details>


- [x] Booleans
- [x] For Loops
- [x] Game Show Teaser: on Monday!

## Assignments Problems

<details>
<summary>Q5: Liftoff!</summary>
<details open>
<summary>Description</summary>
🚀 countdown.
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

Or, infinitely better:

```python
"""
Prints out a spaceship launch sequence.
"""
def main():
    for i in range(10,0,-1):
        print(i)
    print("Liftoff!")

if __name__ == '__main__':
    main()
```
</details>
</details>
<hr />

<details>
<summary>Q6: Khansole Academy</summary>
<details open>
<summary>Description</summary>
This program is intended to help people to learn randomly generating two numbers, asking the user for the answer, checking for correctness, and informing a message to communicate if the user input is the right value.
</details>
<details>
<summary>Code</summary>

`khansole_academy.py`
```python
"""
Prints out a randomly generated addition problem
and checks if the user answers correctly.
"""

import random


def main():
    khansole_academy()


def khansole_academy():
    n1 = random.randint(0, 100)
    n2 = random.randint(0, 100)
    tot = n1 + n2

    question = "What is " + str(n1) + " + " + str(n2) + "? "
    print(question)
    answer = ''

    while True:
        try:
            answer = int(input())
            break
        except ValueError:
            print("Answer must be an integer")

    print("Your answer:", answer)

    if (answer == tot):
        print("Correct!")
    else:
        print("Incorrect. The expected answer is", tot)


if __name__ == '__main__':
    main()
```
</details>
</details>
<hr />

<details>
<summary>Q7 (optional): Khansole Academy, Extension</summary>
<details open>
<summary>Description</summary>
As the previous, in a loop.
</details>
<details>
<summary>Code</summary>

`khansole_academy.py`
```python
"""
TODO: Write a description here
"""

import random

NUM_CORRECT_IN_A_ROW = 3


def khansole_academy():
    num_of_correct_answers = 0

    while num_of_correct_answers < NUM_CORRECT_IN_A_ROW:
        n1 = create_random_number()
        n2 = create_random_number()
        tot = n1 + n2

        question = "What is " + str(n1) + " + " + str(n2) + "? "
        print(question)
        answer = ''

        while True:
            try:
                answer = int(input())
                break
            except ValueError:
                print("Answer must be an integer")

        print("Your answer:", answer)

        if (answer == tot):
            num_of_correct_answers += 1
            print("Correct!", num_of_correct_answers)
        else:
            print("Incorrect. The expected answer is", tot)
            num_of_correct_answers = 0

        if num_of_correct_answers == NUM_CORRECT_IN_A_ROW:
            print("Congratulations! ...")
            break


def create_random_number():
    return random.randint(0, 100)


def main():
    khansole_academy()


if __name__ == '__main__':
    main()
```
</details>
</details>
<hr />

<details>
<summary>(optional) Extension</summary>
<details open>
<summary>Description</summary>
<h3>Optional Extensions</h3>

Once you’ve completed all the required parts of the assignment, you might want to consider adding some extensions. Extensions, you may recall, are things that are totally optional. Here are some extra programs to write if you are interested – but feel free to just make something cool!

<h3>Extend Khansole Academy</h3>

You could consider extending your Khansole Academy program to, for example, add more problem types (subtraction, multiplication, division, and more). You could also consider problems beyond arithmetic. If you could build your own version of Khansole Academy, what would you use it to help people learn? Be creative and enjoy.

<h3>AI for Game of Nimm</h3>

Can you make a computer player that can always win in a game of Nimm?

<h3>Hailstones</h3>

A separate (optional) problem you could consider writing is based on a problem in Douglas Hofstadter’s Pulitzer-prize-winning book Gödel, Escher, Bach. That book contains many interesting mathematical puzzles, many of which can be expressed in the form of computer programs. In Chapter XII, Hofstadter mentions a wonderful problem that is well within the scope of what you know. The problem can be expressed as follows:

<i>
Pick some positive integer and call it n.
If n is even, divide it by two.
If n is odd, multiply it by three and add one.
Continue this process until n is equal to one.
</i>

On page 401 of the Vintage edition of his book, Hofstadter illustrates this process with the following example, starting with the number 15:

```
15 is odd, so I make 3n+1: 46
46 is even, so I take half: 23
23 is odd, so I make 3n+1: 70
70 is even, so I take half: 35
35 is odd, so I make 3n+1: 106
106 is even, so I take half: 53
53 is odd, so I make 3n+1: 160
160 is even, so I take half: 80
80 is even, so I take half: 40
40 is even, so I take half: 20
20 is even, so I take half: 10
10 is even, so I take half: 5
5 is odd, so I make 3n+1: 16
16 is even, so I take half: 8
8 is even, so I take half: 4
4 is even, so I take half: 2
2 is even, so I take half: 1
```

As you can see from this example, the numbers go up and down, but eventually—at least for all numbers that have ever been tried—comes down to end in 1. In some respects, this process is reminiscent of the formation of hailstones, which get carried upward by the winds over and over again before they finally descend to the ground. Because of this analogy, this sequence of numbers is usually called the Hailstone sequence, although it goes by many other names as well.

You might want to write a Python program that reads in a number from the user and then displays the Hailstone sequence for that number, just as in Hofstadter’s book, followed by a line showing the number of steps taken to reach 1. For example, here’s a sample run of what such a program might look like (user input is in bold italics):

```
Enter a number: 17
17 is odd, so I make 3n + 1: 52
52 is even, so I take half: 26
26 is even, so I take half: 13
13 is odd, so I make 3n + 1: 40
40 is even, so I take half: 20
20 is even, so I take half: 10
10 is even, so I take half: 5
5 is odd, so I make 3n + 1: 16
16 is even, so I take half: 8
8 is even, so I take half: 4
4 is even, so I take half: 2
2 is even, so I take half: 1
The process took 12 steps to reach 1
```

</details>
<details>
<summary>extension.py</summary>

`extension.py`
```python
"""
TODO: Write a description here
"""


def main():
    hailstone(int(input("Enter a number:  ")))


def hailstone(number):
    # n = 0

    while True:
        if number == 1:
            break
        if number % 2 == 0:
            number = int(number / 2)
            print(f"{number} is even, so I take half: {number}")
        else:
            number = 3 * number + 1
            print(f"{number} is odd, so I make 3n + 1: {number}")


if __name__ == "__main__":
    main()
```

```sh
Enter a number:  46
23 is even, so I take half: 23
70 is odd, so I make 3n + 1: 70
35 is even, so I take half: 35
106 is odd, so I make 3n + 1: 106
53 is even, so I take half: 53
160 is odd, so I make 3n + 1: 160
80 is even, so I take half: 80
40 is even, so I take half: 40
20 is even, so I take half: 20
10 is even, so I take half: 10
5 is even, so I take half: 5
16 is odd, so I make 3n + 1: 16
8 is even, so I take half: 8
4 is even, so I take half: 4
2 is even, so I take half: 2
1 is even, so I take half: 1
```
</details>
</details>
<hr />

## Section problems

<details>
<summary>Mars Weight</summary>
<details open>
<summary>Description</summary>
Last Monday, NASA made history with the first controlled flight on another planet. Its latest Mars Rover, Perseverance, has onboard a 50cm high helicopter called Ingenuity. On Sunday, Ingenuity made its <a href="https://www.nytimes.com/2021/04/25/science/mars-helicopter-nasa.html">third flight</a>, during which it flew faster and further than it had on any of its test flights on Earth. Interestingly, Ingenuity <a href="https://github.com/readme/nasa-ingenuity-helicopter">uses Python</a> for some of its flight modeling software!

When programming Ingenuity, one of the things that NASA engineers need to account for is the fact that due to the weaker gravity on Mars, an Earthling's weight on Mars is 37.8% of their weight on Earth. Write a Python program that prompts an Earthling to enter their weight on Earth and prints their calculated weight on Mars.
</details>
<details>
<summary>Code</summary>

`marsweight.py`
```python
"""
Prompts the user for a weight on Earth
and prints the equivalent weight on Mars.
"""


def main():
    # Fill this function out!
    # earthling_weight = float(input("What is your weight on Heart: "))
    # sigh... :)
    print("The equivalent on Mars:",
        float(input("Enter a weight on Earth: ")) * 0.378)


if __name__ == "__main__":
    main()
```
</details>
</details>
<hr />

<details>
<summary>8-ball</summary>
<details open>
<summary>Description</summary>
The idea behind an 8-ball is very simple. You ask it a yes or no question, and it tells you the answer. The catch is that the answer it chooses is randomly selected from a set of prefabricated responses.
</details>
<details>
<summary>Code</summary>

`8ball.py`
```python
"""
Simulates a magic eight ball.
Prompts the user to type a yes or no question and gives
a random answer from a set of prefabricated responses.
"""
import random


def main():
    answers = ["As I see it, yes.", "Ask again later."]

    while True:
        # question = input("Ask a yes or no question: ")
        # if question == "":
        if input("Ask a yes or no question: ") == "":
            break
        answer = random.randint(0, 1)
        print(answers[answer])


if __name__ == "__main__":
    main()
```
</details>
</details>
<hr />

## Optional Worked Examples

- [x] Lecture Examples

<details>
<summary>Carbon Dating</summary>
<details open>
<summary>Description</summary>
Write a program to calculate how old something is.

Input: what percent of c14 is remaining in the sample?

Output: age of the sample, in years
</details>
<details>
<summary>Code</summary>

`carbondate.py`
```python
import math

# The constant K in the half life formula
K = -8266.64258429376

def main():
    calculate_age_single_sample()

def calculate_age_single_sample():
    # Ask the user to enter the percent of c14 left in their sample
    pct_left = float(input("% of natural c14: "))
    # Calculate the age: https://en.wikipedia.org/wiki/Radiocarbon_dating
    age = K * math.log(pct_left / 100)
    # Print the result
    print("Sample is " + str(age) + " years old.")

if __name__ == '__main__':
    main()
```
</details>
</details>
<hr />

<details>
<summary>Equals Contrast</summary>
<details open>
<summary>Description</summary>
/shrug
</details>
<details>
<summary>Code</summary>

`.py`
```python

```
</details>
</details>
<hr />

<details>
<summary>Guess My Number</summary>
<details open>
<summary>Description</summary>
Guessing a number between 1 and 99.
</details>
<details>
<summary>Code</summary>

`guess_number.py`
```python
"""
Generates a random number between 1 and 99.
Has the user keep guessing until they figure out
what the number is. Tells the user after each guess
if their guess was too high or too low.
"""

import random

def main():
    secret_number = random.randint(1, 99)
    print("I am thinking of a number between 1 and 99...")
    guess = int(input("Enter a guess: "))
    # True if guess is not equal to secret number
    while guess != secret_number:
        # True if guess is less than secret number
        if guess < secret_number:
            print("Your guess is too low")
        else:
            print("Your guess is too high")
        print("") # an empty line
        guess = int(input("Enter a new guess: "))
    print("Congrats! The number was: " + str(secret_number))

if __name__ == '__main__':
    main()
```
</details>
</details>
<hr />

<details>
<summary>Sentinel Loops</summary>
<details open>
<summary>Description</summary>
When the user inputs `-1`, the world ends!
</details>
<details>
<summary>Code</summary>

`sentinel.py`
```python
"""
Asks the user for a number until they enter -1
Reports the total value of all the numbers at the end
"""


def main():
    number = int(input("Enter a number, -1 to stop: "))
    tot = 0
    while number != -1:
        tot += number
        number = int(input("Enter a number, -1 to stop: "))
    print("Tot:", tot)


if __name__ == '__main__':
    main()
```
</details>
</details>
<hr />

<details>
<summary>Print Even Numbers</summary>
<details open>
<summary>Description</summary>
Program to print the first 100 even numbers
</details>
<details>
<summary>Code</summary>

`print_even.py`
```python
"""
Example of using the index variable of a for loop
"""

def main():
    for i in range(100):
        # in a for loop, you have access to
        # a variable which knows how many times the loop
        # has completed
        print(i * 2)

if __name__ == '__main__':
    main()

```
</details>
</details>
<hr />

- [ ] Console Examples

<details>
<summary>Square number</summary>
<details open>
<summary>Description</summary>
Ask the user for a number and print its square (the product of the number times itself).

<div>
<p>$ python square.py</p>
<p>Type a number to see its square: 4</p>
<p>4.0 squared is 16.0</p>
</div>
</details>
<details>
<summary>Code</summary>

`square.py`
```python

def main():
    # incorrect, but...
    print(
        "squared is",
        pow(float(input("Type a number to see its square: ")), 2)
    )


if __name__ == "__main__":
    main()
```
</details>
</details>
<hr />

<details>
<summary>Perimeter of a triangle</summary>
<details open>
<summary>Description</summary>
Prompt the user to enter the lengths of each side of a triangle and then calculate and print the perimeter of the triangle (the sum of all of the side lengths).
</details>
<details>
<summary>Code</summary>

`perimeter.py`
```python
sides = []


def main():
    ask_length_sides()


def ask_length_sides():
    for i in range(3):
        text = "What is the length of side " + str(i + 1) + "? "
        # print(sides)
        sides.append(float(input(text)))
    calc_perimeter(sides)


def calc_perimeter(sides):
    perimeter = 0
    for i in range(len(sides)):
        # print(sides[i])
        perimeter += sides[i]
    print("The perimeter of the triangle is", perimeter)


if __name__ == "__main__":
    main()
```
</details>
</details>
<hr />

<details>
<summary>Fahrenheit to Celsius</summary>
<details open>
<summary>Description</summary>
Write a program which prompts the user for a temperature in Fahrenheit (this can be a number with decimal places!) and outputs the temperature converted to Celsius.
</details>
<details>
<summary>Code</summary>

`f_to_c.py`
```python
def main():
    convert_F_to_C()


def convert_F_to_C():
    # degrees_celsius = (degrees_fahrenheit - 32) * 5/9
    f = float(input("Enter temperature in Fahrenheit: "))
    print("Temperature: ", f, "\bF =", format((f - 32) * 5 / 9, '.2f'), "\bC")


if __name__ == "__main__":
    main()
```
</details>
</details>
<hr />

<details>
<summary>Remainder division</summary>
<details open>
<summary>Description</summary>
Time to ask the user for two numbers, one at a time, and then print the result of dividing the first number by the second and also the remainder of the division.
</details>
<details>
<summary>Code</summary>

`remainder.py`
```python
def main():
    answer()


def answer():
    num1 = float(input("Please enter an integer to be divided: "))
    num2 = float(input("Please enter an integer to divide by: "))
    print("The result of this division is", int(num1 / num2), "with a remainder of", int(num1 % num2))


if __name__ == "__main__":
    main()
```
</details>
</details>
<hr />

<details>
<summary>Seconds in a year</summary>
<details open>
<summary>Description</summary>
Python will calculate the number of seconds in a year, and tell the user what the result is in a nice print statement with the use constants: there are 365 days in a year, 24 hours in a day, 60 minutes in an hour, and 60 seconds per minute.
</details>
<details>
<summary>Code</summary>

`seconds_per_year.py`
```python
DAYS_PER_YEAR = 365
HOURS_PER_DAY = 24
MINUTES_PER_HOUR = 60
SECONDS_PER_MINUTE = MINUTES_PER_HOUR


def main():
    calculate_seconds_per_year()


def calculate_seconds_per_year():
    seconds_per_year = DAYS_PER_YEAR *\
                        HOURS_PER_DAY *\
                        MINUTES_PER_HOUR *\
                        SECONDS_PER_MINUTE
    print(f"There are {seconds_per_year} per year.")


if __name__ == "__main__":
    main()
```
</details>
</details>
<hr />

<details>
<summary>Tiny mad libs</summary>
<details open>
<summary>Description</summary>
The program prompts the user for an adjective, then a noun, then a verb, and then prints a fun sentence with those words!
</details>
<details>
<summary>Code</summary>

`tiny_mad_libs.py`
```python
SENTENCE_START = "Code in Place is fun. I learned to program and used Python to make my " # adjective noun verb


def main():
    tiny_mad_lib()


def tiny_mad_lib():
    adjective = input("Please type an adjective and press enter. ")
    noun = input("Please type a noun and press enter. ")
    verb = input("Please type a verb and press enter. ")
    print(SENTENCE_START + adjective, noun, verb + "!")


if __name__ == "__main__":
    main()
```
</details>
</details>
<hr />

<details>
<summary>Dog years</summary>
<details open>
<summary>Description</summary>
This program asks an user to input an age in human years, and converts it to the equivalent age in dog years.
</details>
<details>
<summary>Code</summary>

`dog_years.py`
```python
"""
Dogs are man's best friend, but they have different lifespans than humans.
If you divide the average human lifespan by the average lifespan of a dog,
you can calculate the multiplier for converting an age in human years to an
age in dog years. The average lifespan of a human is 79 years and the average
lifespan of a dog is 11 years. So, 1 human year
is equal to 79/11 = 7.18 dog years. To convert, say,
3 human years to dog years,
you'd multiply 3 * 7.18 = 21.54 dog years.
That means, if your dog is 3 years old in human years,
they're past their teenage years in dog years!
"""

MULTIPLIER = 7.18


def main():
    calc_dog_age()


def calc_dog_age():
    human_age = float(input("Enter an age in human years: "))
    print(f"That's {human_age * MULTIPLIER} in dog years!")


if __name__ == "__main__":
    main()
```
</details>
</details>
<hr />

<details>
<summary>E = mc^2</summary>
<details open>
<summary>Description</summary>
Program that continually reads in mass from the user and then outputs the equivalent energy using Einstein's mass-energy equivalence formula (E stands for energy, m stands for mass, and C is the speed of light:

<quote>E = m⋅C2</quote>

Almost 100 years ago, Albert Einstein famously discovered that mass and energy are interchangeable and are related by the above equation. You should ask the user for mass (m) in kilograms and use a constant value for the speed of light -- C = 299792458 m/s.
</details>
<details>
<summary>Code</summary>

`emc2.py`
```python
C = 299792458  # m/s


def main():
    mass_to_energy()


def mass_to_energy():
    mass = float(input("Enter kilos of mass: "))
    print("e = m * C^2...")
    print(f"m = {mass} kg")
    print(f"C {C} m/s")
    print(mass * pow(C, 2), "joules of energy!")


if __name__ == "__main__":
    main()
```
</details>
</details>
<hr />

<details>
<summary>Pythagorean theorem TODO</summary>
<details open>
<summary>Description</summary>
On hold!
</details>
<details>
<summary>Code</summary>

`pythagorean.py`
```python

```
</details>
</details>
<hr />

<details>
<summary>Weighted coin FIXME</summary>
<details open>
<summary>Description</summary>
Write a program which will flip a weighted coin.

Coin flips are usually fair, but can be cheated -- a weighted coin is a coin where the probability of heads isn't 50%. Your code should use the random module to "flip" coin where the probability of heads is 70% and print the outcome (heads or tails).
</details>
<details>
<summary>Code</summary>

`weighted_coin.py`
```python
"""
🙈 Trying solution at: https://edstem.org/us/courses/11037/discussion/408746
It passes, example to study
"""


import random
import math

def main():
    countHeads = int(0)
    countTails = int(0)

    inputFlipCount = int(input("Input how many times you want to simulate a weighted coin: "))
    for i in range(inputFlipCount):
        flipCoin = random.randint(1,10)
        if flipCoin <= 7 :
            countHeads = countHeads+1
        else:
            countTails = countTails+1

    countHeadsPerc = float((countHeads/inputFlipCount)*100)
    countTailsPerc = float((countTails/inputFlipCount)*100)

    print("Results for " + str(inputFlipCount) + " coin flips:")
    print("Heads: " + str(countHeads) + " Probobility: " + str(trim(countHeadsPerc,2)) + "%")
    print("Tails: " + str(countTails) + " Probobility: " + str(trim(countTailsPerc,2)) + "%")

def trim(f, n):
    return math.floor(f * 10 ** n) / 10 ** n


if __name__ == "__main__":
    main()
```
</details>
</details>
<hr />

<details>
<summary>Tall enough to ride</summary>
<details open>
<summary>Description</summary>
Write a program which asks the user how tall they are and prints whether or not they're taller than a pre-specified minimum height.
</details>
<details>
<summary>Code</summary>

`tall_enough.py`
```python
MINIMUM_HEIGHT = 50


def main():
    find_if_tall_enough()


def find_if_tall_enough():
    ask_for_stature()
    # tall_enough(stature)


def ask_for_stature():
    # return float(input("How tall are you? "))

    # extension
    while True:
        try:
            stature = input("\nHow tall are you (enter a number or 'bye' to stop)? ")
            if stature == str("bye"):
                print("\nBye bye")
                break
            tall_enough(int(stature))
        except ValueError:
            print("\nPlease, enter a number or 'bye' to stop!")


def tall_enough(stature):
    if stature >= MINIMUM_HEIGHT:
        print("You're tall enough to ride!")
    else:
        print("\nSorry, you are not tall enough.\nTry again, you will be luckier ")


if __name__ == "__main__":
    main()
```
</details>
</details>
<hr />

<details>
<summary>Wholesome machine</summary>
<details open>
<summary>Description</summary>
Write a program which prompts the user to type an affirmation of your choice (we'll use "I am capable of doing anything I put my mind to.") until they type it correctly. Sometimes, especially in the midst of such uncertain times, we just need to be reminded that we are resilient, capable, and strong; this little Python program may be able to help!
</details>
<details>
<summary>Code</summary>

`wholesome.py`
```python
AFFIRMATION = "I am capable of doing anything I put my mind to."


def main():
    wholesome()


def wholesome():
    user_input = input("Please type the following affirmation: I am capable of doing anything I put my mind to. ")
    while user_input != AFFIRMATION:
        print("\nThat was not the affirmation.\n")
        user_input = input("Please type the following affirmation: I am capable of doing anything I put my mind to. ")
    print("That's right! :)")


if __name__ == "__main__":
    main()
```
</details>
</details>
<hr />

<details>
<summary>Fibonacci FIXME</summary>
<details open>
<summary>Description</summary>
Write a program to print terms in the Fibonacci sequence up to a maximum value.

In the 13th century, the Italian mathematician Leonardo Fibonacci, as a way to explain the geometric growth of a population of rabbits, devised a mathematical sequence that now bears his name. The first two terms in this sequence, Fib(0) and Fib(1), are 0 and 1, and every subsequent term is the sum of the preceding two. Thus, the first several terms in the Fibonacci sequence look like this:

Fib(0) = 0
Fib(1) = 1
Fib(2) = 1 (0 + 1)
Fib(3) = 2 (1 + 1)
Fib(4) = 3 (1 + 2)
Fib(5) = 5 (2 + 3)

Write a program that displays the terms in the Fibonacci sequence, starting with Fib(0) and continuing as long as the terms are less than 10,000 (you should store this value as a constant!).
</details>
<details>
<summary>Code</summary>

`fibonacci.py`
```python
MAX_TERM_VALUE = 10000

def main():
    curr_term = 0
    next_term = 1
    while curr_term <= MAX_TERM_VALUE:
        print(curr_term)
        term_after_next = curr_term + next_term
        curr_term = next_term
        next_term = term_after_next


if __name__ == "__main__":
    main()
```
</details>
</details>
<hr />

<details>
<summary>International voting age</summary>
<details open>
<summary>Description</summary>
Write a program which asks a user for their age and lets them know if they can or can't vote in the following three fictional countries.

In the fictional countries of Peturksbouipo, Stanlau, and Mayengua, the voting ages are very different:

    the voting age in Peturksbouipo is 16 (in real life, this is the voting age in, for example, Scotland, Ethiopia, and Austria)

    the voting age in Stanlau is 25 (in real life this is the voting age in the United Arab Emirates)

    the voting age in Mayengua is 48 (in real life, as far as we can tell, this isn't the voting age anywhere)

Your code should prompt the for their age and print whether or not they can vote in Peturksbouipo, Stanlau, or Mayengua.
</details>
<details>
<summary>Code</summary>

`voting.py`
```python

PETURKSBOUIPO = 16
STANLAU = 25
MAYENGUA = 48


def main():
    can_vote()


def can_vote():
    ask_for_age()


def ask_for_age():
    while True:
        try:
            age = input("\nHow old are you? ")
            if age == str("bye"):
                print("\nBye bye")
                break
            # return age
            elif int(age) < PETURKSBOUIPO:
                print("Sorry, you can not vote nowhere!")
            elif PETURKSBOUIPO <= int(age) < STANLAU:
                print("You can vote in Peturksbouipo where the voting age is 16.")
                print("You cannot vote in Stanlau where the voting age is 25.")
                print("You cannot vote in Mayengua where the voting age is 48.")
            elif STANLAU <= int(age) < MAYENGUA:
                print("You can vote in Peturksbouipo where the voting age is 16.")
                print("You can vote in Stanlau where the voting age is 25.")
                print("You cannot vote in Mayengua where the voting age is 48.")
            else:
                print("You can vote in Peturksbouipo where the voting age is 16.")
                print("You can vote in Stanlau where the voting age is 25.")
                print("You can vote in Mayengua where the voting age is 48.")
        except ValueError:
            print("\nPlease, enter a number or 'bye' to stop!")


if __name__ == "__main__":
    main()
```
</details>
</details>
<hr />

<details>
<summary>Leap year</summary>
<details open>
<summary>Description</summary>
Write a program that reads a year from the user and tells whether a given year is a leap year or not.
</details>
<details>
<summary>Code</summary>

`leap_year.py`
```python
def main():
    year = int(input('Please input a year: '))

    # checking whether the provided year is evenly divisibly by 4
    if year % 4 == 0:
        # checking whether the provided year is evenly divisibly by 100
        if year % 100 == 0:
            # checking whether the provided year is evenly divisibly by 400
            if year % 400 == 0:
                print("That's a leap year!")
            else:
                print("That's not a leap year.")
        else:
            print("That's a leap year!")
    else:
        print("That's not a leap year.")


if __name__ == "__main__":
    main()
```
</details>
</details>
<hr />

<details>
<summary>First person Karel TODO</summary>
<details open>
<summary>Description</summary>

</details>
<details>
<summary>Code</summary>

`karel.py`
```python

```
</details>
</details>
<hr />

 ## Optonal Related Reading

- [ ] [Lecture Slides](https://codeinplace2020.github.io/faqs/6-ControlFlowRevisited.pdf)
- [x] [If](https://codeinplace2021.github.io/pythonreader/en/if/)
- [x] [While](https://codeinplace2021.github.io/pythonreader/en/while/)
- [x] [Booleans](https://codeinplace2021.github.io/pythonreader/en/booleans/)
- [x] [For](https://codeinplace2021.github.io/pythonreader/en/for/)
