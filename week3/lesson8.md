# Lesson 8: Core Complete May 5th

<details open>
<summary>Learning Goals</summary>
<br />
Learn how to trace control flow. Learn how to write and run doctests. Practice practice practice.

Okay, I will come back here to rephrase it...
</details>

 ## Videos

- [x] Intro
- [x] Sentiment

<details>
<summary>Code</summary>

`sentiment.py`
```python
import nltk.sentiment
analyzer = nltk.sentiment.SentimentIntensityAnalyzer()


def main():
    while True:
        user_text = input('? ')
        score = get_sentiment(user_text)
        reaction = get_reaction(score)
        print(reaction)
        print(score)
        print('')


def get_reaction(score):
    """
    Parameter score: a float between -1 and +1
    Return: An emoji as a string!
    """
    if score > 0.5:
        return "🥰"
    if score > 0:
        return "🙂"
    if score == 0:
        return "😶"
    if score < -0.5:
        return "😢"
    if score < 0:
        return "😟"


def get_sentiment(user_text):
    """
    Parameter user_text: any text (string)
    Return: a sentiment score between -1 and +1 (float)
    """
    # 1. pass the text into the analyzer.polarity_scores function, part of the nltk package
    scores = analyzer.polarity_scores(user_text)
    # 2. extract the sentiment score. Scores is a "dictionary" (covered on May 17th)
    sentiment_score = scores['compound']

    return sentiment_score


if __name__ == '__main__':
    main()
```
</details>

- [x] Factorial

<details>
<summary>Code</summary>

`python -m doctest factorial.py -v`

`factorial.py`
```python
# Constant – visible to all functions
MAX_NUM = 9


def main():
    # repeat for several values!
    for i in range(MAX_NUM+1):
        print(i, factorial(i))


def factorial(n):
    """
    Calculates n factorial.
    5 factorial is 5 * 4 * 3 * 2 * 1
    >>> factorial(5)
    120
    >>> factorial(4)
    24
    >>> factorial(3)
    6
    >>> factorial(1)
    1
    >>> factorial(0)
    1
    """
    result = 1
    for i in range(1, n+1):
        result *= i
    return result


if __name__ == '__main__':
    main()
```
</details>

- [x] add_five

<details>
<summary>Code</summary>

`add_five.py`
```python

def main():
    x = 1
    plus_five(x)
    print(x)

def plus_five(x):
    x += 5

if __name__ == '__main__':
    main()
```
</details>

- [x] Doctests

<details>
<summary>Code</summary>

`python -m doctest leap.py -v`

`leap.py`
```python
"""
Example of using the index variable of a for loop
"""


def main():
    pass


def is_divisible(a, b):
    """
    >>> is_divisible(20, 4)
    True
    >>> is_divisible(12, 7)
    False
    >>> is_divisible(10, 10)
    True
    """
    return a % b == 0


def is_leap_year(year):
    """
    Returns Boolean indicating if given year is a leap year.
    It is a leap year if the year is:
    * divisible by 4, but not divisible by 100
     OR
    * divisible by 400
    Doctests:
    >>> is_leap_year(2001)
    False
    >>> is_leap_year(2020)
    True
    >>> is_leap_year(2000)
    True
    >>> is_leap_year(1900)
    False
    """

    # if the year is divisible by 400, it is a leap year!
    if is_divisible(year, 400):
        return True

    # other wise its a leap year if its divisible by 4 and not 100
    return is_divisible(year, 4) and not is_divisible(year, 100)


if __name__ == '__main__':
    main()
```
</details>

- [x] Rock Paper Scissors

<details>
<summary>ai_guess.py</summary>

`ai_guess.py`
```python
"""
This wasn't in lecture, but I considered adding it!
In this version of guess my number, the human thinks
of a number and the AI tries to guess it.
"""


def main():
    print('think of a number between 0 and 100')
    min_value = 0
    max_value = 100

    while True:
        query = min_value + (max_value - min_value) // 2
        if check_is_answer(query):
            # you know you have the right answer
            break
        if check_is_greater(query):
            # you know the number must be greater than query
            min_value = query + 1
        else:
            # you know the number must be less than query
            max_value = query - 1
    print('Your number was ', query)


def check_is_answer(value):
    return ask_true_false('Is your number '+str(value)+'?')


def check_is_greater(value):
    return ask_true_false('Is your number greater than '+str(value)+'?')


def ask_true_false(prompt):
    response = input(prompt + ' (y/n) ')
    return response == 'y' or response == 'Y'


if __name__ == "__main__":
    main()
```
</details>

<details>
<summary>nim_random.py</summary>

`nim_random.py`
```python
"""
This wasn't in lecture, but I considered adding it!
It runs 10,000 games of nimm where both players play randomly
It then counts how many games player 1 wins.
"""
import random
NUM_EXPERIMENTS = 10000
N_STONES = 20


def main():
	n_player_1_wins = 0
	for i in range(NUM_EXPERIMENTS):
		winner = simulate_random_nimm()
		if winner == 1:
			n_player_1_wins += 1
	print(n_player_1_wins)


def simulate_random_nimm():
	stones = N_STONES
	turn = 1
	while stones > 0:
		take = random.randint(1, 2)
		stones -= take
		if turn == 1:
			turn = 2
		else:
			turn = 1
	return turn


if __name__ == "__main__":
    main()
```
</details>

