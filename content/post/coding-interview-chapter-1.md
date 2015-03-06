+++
categories = []
date = "2015-03-05T18:56:55-05:00"
description = ""
keywords = []
slug = ""
title = "coding interview chapter 1"

+++

###1.1 - Unique Char
> Implement an algorithm to determine if a string has all unique characters.

I'd solve this problem using [sets](https://docs.python.org/3/tutorial/datastructures.html#sets):

```python
    def isUniqueChars(string):
        return len(string) == len(set(string))
```

The explanation on how this work is rather simple, sets don't permit duplicate
values, so a string is formed of only unique chars if and only if, the set
size is the same as the string itself.


###1.3 - Check Permutation
> Given two string, write a method to decide if one is a permutation of the other.

First let's define what is a permutation, this will help understand how to
solve out problem. I'd define permutation of a string as a combination of the
letters of the original string. So in order to a string to be a permutation of
the other they must have:
* The same number of letters.
* The same quantity of each letter.

Using this definition we could simply sort the two strings, if they're equal
we could say that one is a permutation of the other.

```python
    def isPermutation(str1, str2):
        return sorted(str1) == sorted(str2)
```

p.s: Note that using `sorted` in a string, returns a list, but it works anyway.


###1.4 - Replace Spaces
> Write a method to replace all spaces in a string with '%20'

With python this is really simple, we could use
[`strip`](https://docs.python.org/3/library/stdtypes.html#str.strip) and
[`replace`](https://docs.python.org/3/library/stdtypes.html#str.replace), the
first one to remove any trailing spaces, the second one to actually replace
the spaces(' ') with '%20'

```python
    def replaceSpace(string):
        return string.strip().replace(' ', '%20')
```


###1.5 - Compress Word
> Implement a method to perform basic string compression using the counts of
> repeated characters. For example, the string aabcccccaaa would become
> a2blc5a3. If the "compressed" string would not become smaller than the
> original string, your method should return the original string.

The solutions is pretty straighforward, we basically iterate over all the elements, counting them and updating the compressed 'word'.
Note, that there is some 'strange' things happening.

We're using a list in order to concatenate the final string, this is a [Google recommendation](https://google-styleguide.googlecode.com/svn/trunk/pyguide.html#Strings), that using the `+` operator to accumulate a string within a loop, since doing this will result in unnecessary temporary objects.

```python
    def compress(word):
        compressed = []
        current_letter = word[0]
        counter = 0

        for letter in word:
            if letter == current_letter:
                counter += 1
            else:
                compressed.append(current_letter)
                compressed.append(str(counter))

                current_letter = letter
                counter = 1

        #add last sequence
        compressed.append(current_letter)
        compressed.append(str(counter))

        if len(compressed) > len(word):
            return word
        else:
            return ''.join(compressed)
```


###1.6 - Rotate Matrix
> Given an image represented by an NxN matrix, where each pixel in the image
> is a 4 byte, write a method to rotate the image by 90 degrees.

This one is a little bit tricky, I'll show you the code first, and then explain each part.

```python
    def rotate_matrix(matrix):
        return list(zip(*matrix))[::-1]
```

Suppose you have a matrix
<div>
$$
    \begin{bmatrix}
        1 & 2 & 3   \\
        4 & 5 & 6   \\
        7 & 8 & 9
    \end{bmatrix}
$$
</div>
I'm going to use a list of lists to represent our example matrix,

```python
    matrix = [[1, 2, 3],
             [4, 5, 6],
             [7, 8, 9]]
```

By using the
[`zip`](https://docs.python.org/3/tutorial/datastructures.html#sets) with
`*matrix` we're going to see the
[transpose](http://en.wikipedia.org/wiki/Transpose) of the matrix. And from
that, to see a rotated matrix, we only need to revert the order of the rows,
we do that with `[::-1]`

This awesome idea to use the `zip` function to get the transpose of a matrix, was not mine,
but it could be found in Peter Norvig's [IAQ](http://www.norvig.com/python-iaq.html)


###1.7 - Zero out Columns and Rows of Matrix
> Write an algorithm such that if an element in an MxN matrix is 0, its entire
> row and column are set to 0.

This one was pretty boring to do, you basically have to traverse the matrix,
and every time we found a `0` we simply add the values of `i` (row) and `j`
(column) to a set.

I'm choosing a set, because first, we're going to store the value only one
time, also because sets have O(1) complexity to check pertinence, which we use
in our code to avoid traversing columns and rows that we already found a `0`

```python
def find_zero(matrix):
    rows_to_zero = set()
    columns_to_zero = set()

    for i, line in enumerate(matrix):
        if i in rows_to_zero:
            continue
        for j, val in enumerate(line):
            if j in columns_to_zero:
                continue
            if val == 0:
                rows_to_zero.add(i)
                columns_to_zero.add(j)

    return rows_to_zero, columns_to_zero


def zero_out_rows(matrix, rows):
    for i in rows:
        matrix[i] = [0] * len(matrix[i])

    return matrix


def zero_out_columns(matrix, columns):
    for row in matrix:
        for j in columns:
            row[j] = 0

    return matrix


def zero_matrix(matrix):
    rows, columns = find_zero(matrix)
    matrix = zero_out_rows(matrix, rows)
    matrix = zero_out_columns(matrix, columns)

    return matrix
```


###1.8 - String Rotation
> Given two string, s1 and s2, write code to check if s2 is a rotation of s1,
> (e.g: "waterbottle" is a rotation of "erbottlewat").

You basically have to think that in a rotation, there is a point on which we
divide our string in two parts. Let's call the first part `x` and the second
one `y`. The rotation, will be the string `yx`, we could try to do a really
complicated verification for each substring (I did this at first) OR be cleaver
and see that, if we concatenate the original string with it self we will always
have `yx` -> xy + xy = x**yx**y.

```python
def isRotation(s1, s2):
    s1s1 = s1 + s1
    return s2 in s1s1
```

This one, after seeing the answer the author provided, I thought, how stupid I was :disappointed:

Well guys, this was the first chapter, please if you think there is a better
way of solving any of the problems, please comment and tell me.
