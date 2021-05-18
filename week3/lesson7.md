# Lesson 7: Functions Revisited May 3rd

<details open>
<summary>Learning Goals</summary>
<br />
This week goal is to learn how to define functions, pass information via parameters, return information.
</details>

 ## Videos

- [x] Recap and Show

<details>
<summary>gameshow</summary>

`gameshow.py`
```python
def main():
    print("Welcome to the CodeInPlace Game Show")
    print("Pick a door and win a prize")
    print("------------------------------------")

    # Part 1: get the door number form the user
    door = int(input("Door: "))
    # while the input is invalid
    while door < 1 or door > 3:
        # tell the user the input was invalid
        print("Invalid door!")
        # ask for a new input
        door = int(input("Door: "))

    # Part 2: compute the prize
    prize = 4
    if door == 1:
        prize = 2 + 9 // 10 * 100
    elif door == 2:
        locked = prize % 2 != 0
        if not locked:
            prize += 6
    elif door == 3:
        for i in range(door):
            prize += i

    # Part 3: report the prize
    print('You win ' + str(prize) + ' treats')


if __name__ == '__main__':
    main()
```
</details>
<hr />

- [x] Toasters are Fns

<details>
<summary>gameshow with functions</summary>

`gameshow.py`
```python
def main():
    print("Welcome to the CodeInPlace Game Show")
    print("Pick a door and win a prize")
    print("------------------------------------")

    # Part 1: get the door number form the user
    door = get_door_choice()

    # Part 2: compute the prize
    prize = calculate_prize(door)

    # Part 3: report the prize
    print('You win ' + str(prize) + ' treats')


def get_door_choice():
    """
    Asks the user for a door. Keeps reprompting until they enter
    a valid input (door 1, 2 or 3)
    """
    door = int(input("Door: "))
    # while the input is invalid
    while door < 1 or door > 3:
        # tell the user the input was invalid
        print("Invalid door!")
        # ask for a new input
        door = int(input("Door: "))
    return door


def calculate_prize(door):
    """
    Based on the door choice, returns the prize.
    Assumes that the door value is an integer which
    must be 1, 2 or 3. Returns a number.
    """
    prize = 4
    if door == 1:
        prize = 2 + 9 // 10 * 100
    elif door == 2:
        locked = prize % 2 != 0
        if not locked:
            prize += 6
    elif door == 3:
        for i in range(door):
            prize += i
    return prize


if __name__ == '__main__':
    main()
```
</details>
<hr />

- [x] Anatomy of a Fn

<details>
<summary>woot</summary>

`woot.py`
```python

def main():
   woot(10)


def woot(num):
   for i in range(num):
      print('woot')


if __name__ == '__main__':
    main()
```
</details>
<hr />

- [x] Many Examples

<details>
<summary>meters2cms.py</summary>

`meters2cms`
```python
def main():
    meters = float(input('enter meters: '))
    resulCodet = meters_to_cm(meters)
    print(result)


def meters_to_cm(meters):
    """
    Takes in meters as incoming information.
    Returns the corresponding number of cms
    """
    return 100 * meters


if __name__ == '__main__':
```
</details>
<hr />

<details>
<summary>Max</summary>

`max.py`
```python
def main():
	larger = max(1, 10)
	print(larger)


def max(num_1, num_2):
	"""
	returns the larger of the two values
	"""
	if num_2 > num_1:
		return num_2
	return num_1


if __name__ == '__main__':
	main()
```
</details>
<hr />

- [x] Decomp Show

## Assignments Problems

<details>
<summary>Q8 (optional): Ancient Game of Nimm</summary>
<details open>
<summary>Description</summary>

</details>
<details>
<summary>nimm.py</summary>

`nimm.py`
```python
"""
The game of Nimm.

1. The game starts with a pile of 20 stones between the players.
2. The two players alternate turns.
3. On a given turn, a player may take either 1 or 2 stone from the center pile.
4. The two players continue until the center pile has run out of stones.

Write a program to play Nimm.
"""
import random


STONES = 20
PLAYER1 = "Player 1"
PLAYER2 = "Player 2"


def main():
    game()


def game():
    stones = STONES
    current_player = PLAYER1
    stones_to_remove = 0

    while stones > 0:
        print(f"There are {stones} stones left")

        if current_player == PLAYER1:
            # print("")
            # print(f"There are {stones} stones left")
            stones_to_remove = stones_to_remove_def(PLAYER1)
            # stones_to_remove = int(input("Player 1 would you like to remove 1 or 2 stones? "))

            # while stones_to_remove > 2:
            #     stones_to_remove = int(input("Player 1 would you like to remove 1 or 2 stones? "))
            current_player = PLAYER2
        else:
            stones_to_remove = stones_to_remove_def(PLAYER2)
            # stones_to_remove = int(input("Player 2 would you like to remove 1 or 2 stones? "))

            # while stones_to_remove > 2:
            #     stones_to_remove = int(input("Player 2 would you like to remove 1 or 2 stones? "))
            current_player = PLAYER1
        stones -= stones_to_remove

        print("")
    if current_player == PLAYER1:
        print(f"{PLAYER1} wins!")
    else:
        print(f"{PLAYER2} wins!")


def stones_to_remove_def(player):
    stones_to_remove = int(input(f"{player} would you like to remove 1 or 2 stones? "))
    if stones_to_remove == 0:
        stones_to_remove = int(input("Please enter 1 or 2: "))
    while stones_to_remove > 2:
        stones_to_remove = int(input("Please enter 1 or 2: "))
    return stones_to_remove


if __name__ == '__main__':
    main()
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

- [x] Lecture Examples (in videos)
- [x] Console Examples

 ## Optonal Related Reading

- [ ] [Lecture Slides](https://codeinplace2020.github.io/faqs/7-Functions.pdf)
- [ ] [Functions](https://codeinplace2021.github.io/pythonreader/en/functions/)
