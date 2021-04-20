# Lesson 1 Welcome to Karel April 19th

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

<hr />
<details>
<summary>Q4: Cleanup Karel, Milestone 2</summary>
<details open>
<summary>Description</summary>
Karel has a bit of spring cleaning to do! Karel's world will have beepers in some positions in the bottom row; write a program to have Karel walk across the bottom row and, at each position, pick up a beeper only if one is present. Notice that you've already written the code to check if a beeper is present and only pick up a beeper if one is there from the previous milestone -- you should use your code from the previous milestone as a helper function to help with the decomposition of this problem!

Additionally, note that Karel's starting position will never contain a beeper, so there's no need to check it.

For example, if this is the initial starting world, with some beepers in the first row:

<br />
<img width="600px" src="https://static.us.edusercontent.com/files/wrFTLPTbItmNInxXGsu6vf6Z" />
<br />

This should be the end result, with a clear bottom row:

<br />
<img width="600px" src="https://static.us.edusercontent.com/files/pR9y61NWe7bH7kJ5QaaIlOhn" />
<br />

We've provided you two worlds on which to test your code. You can toggle between them by changing the very last line in the file from run_karel_program('Cleanup1.w') to run_karel_program('Cleanup2.w') (and vice versa) -- you will likely need to press Run (it's fine if you do so without any code written) for the world change to take effect.
</details>
<details>
<summary>Code</summary>

``
```python
from karel.stanfordkarel import *

"""
File: CleanupKarel.py
--------------------
When you finish writing this file, CleanupKarel should be able to
pick up all beepers from the first row of any sized world and
end in the bottom right corner facing East.
"""

def main():
    """
    You should write your code to make Karel do its task in
    this function. Make sure to delete the 'pass' line before
    starting to write your own code. You should also delete this
    comment and replace it with a better, more descriptive one.
    """
    while no_beepers_present():
        move()
        if beepers_present():
            while beepers_present():
                pick_beeper()

if __name__ == '__main__':
    run_karel_program('Cleanup1.w')
```

`Cleanup1.w`
```yaml
Dimension: (5, 5)
Beeper: (2, 1); 1
Beeper: (4, 1); 1
Beeper: (5, 1); 1
Karel: (1, 1); east
BeeperBag: 0
```

`Cleanup2.w`
```yaml
Dimension: (7, 4)
Beeper: (2, 1); 1
Beeper: (5, 1); 1
Beeper: (3, 1); 1
Beeper: (7, 1); 1
Karel: (1, 1); east
BeeperBag: 0
```
</details>
</details>

<hr />
<details>
<summary>Q5: Ramp Climbing Karel</summary>
<details open>
<summary>Description</summary>
Write a program that has Karel draw a diagonal line across the world, with a slope of ½, like so:

<br />
<img width="600px" src="https://static.us.edusercontent.com/files/19era4m85IbSZmbhWQPzhwVP" />
<br />

The key to drawing a diagonal line with slope ½ is to move two steps forward and one step up between each beeper. In this problem you can and should assume that the world is an odd number of columns across. Solving the problem for even columns as well is much harder and would count as an "extension".

You should assume

- Karel always begins at the bottom left corner of and empty world facing East.
- You may assume that the world is an odd number of columns across
- Karel's bag has infinite beepers.
- It does not matter which direction Karel ends up facing.
- The world is always square (the world's height is the same as its width)

We've provided you three worlds on which to test your code. You can toggle between them by changing the very last line in the file from run_karel_program('RampKarel1.w') to run_karel_program('RampKarel2.w') or run_karel_program('RampKarel3.w') -- you will likely need to press Run (it's fine if you do so without any code written) for the world change to take effect. RampKarel1 is a 7x7 world, RampKarel2 is a 3x3 world, and RampKarel3 is a 25x25 world.
</details>
<details>
<summary>Code</summary>

`RampClimbingKarel.py`
```python
from karel.stanfordkarel import *

"""
File: RampClimbingKarel.py
--------------------
When you finish writing this file, RampClimbingKarel should be
able to draw a line with slope 1/2 in any odd sized world
"""

def main():
    """
    You should write your code to make Karel do its task in
    this function. Make sure to delete the 'pass' line before
    starting to write your own code. You should also delete this
    comment and replace it with a better, more descriptive one.
    """
    while front_is_clear():
        pump_up_the_volume()

def pump_up_the_volume():
    put_beeper()
    double_move()
    turn_left()
    move()
    turn_right()

def turn_right():
    turn_left()
    turn_left()
    turn_left()

def double_move():
    move()
    move()


if __name__ == '__main__':
    run_karel_program('RampKarel1.w')
```

`RampKarel1.w`
```yaml
Dimension: (7, 7)
BeeperBag: INFINITY
```

`RampKarel2.w`
```yaml
Dimension: (3, 3)
BeeperBag: INFINITY
```

`RampKarel3.w`
```yaml
Dimension: (25, 25)
BeeperBag: INFINITY
```
</details>
</details>

