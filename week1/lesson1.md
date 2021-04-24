# Lesson 1: Welcome to Karel April 19th

<details open>
<summary>Learning Goals</summary>
<br />

By the end of class you should know about Code in Place. You should also know basic Karel commands. The Karel material is review from the concepts that you used in the application -- this gives you a chance to get used to the course structure in a gentle way. Learn about the art of writing beautiful programs.
</details>

 ## Videos

- [x] Welcome
- [x] About Code in Place
- [x] Meet Karel

## Assignments Problems

<details>
<summary>Q1: Jigsaw Puzzle Karel</summary>
<details open>
<summary>Description</summary>
During quarantine, Karel has picked up a new hobby: doing puzzles! Karel is almost done with the square puzzle represented by the 4x4 grid of beepers shown below:

<br />
<img img width="600px" src="https://static.us.edusercontent.com/files/NBulki5rUJribfbNf9ScnoFp" />
<br />

The beeper in the bottom most row represents the last piece of the puzzle! Write a program which will get Karel to pick up the last piece, put it in place, and move Karel back to the bottom left corner of the world facing East so she can admire the completed puzzle. Here's what your end result should look like:

<br />
<img img width="600px" src="https://static.us.edusercontent.com/files/KjPIYmUMTfMPW0G2BO6k6jbb" />
<br />

To reiterate, you should write the sequence of commands so that Karel will:

- Move to and pick up the last puzzle piece (the beeper in row 1, column 3)

- Put the puzzle piece in place (row 3, column 4)

- Return Karel to her initial position

Although the program does not have many lines of code, it is still worth getting some practice with decomposition. In your solution, include a function for each of the three steps shown in the outline above.
</details>
<details>
<summary>Code</summary>

`PuzzleKarel.py`
```python
from karel.stanfordkarel import *

"""
File: PuzzleKarel.py
--------------------
Karel should finish the puzzle by picking up the last beeper (puzzle piece) and placing it in the right spot.
Karel should end in the same position Karel starts in -- the bottom left corner of the world.
"""

def main():
    """
    You should write your code to make Karel do its task in
    this function. Make sure to delete the 'pass' line before
    starting to write your own code. You should also delete this
    comment and replace it with a better, more descriptive one.
    """
    pick_up_the_gorgeous_beeper()
    put_the_puzzle_piece_in_place()
    return_karel_to_her_initial_position()

def pick_up_the_gorgeous_beeper():
    double_move()
    pick_beeper()

def put_the_puzzle_piece_in_place():
    move()
    turn_left()
    double_move()
    put_beeper()

def return_karel_to_her_initial_position():
    turn_around()
    double_move()
    turn_right()
    move()
    move()
    move()
    turn_around()

def turn_around():
    turn_left()
    turn_left()

def double_move():
    move()
    move()

def turn_right():
    turn_left()
    turn_left()
    turn_left()

if __name__ == '__main__':
    run_karel_program('Puzzle.w')
```

`Puzzle.w`
```yaml
Dimension: (7, 7)
Wall: (3, 2); north
Wall: (6, 4); east
Wall: (5, 3); south
Wall: (2, 6); east
Wall: (6, 5); east
Wall: (6, 6); east
Wall: (6, 7); south
Wall: (3, 3); west
Wall: (2, 4); east
Wall: (6, 3); south
Wall: (2, 5); east
Wall: (5, 7); south
Wall: (6, 3); east
Wall: (4, 6); north
Wall: (3, 6); north
Beeper: (4, 3); 0
Beeper: (5, 3); 1
Beeper: (6, 3); 1
Beeper: (6, 4); 1
Beeper: (5, 4); 1
Beeper: (5, 5); 1
Beeper: (6, 5); 1
Beeper: (6, 6); 1
Beeper: (5, 6); 1
Beeper: (4, 6); 1
Beeper: (3, 6); 1
Beeper: (3, 5); 1
Beeper: (4, 5); 1
Beeper: (4, 4); 1
Beeper: (3, 4); 1
Beeper: (3, 1); 1
Beeper: (3, 3); 1
Beeper: (3, 2); 0
Beeper: (2, 2); 0
Beeper: (2, 3); 0
Beeper: (2, 4); 0
Beeper: (2, 5); 0
Beeper: (2, 6); 0
Karel: (1, 1); east
BeeperBag: 0
```
</details>
</details>

## Optional Worked Examples

- [ ] Welcome to Karel

 ## Optonal Related Reading

- [x] [Intro
        pick_beeper()
        turn_left() to Karel](https://compedu.stanford.edu/karel-reader/docs/python/en/chapter1.html)
- [x] [Programming Karel](https://compedu.stanford.edu/karel-reader/docs/python/en/chapter2.html)
- [x] [New Functions](https://compedu.stanford.edu/karel-reader/docs/python/en/chapter3.html)
- [x] [Decomposition](https://compedu.stanford.edu/karel-reader/docs/python/en/chapter4.html)

- [ ] [Python (programming language)](https://en.wikipedia.org/wiki/Python_(programming_language))
- [ ] [Programming language](https://en.wikipedia.org/wiki/Programming_language)