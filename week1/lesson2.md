# Lesson 2 Control Flow April 21st

<details open>
<summary>Learning Goals</summary>
<br />

Learn how to use for loops to repeat a block of code a fixed number of times. Learn to use a while loop to repeat a block of code, checking on a condition before each repetition. Learn to use an if statement which only executes a block of code 'if' a given condition passes!
</details>

 ## Videos

- [x] Karel Recap
- [x] For Loops
- [x] While Loops
- [x] If Statements
- [x] SteepleChase

## Control flow with Karel

This part presents a series of exercises in an incremental difficult degree. There are warmups for the `for` and while` loops, and if/else conditions.

`Note:` receiving a `Karel: No beepers left in bag` message is an amazing experience 🤯

<hr />
<details>
<summary>More Problems</summary>
<details open>
<summary>Description</summary>

After the warmup, a series of more complex problems is available.

</details>

<details>
<summary>Spring flowers!</summary>
<details open>
<summary>Description</summary>
Make the flowers to bloom!
</details>
<details>
<summary>Code</summary>

`SpringFlowers.py`
```python
from karel.stanfordkarel import *

"""
File: SpringFlowers.py
------------------------------
Karel starts in the bottom left corner of a world with 2 empty flower stems, facing East.
Karel should bloom both flowers with beepers and end in the bottom right corner of the world facing East.
"""

def main():
    """
    You should write your code to make Karel do its task in
    this function. Make sure to delete the 'pass' line before
    starting to write your own code. You should also delete this
    comment and replace it with a better, more descriptive one.
    """
    for i in range(2):
        make_one_flower()
    find_the_wall()

def make_one_flower():
    find_the_wall()
    turn_left()
    climb_the_stem()
    flower_bloom()
    find_the_wall()
    turn_left()

def climb_the_stem():
    while right_is_blocked():
        move()

def flower_bloom():
    put_beeper()
    move()
    put_beeper()
    turn_right()
    move()
    put_beeper()
    turn_right()
    move()
    put_beeper()

def find_the_wall():
    while front_is_clear():
        move()

def turn_right():
    for i in range(3):
        turn_left()

if __name__ == "__main__":
    run_karel_program('SpringFlowers1')
```

`SpringFlowers1.w`
```yaml
Dimension: (7, 7)
Wall: (5, 2); east
Wall: (2, 3); east
Wall: (2, 4); east
Wall: (5, 3); east
Wall: (2, 1); east
Wall: (2, 2); east
Wall: (6, 1); west
Karel: (1, 1); east
BeeperBag: INFINITY
```

`SpringFlowers2.w`
```yaml
Dimension: (7, 7)
Wall: (5, 2); east
Wall: (5, 1); east
Wall: (3, 2); east
Wall: (5, 4); east
Wall: (5, 3); east
Wall: (3, 1); east
Beeper: (3, 3); 0
Beeper: (4, 3); 0
Beeper: (4, 4); 0
Beeper: (3, 4); 0
Beeper: (5, 5); 0
Beeper: (6, 5); 0
Beeper: (6, 6); 0
Beeper: (5, 6); 0
Karel: (1, 1); east
BeeperBag: INFINITY
```
</details>
</details>

<hr />
<details>
<summary>Three slots (for loops, fencepost) Fix 💣</summary>
<details open>
<summary>Description</summary>
Place beepers in multiple slots.
<br />
<br />
For an extra challenge, this code should use with a while loop instead so that it works for worlds with any number of columns / slots!
<br />
<img width="600px" src="" />
<br />

</details>
<details>
<summary>Code</summary>

`SlotsKarel.py`
```python
from karel.stanfordkarel import *

"""
File: SlotsKarel.py
-----------------------
Place 10 beepers in all spots on the bottom row of any sized world.
"""

def main():
    """
    You should write your code to make Karel do its task in
    this function. Make sure to delete the 'pass' line before
    starting to write your own code. You should also delete this
    comment and replace it with a better, more descriptive one.
    """

    for i in range(3):
        put_one_beeper()
        move()
    find_the_wall()

def put_one_beeper():
    turn_right()
    find_the_wall()
    turn_around()
    put_beeper()
    climb_the_stem()
    turn_right()

def climb_the_stem():
    if front_is_clear():
        if right_is_blocked():
            move()

def find_the_wall():
    while front_is_clear():
        move()

def turn_around():
    for i in range(2):
        turn_left()

def turn_right():
    for i in range(3):
        turn_left()

if __name__ == "__main__":
    run_karel_program('Slots.w')
