# Lesson 12: Dictionaries May 17th

<details open>
<summary>Learning Goals</summary>
<br />
Understand how to create, use and modify a dictionary variable. Dictionaries are the last variable type you will learn in Code in Place!
</details>

 ## Videos

- [x] Intro
- [x] Dictionaries
- [x] Adding to dictionaries
- [x] Dictionaries are mutable

<details>
<summary>birthday.py</summary>

`birthday.py`
```python
"""
File: birthday.py
-----------------
Program to show an example of using dictionaries with functions.
"""


def have_birthday(dict, name):
    """
    Print a birthday message and increment the age of the person
    with the given name in the dictionary passed in.
    """
    print("You're one year older, " + name + "!")
    dict[name] += 1


def main():
    ages = {'Chris': 33, 'Julie': 22, 'Mehran': 50}
    print(ages)
    have_birthday(ages, 'Chris')
    print(ages)
    have_birthday(ages, 'Mehran')
    print(ages)


# Python boilerplate.
if __name__ == '__main__':
    main()
```
</details>
<hr />

- [x] Dictionary functions
- [x] count_characters.py

<details>
<summary>count_characters.py</summary>

`count_characters.py`
```python
"""
File: count_characters.py
-------------------------
This program counts the number of each character in the string TEXT.
It uses a dictionary to store the results, where each key is a
character and the corresponding value is the number of times that
character appeared in the string.
"""

TEXT = 'Happy day! I love the Code in Place community!'


def get_counts_dict(str):
    """
    Returns a dictionary with where each key is a character and the corresponding
    value is the number of times that character appeared in the string str passed in.
    """
    counts = {}                             # create empty dictionary

    for ch in str:
        if ch not in counts:
            counts[ch] = 1
        else:
            counts[ch] += 1

    return counts


def print_counts(dict):
    """
    This function prints out the key and its associated value for each
    key/value pair in the dictionary passed in.
    """
    print('Counts from dictionary')
    for key in dict:
        print(str(key) + ' = ' + str(dict[key]))


def main():
    """
    Display the number of times each character appears in the constant TEXT.
    """
    count_dict = get_counts_dict(TEXT)
    print('count_dict = ', count_dict)
    print_counts(count_dict)


# Python boilerplate.
if __name__ == '__main__':
    main()
```
</details>
<hr />

- [x] phonebook.py

<details>
<summary>phonebook.py</summary>

`phonebook.py`
```python
"""
File: phonebook.py
------------------
Program to show an example of using dictionaries to maintain
a phonebook.
"""


def read_phone_numbers():
    """
    Ask the user for names/numbers to story in a phonebook (dictionary).
    Returns the phonebook.
    """
    phonebook = {}  # Create empty phonebook

    while True:
        name = input("Name: ")
        if name == "":
            break
        number = input("Number: ")
        phonebook[name] = number

    return phonebook


def print_phonebook(phonebook):
    """
    Prints out all the names/numbers in the phonebook.
    """
    for name in phonebook:
        print(name, "->", phonebook[name])


def lookup_numbers(phonebook):
    """
    Allow the user to lookup phone numbers in the phonebook
    by looking up the number associated with a name.
    """
    while True:
        name = input("Enter name to lookup: ")
        if name == "":
            break
        if name not in phonebook:
            print(name + " is not in the phonebook")
        else:
            print(phonebook[name])


def main():
    phonebook = read_phone_numbers()
    print_phonebook(phonebook)
    lookup_numbers(phonebook)


# Python boilerplate.
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

- [ ] []()

 ## Optonal Related Reading

- [ ] [Lecture Slides](https://codeinplace2020.github.io/faqs/12-Dictionaries.pdf)
- [ ] [Dictionaries](https://codeinplace2021.github.io/pythonreader/en/dicts/)
