# Lesson 10: Lists May 12th

<details open>
<summary>Learning Goals</summary>
<br />
Be able to create a list. Be able to modify a list. Be able to loop over a list and access each element!
</details>

 ## Videos

- [x] Intro
- [x] Using the console
- [x] Lists

<details>
<summary>listexamples.py</summary>

`listexamples.py`
```python
"""
File: listexamples.py
---------------------
This program contains examples of using different functionality of
lists to show how you can do different list operations.
"""


def access_list_elements():
    """
    Shows an example of accessing individual elements in a list
    as well as overwriting a value.
    """
    num_list = [10, 20, 30, 40, 50]
    print('num_list =', num_list)
    print('num_list[0] =', num_list[0])
    print('num_list[1] =', num_list[1])
    print('Setting num_list[0] to 15')
    num_list[0] = 15
    print('num_list =', num_list)


def print_individual_list_elements():
    """
    Shows an example of using a for-loop with range to iterate
    through the elements of a list.
    """
    letters = ['a', 'b', 'c', 'd', 'e']
    print('letters =', letters)
    print('length of letters =', len(letters))
    for i in range(len(letters)):
        print(i, "->", letters[i])


def appending_elements():
    """
    Shows two examples of using appending elements onto lists.
    """
    alist = [10, 20, 30]
    print('alist =', alist)
    print('Appending 40 to alist')
    alist.append(40)
    print('Appending 50 to alist')
    alist.append(50)
    print('alist =', alist)

    new_list = []
    print('new_list =', new_list)
    print('Appending a to new_list')
    new_list.append('a')
    print('Appending 4.3 to new_list')
    new_list.append(4.3)
    print('new_list =', new_list)


def popping_elements():
    """
    Shows an example of popping elements off a list.
    """
    alist = [10, 20, 30, 40, 50]
    print('alist =', alist)
    x = alist.pop()
    print('popped element from alist, got', x)
    print('alist =', alist)
    x = alist.pop()
    print('popped element from alist, got', x)
    print('alist =', alist)
    x = alist.pop()
    print('popped element from alist, got', x)
    print('alist =', alist)
    x = alist.pop()
    print('popped element from alist, got', x)
    print('alist =', alist)
    x = alist.pop()
    print('popped element from alist, got', x)
    print('alist =', alist)


def look_up_elements():
    """
    Shows an example of using 'in' to check if a value is contained in
    a list.
    """
    str_list = ['Ruth', 'John', 'Sonia']
    print('str_list =', str_list)
    if 'Sonia' in str_list:
        print('Sonia is in str_list')


def for_each_loop():
    """
    Shows an example of using a for-each loop with a list.
    """
    str_list = ['Ruth', 'John', 'Sonia']
    for elem in str_list:
        print(elem)


def main():
    """
    We call a number of different functions that show the results
    of different list operations to show examples of how they work.
    """
    access_list_elements()
    print_individual_list_elements()
    appending_elements()
    popping_elements()
    look_up_elements()
    for_each_loop()


if __name__ == '__main__':
    main()
```
</details>
<hr />

- [x] List functions

<details>
<summary>listparameter.py</summary>

``
```python
"""
File: listparameter.py
---------------------
This program contains examples of using lists as parameters,
especially in different type of for loops.
"""


def add_five_buggy(alist):
    """
    Attempts to add 5 to all the elements in the list.
    BUGGY CODE!  Does not actually add 5 to the list elements
    if values are primitive type (like int or float), since
    value would just be a local copy of such variables.
    """
    for value in alist:
        value += 5


def add_five_working(alist):
    """
    Successfully adds 5 to all the elements in the list.
    Changes made to the list persist after this function ends
    since we are changing actual values in the list.
    """
    for i in range(len(alist)):
        alist[i] += 5


def create_new_list(alist):
    """
    Shows an example of what happens when you create a new list
    that has the same name as a parameter in a function.  After
    you create the new list, you are no longer referring to the
    parameter "alist" that was passed in
    """
    # This "alist" is referring to the parameter "alist"
    alist.append(9)

    # Creating a new "alist". This is not the same as the parameter
    # passed in.  After this line references to "alist" are no longer
    # referring to the parameter "alist" that was passed in.
    alist = [1, 2, 3]


def main():
    values = [5, 6, 7, 8]
    print('values =', values)

    add_five_buggy(values)
    print('values =', values)

    add_five_working(values)
    print('values =', values)

    values = [5, 6, 7, 8]
    create_new_list(values)
    print('values =', values)


if __name__ == '__main__':
    main()
```
</details>
<hr />