<details>
<summary>rps.py</summary>

`rps.py`
```python
"""
Implements the game of Rock-Paper-Scissors!

History:
This classic game dates back to the Han Dinesty, over 2200 years ago.
The First International Rock-Paper-Scissors Programming Competition
was held in 1999 and was won by a team called "Iocaine Powder"

The Game:
Each player choses a move (simultaneously) from the choices:
rock, paper or scissors.
If they chose the same move the game is a tie. Otherwise:
rock beats scissors
scissors beats paper
paper beats rock.

In this program a human plays against an AI. The AI choses randomly
(we promise). The game is repeated N_GAMES times and the human gets
a total score. Each win is worth +1 points, each loss is worth -1
"""
import random

N_GAMES = 3


def main():
    print_welcome()


def print_welcome():
    print('Welcome to Rock Paper Scissors')
    print('You will play '+str(N_GAMES)+' games against the AI')
    print('rock beats scissors')
    print('scissors beats paper')
    print('paper beats rock')
    print('----------------------------------------------')
    print('')


if __name__ == '__main__':
    main()
```
</details>

<details>
<summary>rps.py</summary>

`rps.py`
```python
"""
Implements the game of Rock-Paper-Scissors!

History:
This classic game dates back to the Han Dinesty, over 2200 years ago.
The First International Rock-Paper-Scissors Programming Competition
was held in 1999 and was won by a team called "Iocaine Powder"

The Game:
Each player choses a move (simultaneously) from the choices:
rock, paper or scissors.
If they chose the same move the game is a tie. Otherwise:
rock beats scissors
scissors beats paper
paper beats rock.

In this program a human plays against an AI. The AI choses randomly
(we promise). The game is repeated N_GAMES times and the human gets
a total score. Each win is worth +1 points, each loss is worth -1
"""
import random

N_GAMES = 3


def main():
    print_welcome()
    score = 0

    for i in range(N_GAMES):
        ai_move = get_ai_move()
        human_move = get_human_move()
        outcome = decide_outcome(ai_move, human_move)
        announce_result(ai_move, outcome)
        score += calc_outcome_score(outcome)

    print('your score', score)


def announce_result(ai_move, outcome):
    """
    Lets the user what the AI played and who won
    """
    print('The AI plays: ' + ai_move)
    print('The winner is: ' + outcome)
    print('')


def calc_outcome_score(outcome):
    """
    You get 1 point for winning, and lose 1 point for losing.
    >>> calc_outcome_score('tie')
    0
    >>> calc_outcome_score('human')
    1
    >>> calc_outcome_score('ai')
    -1
    """
    if outcome == 'human':
        return +1
    if outcome == 'ai':
        return -1
    return 0


def decide_outcome(ai_move, human_move):
    """
    >>> decide_outcome('rock','scissors')
    'ai'
    >>> decide_outcome('scissors','scissors')
    'tie'
    """
    # if the two moves are the same, it is a tie
    if ai_move == human_move:
        return 'tie'
    if ai_move == 'rock':
        if human_move == 'scissors':
            return 'ai'
        return 'human'
    if ai_move == 'scissors':
        if human_move == 'paper':
            return 'ai'
        return 'human'
    if ai_move == 'paper':
        if human_move == 'rock':
            return 'ai'
        return 'human'
    print('should not get here!')


def get_human_move():
    """
    make sure the human enters 'rock' 'paper' or 'scissors'
    """
    while True:
        choice = input('what do you play? ')
        if is_valid_choice(choice):
            return choice
        print('invalid choice')


def get_ai_move():
    """
    for now the AI plays randomly. But the optimal strategy is:
    If you lose, switch to the thing that beats the thing your opponent just played.
    If you win, switch to the thing that would beat the thing that you just played.
    """
    value = random.randint(1, 3)
    if value == 1:
        return 'rock'
    if value == 2:
        return 'paper'
    return 'scissors'


def is_valid_choice(choice):
    """
    >>> is_valid_choice('rock')
    True
    >>> is_valid_choice('paper')
    True
    >>> is_valid_choice('unicorn')
    False
    """
    if choice == 'rock':
        return True
    if choice == 'paper':
        return True
    if choice == 'scissors':
        return True
    return False


def print_welcome():
    print('Welcome to Rock Paper Scissors')
    print('You will play '+str(N_GAMES)+' games against the AI')
    print('rock beats scissors')
    print('scissors beats paper')
    print('paper beats rock')
    print('----------------------------------------------')
    print('')


if __name__ == '__main__':
    main()
```
</details>

## Assignments Problems

<details>
<summary>(Optional) Nimm</summary>
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

## Optional Worked Examples

- [x] Lecture Examples

 ## Optonal Related Reading

- [ ] [Lecture Slides](https://codeinplace2020.github.io/faqs/8-CoreComplete.pdf)
- [x] [Functions](https://codeinplace2021.github.io/pythonreader/en/functions/)
- [x] [Doc Tests](https://codeinplace2021.github.io/pythonreader/en/doctests/)
