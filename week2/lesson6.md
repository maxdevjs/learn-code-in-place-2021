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
<summary>Q8 (optional): Ancient Game of Nimm</summary>
<details open>
<summary>Description</summary>

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
<summary>(optional) Extension </summary>
<details open>
<summary>Description</summary>

</details>
<details>
<summary>Code</summary>

`.py`
```python

```
</details>
</details>
<hr />

## Optional Worked Examples

- [ ] Lecture Examples
- [ ] Console Examples

 ## Optonal Related Reading

- [ ] [Lecture Slides](https://codeinplace2020.github.io/faqs/6-ControlFlowRevisited.pdf)
- [x] [If](https://codeinplace2021.github.io/pythonreader/en/if/)
- [ ] [While](https://codeinplace2021.github.io/pythonreader/en/while/)
- [ ] [Booleans](https://codeinplace2021.github.io/pythonreader/en/booleans/)
- [ ] [For](https://codeinplace2021.github.io/pythonreader/en/for/)