```

`Slots.w`
```yaml
Dimension: (3, 2)
Wall: (1, 1); east
Wall: (3, 1); west
Karel: (1, 2); east
BeeperBag: INFINITY
```

</details>
</details>

<hr />
<details>
<summary>Five corridors (for loops, while loops, fencepost, if/else)</summary>
<details open>
<summary>Description</summary>
Put beepers at the end of corridors that do not already have.
<br />
<img width="600px" src="" />
<br />

</details>
<details>
<summary>Code</summary>

`FiveCorridorsKarel.py`
```python
from karel.stanfordkarel import *

"""
File: FiveCorridorsKarel.py
-----------------------
Karel traverse 5 variable length corridors and place beepers at the ends of them if there aren't already beepers there.
"""

def main():
    """
    You should write your code to make Karel do its task in
    this function. Make sure to delete the 'pass' line before
    starting to write your own code. You should also delete this
    comment and replace it with a better, more descriptive one.
    """
    do_it_all()

def do_it_all():
    for i in range(5):
        forth_and_back()

def forth_and_back():
    find_the_wall()
    check_beeper()
    turn_around()
    find_the_wall()
    turn_right()
    if front_is_clear():
        move()
    turn_right()

def check_beeper():
    if no_beepers_present():
        if facing_east():
            put_beeper()

def find_the_wall():
    while front_is_clear():
        move()

def turn_around():
    for i in range(2):
        turn_left()

def turn_right():
    for i in range(3):
        turn_left()


if __name__ == "__main__":
    run_karel_program()
```

`Corridors.w`
```yaml
Dimension: (7, 5)
Wall: (2, 1); north
Wall: (6, 3); north
Wall: (6, 4); north
Wall: (5, 5); south
Wall: (5, 1); north
Wall: (6, 3); east
Wall: (3, 4); north
Wall: (6, 3); south
Wall: (2, 3); north
Wall: (5, 3); south
Wall: (4, 1); east
Wall: (3, 4); south
Wall: (7, 4); north
Wall: (7, 3); north
Wall: (2, 2); north
Wall: (2, 5); south
Wall: (4, 2); north
Wall: (4, 4); south
Wall: (6, 1); north
Wall: (3, 2); south
Wall: (5, 4); south
Wall: (4, 4); east
Wall: (3, 2); north
Wall: (4, 5); south
Wall: (4, 2); south
Wall: (7, 3); south
Wall: (7, 1); north
Beeper: (7, 2); 1
Beeper: (4, 4); 1
Karel: (1, 1); east
BeeperBag: INFINITY
```

</details>
</details>

<hr />
<details>
<summary>Upstairs, downstairs (for/while loops)</summary>
<details open>
<summary>Description</summary>
Go upstairs and downstairs.
<br />
<img width="600px" src="" />
<br />

</details>
<details>
<summary>Code</summary>

`UpstairsDownstairs.py`
```python
from karel.stanfordkarel import *

"""
File: UpstairsDownstairs.py
------------------------------
Karel will climb three stair steps up and then three stair steps down.
"""

def main():
    """
    You should write your code to make Karel do its task in
    this function. Make sure to delete the 'pass' line before
    starting to write your own code. You should also delete this
    comment and replace it with a better, more descriptive one.
    """
    while front_is_blocked():
        step_up()

    while front_is_clear():
        step_down()

def step_up():
    if front_is_blocked():
        turn_left()
        move()
        turn_right()
        move()

def step_down():
    if front_is_clear():
        move()
        turn_right()
        move()
        turn_left()

def turn_right():
    for i in range(3):
        turn_left()

if __name__ == "__main__":
    run_karel_program('UpstairsDownstairs.w')
```

`UpstairsDownstairs.w`
```yaml
Dimension: (7, 4)
Wall: (3, 2); north
Wall: (5, 3); south
Wall: (2, 1); north
Wall: (3, 3); east
Wall: (6, 1); east
Wall: (5, 3); west
Wall: (2, 1); west
Wall: (2, 2); east
Wall: (4, 3); north
Wall: (6, 2); south
Wall: (6, 2); west
Karel: (1, 1); east
BeeperBag: 0
```

</details>
</details>

<hr />
<details>
<summary>Zig zag (while loops, optional if/else)</summary>
<details open>
<summary>Description</summary>
Karel should place a zig zag pattern of beepers such that all odd columns have beepers in row 1 and all even columns have beepers in row 2.
<br />
<img width="600px" src="" />
<br />

</details>
<details>
<summary>Code</summary>

`ZigZagKarel.py`
```python
from karel.stanfordkarel import *

"""
File: ZigZagKarel.py
-----------------------
Places a zig zag pattern of beepers in the world.
"""