- [x] List looping
- [x] List as params
- [x] averagescores

<details>
<summary>averagescores.py</summary>

``
```python
"""
File: averagescores.py
----------------------
This program reads score values from a user and computes their
average.  It also adds extra credit to all the scores and computes
the new average.
"""


EXTRA_CREDIT = 5


def get_scores():
    """
    Asks the user for a list of scores (numbers).
    Returns a list containing the scores
    """
    score_list = []
    while True:
        score = float(input("Enter score (0 to stop): "))
        if score == 0:
            break
        score_list.append(score)
    return score_list


def compute_average(score_list):
    """
    Returns the average value of the list of scores passed in.
    """
    num_scores = len(score_list)
    total = sum(score_list)
    return total / num_scores


def give_extra_credit(score_list, extra_credit_value):
    """
    Adds extra_credit_value to all the values in score_list.
    """
    for i in range(len(score_list)):
        score_list[i] += extra_credit_value


def print_list(alist):
    """
    Prints all the values in the list passed in
    """
    for value in alist:
        print(value)


def main():
    """
    Computes average for a set of scores entered by the user.
    Then adds extra credit to scores and recomputes average.
    """
    scores = get_scores()
    print("Scores are:")
    print_list(scores)
    avg = compute_average(scores)
    print('Average score is', avg)

    print('Adding extra credit:', EXTRA_CREDIT, "points")
    give_extra_credit(scores, EXTRA_CREDIT)
    print("New scores are:")
    print_list(scores)
    avg = compute_average(scores)
    print('New average is', avg)


if __name__ == '__main__':
    main()
```
</details>
<hr />

## Assignments Problems

<details>
<summary></summary>
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

</details>
</details>
<hr />

## Optional Worked Examples

- [x]

<details>
<summary>get_first.py</summary>

`get_first.py`
```python
SAMPLE_LIST = [1, 2, 3, 'a', 'b', 'c']


def get_first_element(lst):
    # delete the pass statement below and write your code here!
    """
    >>> get_first_element(SAMPLE_LIST)
    1
    """
    print(lst[0])


def main():
    get_first_element(SAMPLE_LIST)


if __name__ == "__main__":
    main()
```

```sh
[user@sahara ~]$  python -m doctest get_first.py -v
Trying:
    get_first_element(SAMPLE_LIST)
Expecting:
    1
ok
2 items had no tests:
    get_first
    get_first.main
1 items passed all tests:
   1 tests in get_first.get_first_element
1 tests in 3 items.
1 passed and 0 failed.
Test passed.
[user@sahara ~]$
```
</details>

<hr />
<details>
<summary>get_last.py</summary>

`get_last.py`
```python
SAMPLE_LIST = [1, 2, 3, 'a', 'b', 'c']


def get_last_element(lst):
    # delete the pass statement below and write your code here!
    print(lst.pop())


def main():
    get_last_element(SAMPLE_LIST)


if __name__ == "__main__":
    main()
```

</details>

<hr />
<details>
<summary>get_list.py</summary>

`get_list.py`
```python
def main():
    # delete the pass statement below and write your code here!
    lst = []

    while True:
        # as the type of the expected value
        # isn't specified, there is no need
        # for check
        value = input("Enter a value: ")
        if value == "":
            break
        lst.append(value)
    print(lst)


if __name__ == "__main__":
    main()
```
</details>