<hr />
<details>
<summary>Q6: Stone Mason Karel</summary>
<details open>
<summary>Description</summary>
Your next task is to repair the damage done to the Stanford Main Quad in the 1989 Loma Prieta earthquake. In particular, Karel should repair a set of arches where some of the stones (represented by beepers, of course) are missing from the columns supporting the arches, as illustrated in the figure below.

<br />
<img width="600px" src="https://static.us.edusercontent.com/files/6gHfxhu8FwoTsIaHSPAH4c7q" />
<br />

Your program should work on the world shown above, but it should be general enough to handle any world that meets the basic conditions outlined at the end of this problem.

<b>There are three example worlds here, and your program should work correctly in all of them.</b> You can toggle between them by changing the very last line in the file from run_karel_program('SampleQuad1.w') to run_karel_program('SampleQuad2.w') or run_karel_program('SampleQuad3.w') -- you will likely need to press Run (it's fine if you do so without any code written) for the world change to take effect.


When Karel is done, the missing stones in the columns should be replaced by beepers, so that the final picture resulting from the initial world shown in Figure 5 would look like the illustration below.

<br />
<img width="600px" src="https://static.us.edusercontent.com/files/CnXs0mvxKMChNPSIcTtaLHnc" />
<br />

Karel’s final location and the final direction Karel is facing at the end of the run do not matter. Karel may count on the following facts about the world:

- Karel starts at the corner where 1st Avenue and 1st Street meet, facing east, with an infinite number of beepers in Karel’s beeper bag. The first column should be built on 1st Avenue.
- The columns are always exactly four Avenues apart, so they would be built on 1st Avenue, 5th Avenue, 9th Avenue, and so on.
- The final column will always have a wall immediately after it. Although this wall appears after 13th Avenue in the example figure, your program should work for any number of beeper columns.
- The top of a beeper column will always be marked by a wall. However, Karel cannot assume that columns are always five units high, or even that all columns within a given world are the same height.
- In an initial world, some columns may already contain beepers representing stones that are still in place. Your program should not put a second beeper on corners that already have beepers. Avenues that will not have columns will never contain existing beepers

</details>
<details>
<summary>Code</summary>

`StoneMasonKarel.py`
```python
from karel.stanfordkarel import *

"""
File: StoneMasonKarel.py
------------------------
When you finish writing code in this file, StoneMasonKarel should be
able to solve the "repair the quad" problem from Assignment 1.
You should make sure that your program works for all of the
sample worlds supplied in the starter folder.
"""

def main():
    """
    You should write your code to make Karel do its task in
    this function. Make sure to delete the 'pass' line before
    starting to write your own code. You should also delete this
    comment and replace it with a better, more descriptive one.
    """
    while front_is_clear():
        logic_not_so_logic()
    pave_the_path_to_success()
    back_to_the_solid_foundation()

def pave_the_path_to_success():
    # while front_is_clear():
    if no_beepers_present():
        put_beeper()
    turn_left()
    while front_is_clear():
        move()
        while no_beepers_present():
            put_beeper()

def logic_not_so_logic():
    pave_the_path_to_success()
    back_to_the_solid_foundation()
    move_through_avenues()

def turn_around():
    turn_left()
    turn_left()

def turn_right():
    turn_left()
    turn_left()
    turn_left()

def back_to_the_solid_foundation():
    turn_around()
    while front_is_clear():
        move()
    turn_left()

def move_through_avenues():
    move()
    move()
    move()
    move()

if __name__ == '__main__':
    run_karel_program('SampleQuad1.w')
```

`SampleQuad1.w`
```yaml
Dimension: (13, 8)
Beeper: (1, 4); 1
Beeper: (1, 5); 1
Wall: (1, 6); South
Wall: (2, 6); West
Wall: (2, 7); South
Wall: (3, 7); West
Wall: (3, 8); South
Wall: (4, 7); West
Wall: (4, 7); South
Beeper: (5, 1); 1
Beeper: (5, 2); 1
Beeper: (5, 4); 1
Wall: (5, 6); West
Wall: (5, 6); South
Wall: (6, 6); West
Wall: (6, 7); South
Wall: (7, 7); West
Wall: (7, 8); South
Wall: (8, 7); West
Wall: (8, 7); South
Beeper: (9, 3); 1
Beeper: (9, 5); 1
Wall: (9, 6); West
Wall: (9, 6); South
Wall: (10, 6); West
Wall: (10, 7); South
Wall: (11, 7); West
Wall: (11, 8); South
Wall: (12, 7); West
Wall: (12, 7); South
Beeper: (13, 1); 1
Beeper: (13, 3); 1
Beeper: (13, 5); 1
Wall: (13, 6); West
Wall: (13, 6); South
BeeperBag: INFINITY
Karel: (1, 1); East
Speed: 0.5

```

`SampleQuad2.w`
```yaml
Dimension: (13, 9)
Beeper: (1, 1); 1
Beeper: (1, 2); 1
Wall: (1, 4); South
Wall: (2, 4); West
Wall: (2, 5); South
Wall: (3, 4); West
Wall: (3, 4); South
Wall: (4, 4); West
Wall: (4, 5); South
Beeper: (5, 1); 1
Wall: (5, 5); West
Beeper: (5, 5); 1
Wall: (5, 6); South
Wall: (6, 5); West
Wall: (6, 5); South
Wall: (7, 4); West
Wall: (7, 4); South
Wall: (8, 3); West
Wall: (8, 3); South
Wall: (9, 2); West
Wall: (9, 2); South
Wall: (10, 2); West
Wall: (10, 3); South
Wall: (11, 3); West
Wall: (11, 4); South
Wall: (12, 4); West
Wall: (12, 5); South
Beeper: (13, 1); 1
Beeper: (13, 3); 1
Wall: (13, 4); West
Wall: (13, 4); South
BeeperBag: INFINITY
Karel: (1, 1); East
Speed: 0.5
```

`SampleQuad3.w`
```yaml
Dimension: (5, 7)
Wall: (4, 5); west
Wall: (2, 5); south
Wall: (5, 2); south
Wall: (4, 3); east
Wall: (3, 5); north
Wall: (2, 4); west
Wall: (1, 3); north
Wall: (3, 5); west
Wall: (5, 2); west
Wall: (4, 4); west
Wall: (4, 3); north
Beeper: (5, 1); 1
Beeper: (1, 2); 1
Karel: (1, 1); east
BeeperBag: INFINITY
```

</details>
</details>

<hr />
<details>
<summary>Q7: Midpoint (optional!)</summary>
<details open>
<summary>Description</summary>
As an exercise in solving algorithmic problems, program Karel to place a single beeper at the middle of 1st Street (aka Row). For example, say Karel starts in the 5x5 world pictured in the figure:

<br />
<img width="600px" src="https://static.us.edusercontent.com/files/pqkbrO0wYb8xNzxtFrfPIddw" />
<br />

Karel should end with Karel standing on a beeper in the following position:

<br />
<img width="600px" src="https://static.us.edusercontent.com/files/zGfurKGRTTf4nT9OmEo305HF" />
<br />

Note that the final configuration of the world should have only a single beeper at the midpoint of 1st Street. Along the way, Karel is allowed to place additional beepers wherever it wants to, but must pick them all up again before it finishes. Similarly, if Karel paints/colors any of the corners in the world, they must all be uncolored before Karel finishes.

In solving this problem, you may count on the following facts about the world:

- Karel starts at the bottom left corner, facing east, with an infinite number of beepers in its bag.
- The initial state of the world includes no interior walls or beepers.
- The world need not be square, but you may assume that it is at least as tall as it is wide.

Your program, moreover, can assume the following simplifications:

- If the width of the world is odd, Karel must put the beeper in the center square. If the width is even, Karel may drop the beeper on either of the two center squares.
- It does not matter which direction Karel is facing at the end of the run.

There are many different algorithms you can use to solve this problem so feel free to be creative!

You should make sure your program runs successfully in all of the following worlds (which are just a few different examples to test out the generality of your solution): Midpoint.w (default world), `Midpoint1.w`, `Midpoint2.w`, `Midpoint8.w` .

You can toggle between worlds by changing `Midpoint.w` in the last line of the file (which is currently `run_karel_program`('Midpoint.w') to the filename of your choice (make sure to include the quotation marks around the filename) and running your program.
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
<summary>Extension (optional!)</summary>
<details open>
<summary>Description</summary>
If you finish early, you may optionally write a Karel project of your own choice. Modify this file to use Karel to complete any task of your choosing! Extensions are a great chance for practice and to be creative. Make sure to write comments to explain what your program is doing and update the world to be appropriate for your program. (Notice that you can toggle the rows and columns of Karel's world, and if you right click Karel's world, you'll see a dropdown of other things you can do by clicking!)
</details>
<details>
<summary>Code</summary>

`ExtensionKarel.py`
```python
from karel.stanfordkarel import *

"""
File: ExtensionKarel.py
-----------------------
This file is for optional extension programs.
"""

def main():
    """
    You should write your code to make Karel do its task in
    this function. Make sure to delete the 'pass' line before
    starting to write your own code. You should also delete this
    comment and replace it with a better, more descriptive one.
    """
    crazy_swing()

def turn_right():
   turn_left()
   turn_left()
   turn_left()

def crazy_swing():
    while no_beepers_present():
        if front_is_clear():
            move()
            turn_right()
            if front_is_clear():
                move()
            turn_left()
            if front_is_clear():
                move()
        else:
            turn_left()
            turn_left()
            turn_right()

if __name__ == "__main__":
    run_karel_program()
```

</details>
</details>

## Optional Worked Examples

- [ ] Welcome to Karel

 ## Optonal Related Reading

- [ ] [Intro to Karel](https://compedu.stanford.edu/karel-reader/docs/python/en/chapter1.html)
- [ ] [Programming Karel](https://compedu.stanford.edu/karel-reader/docs/python/en/chapter2.html)
- [ ] [New Functions](https://compedu.stanford.edu/karel-reader/docs/python/en/chapter3.html)
- [ ] [Decomposition](https://compedu.stanford.edu/karel-reader/docs/python/en/chapter4.html)