def main():
    """
    You should write your code to make Karel do its task in
    this function. Make sure to delete the 'pass' line before
    starting to write your own code. You should also delete this
    comment and replace it with a better, more descriptive one.
    """
    while front_is_clear():
        put_beeper()
        double_move()
    turn_left()
    move()
    turn_left()
    while front_is_clear():
        put_beeper()
        double_move()

def double_move():
    if front_is_clear():
        move()
    if front_is_clear():
        move()

if __name__ == "__main__":
    run_karel_program('ZigZag1.w')
```

`ZigZag1.w`
```yaml
Dimension: (6, 2)
Karel: (1, 1);
BeeperBag: INFINITY
```

`ZigZag2.w`
```yaml
Dimension: (3, 2)
Karel: (1, 1); east
BeeperBag: INFINITY
```

</details>
</details>

<hr />
<details>
<summary>Labyrinth (while loops, if/else)</summary>
<details open>
<summary>Description</summary>
Solve the [maze](https://en.wikipedia.org/wiki/Labyrinth).

FIX: How am I supposed to count the beepers and then stop on the bigger pile?

Found: check Treasure hunt, part 1 (while loops)
<br />
<img width="600px" src="" />
<br />

</details>
<details>
<summary>Code</summary>

`LabyrinthKarel.py`
```python
from karel.stanfordkarel import *

"""
File: LabyrinthKarel.py
------------------------------
Karel solves labyrinths!
"""

def main():
    """
    You should write your code to make Karel do its task in
    this function. Make sure to delete the 'pass' line before
    starting to write your own code. You should also delete this
    comment and replace it with a better, more descriptive one.
    """
    reach_the_finish_line()

def reach_the_finish_line():
    while front_is_clear():
        move()
        find_the_direction()

def find_the_direction():
    if left_is_clear():
            turn_left()
    if right_is_clear():
        turn_right()

def find_the_wall():
    while front_is_clear():
        move()

def turn_right():
    for i in range(3):
        turn_left()

if __name__ == "__main__":
    run_karel_program('Labyrinth1')
```

`Labyrinth1.w`
```yaml
Dimension: (5, 4)
Wall: (1, 2); east
Wall: (1, 3); east
Wall: (4, 1); north
Wall: (5, 2); north
Wall: (4, 4); south
Wall: (4, 3); south
Wall: (2, 3); north
Wall: (2, 1); east
Wall: (3, 3); north
Wall: (3, 2); south
Wall: (2, 2); east
Wall: (4, 3); west
Beeper: (2, 1); 0
Karel: (3, 1); east
BeeperBag: 0
```

`Labyrinth2.w`
```yaml
Dimension: (5, 4)
Wall: (1, 1); north
Wall: (5, 3); south
Wall: (3, 3); east
Wall: (2, 4); south
Wall: (3, 2); west
Wall: (4, 4); south
Wall: (4, 2); south
Wall: (3, 2); east
Wall: (1, 4); south
Wall: (2, 1); east
Wall: (3, 3); north
Wall: (2, 3); south
Beeper: (2, 1); 0
Karel: (1, 1); east
BeeperBag: 0
```

</details>
</details>

<hr />
<details>
<summary>Treasure hunt, part 1 (while loops)</summary>
<details open>
<summary>Description</summary>
Because the treasure is meant for Karel only, Karel should pick up all the beepers she encounters as she moves along, including the final pile of 10. Karel should end up where the pile of 10 beepers is.
<br />
<img width="600px" src="" />
<br />

</details>
<details>
<summary>Code</summary>

`TreasureHunt1.py`
```python
from karel.stanfordkarel import *

"""
File: TreasureHunt1.py
------------------------------
Karel will move forward until a beeper.
At every beeper, Karel will turn left and move until the next beeper, until Karel is standing on the treasure, which is a pile of 10 beepers.
"""

def main():
    """
    You should write your code to make Karel do its task in
    this function. Make sure to delete the 'pass' line before
    starting to write your own code. You should also delete this
    comment and replace it with a better, more descriptive one.
    """
    move_to_beeper()

# FIX: end up where the pile of 10 beepers is

def move_to_beeper():
    while no_beepers_present():
        move()
    if beepers_present():
        turn_left()
        pick_beeper()
        if beepers_present():
            while beepers_present():
                pick_beeper()
        else:
            move()
            move_to_beeper()

if __name__ == "__main__":
    run_karel_program('TreasureHunt1.w')