<hr />
<details>
<summary>shorten.py</summary>

`shorten.py`
```python
# SAMPLE_LIST = ['a', 'b']
SAMPLE_LIST = ['a', 'b', 'c', 'd', 'e']
MAX_LENGTH = 3


def shorten(lst, max_len):
    """
    >>> shorten(['a', 'b', 'c', 'd', 'e'], 3)
    e
    d
    >>> shorten(['a', 'b', 'c'], 3)
    >>> shorten(['a', 'b'], 3)
    """
    # delete the pass statement below and write your code here!
    while len(lst) > max_len:
        print(lst.pop())


def main():
    shorten(SAMPLE_LIST, MAX_LENGTH)


if __name__ == "__main__":
    main()
```

```sh
[user@sahara ~]$ python -m doctest shorten.py  -v
Trying:
    shorten(['a', 'b', 'c', 'd', 'e'], 3)
Expecting:
    e
    d
ok
Trying:
    shorten(['a', 'b', 'c'], 3)
Expecting nothing
ok
Trying:
    shorten(['a', 'b'], 3)
Expecting nothing
ok
2 items had no tests:
    shorten
    shorten.main
1 items passed all tests:
   3 tests in shorten.shorten
3 tests in 3 items.
3 passed and 0 failed.
Test passed.
```
</details>

<hr />
<details>
<summary>count_even.py</summary>

`count_even.py`
```python
SAMPLE_LIST = [1, 2, 3, 4, 5, 6]


def count_even(lst):
    """
    Returns number of even numbers in list.
    >>> count_even([1,2,3,4])
    2
    >>> count_even([1,3,5,7])
    0
    """
    # delete the pass statement below and write your code here!
    n = 0

    for item in lst:
        if item % 2 == 0:
            n += 1
    print(n)


def main():
    count_even(SAMPLE_LIST)


if __name__ == "__main__":
    main()
```

```sh
[user@sahara ~]$ python -m doctest count_even.py -v
Trying:
    count_even([1,2,3,4])
Expecting:
    2
ok
Trying:
    count_even([1,3,5,7])
Expecting:
    0
ok
2 items had no tests:
    count_even
    count_even.main
1 items passed all tests:
   2 tests in count_even.count_even
2 tests in 3 items.
2 passed and 0 failed.
Test passed.
```
</details>

<hr />
<details>
<summary>find_karel.py</summary>

`find_karel.py`
```python
SAMPLE_ROSTER = ['miranda', 'karel', 'shrek', 'donkey']


def find_karel(roster):
    """
    Prints whether or not Karel is in the roster.
    >>> find_karel(['chris', 'mehran'])
    Karel isn't here.
    >>> find_karel(['karel', 'is', 'here'])
    Karel is here!
    """
    # delete the pass statement below and write your code here!
    flag = False
    for item in roster:
        if item == 'karel':
            flag = True
    if flag:
        print("Karel is here!")
    else:
        print("Karel isn't here.")


def main():
    # delete the pass statement below and write your code here!
    find_karel(SAMPLE_ROSTER)


if __name__ == "__main__":
    main()
```

```sh
Trying:
    find_karel(['chris', 'mehran'])
Expecting:
    Karel isn't here.
ok
Trying:
    find_karel(['karel', 'is', 'here'])
Expecting:
    Karel is here!
ok
2 items had no tests:
    find_karel
    find_karel.main
1 items passed all tests:
   2 tests in find_karel.find_karel
2 tests in 3 items.
2 passed and 0 failed.
Test passed.
```
</details>

 ## Optonal Related Reading

- [ ] [Lecture Slides](https://codeinplace2020.github.io/faqs/10-Lists.pdf)
- [x] [Lists](https://codeinplace2021.github.io/pythonreader/en/lists/)