```

`TreasureHunt1.w`
```yaml
Dimension: (7, 7)
Beeper: (6, 1); 0
Beeper: (5, 1); 1
Beeper: (5, 6); 1
Beeper: (1, 6); 1
Beeper: (1, 5); 1
Beeper: (7, 5); 1
Beeper: (7, 7); 1
Beeper: (3, 7); 1
Beeper: (3, 3); 10
Karel: (1, 1); east

```

</details>
</details>

<hr />
<details>
<summary>bla</summary>
<details open>
<summary>Description</summary>

<br />
<img width="600px" src="" />
<br />

</details>
<details>
<summary>Code</summary>

``
```python

```

``
```yaml

```

</details>
</details>

<hr />
<details>
<summary>bla</summary>
<details open>
<summary>Description</summary>

<br />
<img width="600px" src="" />
<br />

</details>
<details>
<summary>Code</summary>

``
```python

```

``
```yaml

```

</details>
</details>


</details>

## Assignments Problems

<hr />
<details>
<summary>Q2: Year 2021</summary>
<details open>
<summary>Description</summary>
Congratulations on beginning your coding journey! Karel welcomes you to Code in Place 2021. Your next task is to help Karel celebrate the occasion by placing 20 beepers, moving Karel one step, placing 21 beepers, and moving Karel one more step. The world should ultimately look like this:

<br />
<img width="600px" src="https://static.us.edusercontent.com/files/1I5dc3wVCM4UfOyajbk9cexw" />
<br />

Happy coding!
</details>
<details>
<summary>Code</summary>

`2021.py`
```python
from karel.stanfordkarel import *

"""
File: 2021.py
--------------------
When you finish writing this file, Karel should be able to place 20 beepers,
then 21 beepers, and end facing East to the right of the 21 beepers.
"""

def main():
    """
    You should write your code to make Karel do its task in
    this function. Make sure to delete the 'pass' line before
    starting to write your own code. You should also delete this
    comment and replace it with a better, more descriptive one.
    """

    for i in range(20):
        put_beeper()

    move()

    for i in range(21):
        put_beeper()

    move()

if __name__ == '__main__':
    run_karel_program('3x3.w')
```

`3x3.w`
```yaml
Dimension: (3, 3)
Karel: (1, 1); east
BeeperBag: INFINITY
```
</details>
</details>

<hr />

<details>
<summary>Q3: Cleanup Karel, Milestone 1</summary>

<details open>
<summary>Description</summary>
Your next task is to execute a "safe pickup" -- Karel can pick up beepers, but not if none are present! Write a program which will check if a beeper is present at the position Karel is currently on and pick up a beeper if one is present (if there are no beepers present, Karel shouldn't do anything).

Two worlds are provided for your to test your code on -- on the world where Karel starts on a beeper, your code should get Karel to pick the beeper up. On the world where Karel stREADMEarts on a blank spot, your code shouldn't do anything.

We've provided you two 1x1 worlds (one with a beeper, one without) on which to test your code. You can toggle from the beeper-present world to the no-beeper world by changing the very last line in the file from run_karel_program('SafePickup1.w') to run_karel_program('SafePickup2.w') (and vice versa).
</details>
<details>
<summary>Code</summary>

`SafePickup1.py`
```python
from karel.stanfordkarel import *

"""
File: SafePickup.py
--------------------
When you finish writing this file, Karel should be able to
pick up a beeper from the current position if one is present
(but do nothing if no beepers are present).
"""

def main():
    """
    You should write your code to make Karel do its task in
    this function. Make sure to delete the 'pass' line before
    starting to write your own code. You should also delete this
    comment and replace it with a better, more descriptive one.
    """
    while beepers_present():
        pick_beeper()

if __name__ == '__main__':
    run_karel_program('SafePickup1.w')
```

`SafePickup1.w`
```yaml
Dimension: (1, 1)
BeeperBag: INFINITY
Beeper: (1,1); 1
Karel: (1, 1); East
Speed: 0.75
```

`SafePickup2.w`
```yaml
Dimension: (1, 1)
BeeperBag: INFINITY
Karel: (1, 1); East
Speed: 0.75
```
</details>
</details>

## Optional Worked Examples

- [ ] [Control Flow Examples](https://edstem.org/us/courses/10000/lessons/12449/slides/60969)


 ## Optonal Related Reading

- [ ] [For Loops](https://compedu.stanford.edu/karel-reader/docs/python/en/chapter5.html)
- [ ] [While Loops](https://compedu.stanford.edu/karel-reader/docs/python/en/chapter6.html)
- [ ] [Conditionals](https://compedu.stanford.edu/karel-reader/docs/python/en/chapter7.html)
