---
title: Data Structures in Python
subtitle: Basic introduction and operation for all kinds of data structure based on Python.

# Summary for listings and search engines
summary: This article summarizes the characteristics and operations of various basic data structures in Python, such as lists and dictionaries, using simple examples.

# Link this post with a project
projects: []

# Date published
date: '2024-02-11T00:00:00Z'

# Date updated
lastmod: '2024-02-11T00:00:00Z'

# Is this an unpublished draft?
draft: false

# Show this page in the Featured widget?
featured: false

# Featured image
# Place an image named `featured.jpg/png` in this page's folder and customize its options here.
image:
  caption: ''
  focal_point: ''
  placement: 2
  preview_only: false

authors:
  - admin

tags:
  - Python
  - Data Structure

categories:
  - Basic Learning
---

# **1 Basic Conception and Characteristics**

1. **Set**：`set = {a, b, c, ‘d', ...}`

    - It can consist of **multiple categories of data**
    - The elements are **unordered**
    - It **doesn't contain duplicate elements**, which will be automatically overwritten**
    - In programming languages, it does not directly reflect * * and is the foundation of other data structures

2. **List**：`list = [a1, a2, 'a3', ...]`

   - It can consist of **multiple categories of data**
   - The elements are **ordered**
   - **Variable length**, which means elements can be added or deleted 

3. **Array**：`array = [a[0], a[1], a[2], ...]`

   - It can consist of **only one category of data: number**
   - The elements are **ordered**
   - Continuous storage, only recording the address of the first element
   - In Python, an Array is represented as a List.
   
4. **Dictionary**： `dict = {key1:val1, key2:val2, ...}`

   - It can consist of **multiple categories of data**
   - The elements are **unordered**
   - **value`vali=dict[keyi]`** can be queried by **key`keyi`**

5. **Tuple**：`tuple = (obj[0], obj[1], [obj[2][0], obj[2][1], ...])`

   - It can consist of **multiple categories of data**
   - The elements are **ordered**
   - The element **cannot be directly assigned a value**. However, the element in the tuple (such as a list or dictionary `obj [2]`) can be changed

# 2 Operations

## 2.1 List

### *2.1.1. Creation*

  - `list=[]`: Create null list.
  
  - `list=[a0] * N`: Create a list of `N` elements with an initialization value of `a0`
  
    ```python
    s = [0] * 5
    print(s)
    # OUTPUT:
    [0, 0, 0, 0, 0]
    ```

### *2.1.2. Indexing*

- `index=start:stop:step` or `index=num`
  
  ```python
  s = [1,2,3,4,5]
  ```
  
  - `start`: starting index（**default**: 0, **minimum value**: 0, **maximum value**: length of the list），
  - `stop`: ending index（**default**: length of the list+1, **minimum value**: 0, **maximum value**: length of the list+1），
  - `step`: step size，**sequence of indexes**：{start, start**+step**, start**+2\*step**, ..., start**+n\*step**, **?**}，if start+ **(n+1)\*step** > **stop-1** ，the last index: start+ **n\*step**
  
    ```python
    print(s[0:3])
    # OUTPUT:
    [1, 2, 3]
    
    print(s[0:5:2])
    # OUTPUT:
    [1, 3, 5]
    
    print(s[::2])
    # OUTPUT:
    [1, 3, 5]
    
    print(s[1::2])
    # OUTPUT:
    [2, 4]
    
    print(s[-1::])
    # OUTPUT:
    [5]
    
    print(s[::-1])
    # OUTPUT:
    [5, 4, 3, 2, 1]
    ```
  
  - index of a list can be in {0, 1, 2, ..., length of the list-1} or {-length of the list, ..., -2, -1}
  
    ```python
    print(s[-2])
    # OUTPUT:
    4
    
    print(s[3])
    # OUTPUT:
    4
    ```
  
  - `:` represents **ALL**，`list[a:]` indicates all elements whose index $\geq$ `a`，`list[::-1]` indicates reversed `list`
  
    ```python
    print(s[2:])
    # OUTPUT:
    [3, 4, 5]
    
    print(s[2::])
    # OUTPUT:
    [3, 4, 5]
    ```

### *2.1.3. Adding elements*

- `list.append(obj)`: Add a new object at **the end** of the list, taking **only one parameter**, which can be any data type. The added element **keeps its original structural type** in the list。

  ```python
  s = [1, 2, 3]
  s.append(4)
  print(s)
  # OUTPUT:
  [1, 2, 3, 4]
  
  s = [1, 2, 3]
  s.append([5, 6])
  print(s)
  # OUTPUT:
  [1, 2, 3, [5, 6]]
  ```

- `list.extend(seq)`: Add **all elements** from another list sequence `seq` at **the end** of the list at once
  
  Commonly used to expand the original list with a new list
  
  ```python
  s1 = [1, 2, 3]
  s2 = [4, 5]
  s1.extend(s2)
  print(s1)
  # OUTPUT:
  [1, 2, 3, 4, 5]
  ```
  
- `list.insert(index, obj)`: Insert a `obj` at the index position `index`。

  ```python
  s = [1,2,4]
  s.insert(2,3)
  print(s)
  # OUTPUT:
  [1, 2, 3, 4]
  ```

### *2.1.4. Removing elements*

- `list.remove(obj)`: Remove the first match of `obj` from the list.

  ```python
  s = [1,2,4,3,4]
  s.remove(4)
  print(s)
  # OUTPUT:
  [1, 2, 3, 4]
  ```

- `list.pop(index)`: Remove the element with index `index` from the list (**default**: the last element) and **return the value** of that element

  ```python
  s = [1,2,4,3,4]
  k = s.pop(2)
  print(k,s)
  # OUTPUT:
  4 [1, 2, 3, 4]
  ```

- `del list[index]`: Delete single or multiple elements.

  ```python
  s = [1, 2, 4, 5, 3, 4, 5]
  del s[2:4]
  print(s)
  # OUTPUT:
  [1, 2, 3, 4, 5]
  ```

### *2.1.5. Searching or Counting*

- `list.count(obj)`: Count the number of times an element appears in the list

  ```python
  s = [1, 3, 4, 3, 4, 5, 6, 4]
  print(s.count(4))
  # OUTPUT:
  3
  ```

- `list.index(x, start, end)`: Find the index position of the first matching item of a certain value from the list. `start` defaults to 0, and `end` defaults to the end of the list

  ```python
  s = [1, 3, 4, 3, 4, 5, 6, 4]
  pos = s.index(4)
  print(pos)
  # OUTPUT:
  2
  
  pos = s.index(4,5)
  print(pos)
  # OUTPUT:
  7
  
  pos = s.index(4,3,6)
  print(pos)
  # OUTPUT:
  4
  ```

### *2.1.6. Arrangement*

- `list.reverse()`: Reverse the list

  ```python
  s = [1, 2, 3, 4, 5]
  s.reverse()
  print(s)
  # OUTPUT:
  [5, 4, 3, 2, 1]
  ```

- `list.sort(key=None, reverse=False)`: Sort the elements in the list
  
  ```python
  s = [4, 2, 5, 3, 1]
  s.sort()
  print(s)
  # OUTPUT:
  [1, 2, 3, 4, 5]
  ```
  
  - Default: ascend order，`reverse=True`: descend order。
  
    ```python
    s = [4, 2, 5, 3, 1]
    s.sort(reverse=True)
    print(s)
    # OUTPUT:
    [5, 4, 3, 2, 1]
    ```
  
  - `key` is a sorting reference, suitable for situations where the list element is a list (two-dimensional list)
  
    ```python
    s = [[4, 'a'], [2, 'b'], [5, 'c'], [3, 'd'], [1, 'e']]
    s.sort(key=lambda x: x[0])
    print(s)
    # OUTPUT:
    [[1, 'e'], [2, 'b'], [3, 'd'], [4, 'a'], [5, 'c']]
    ```

### *2.1.7. Common Operators*

  ```python
  s1 = [1, 2, 3]
  s2 = [4, 5, 6]
  ```

  - `+` -- `list = list1+list2`: Splice `list1` and `list2` into a new list `list = list1.extend(list2)`

    ```python
    s = s1 + s2
    print(s)
    # OUTPUT:
    [1, 2, 3, 4, 5, 6]
    ```

  - `*` -- `list = list1*3`: Create three copies of `list1` and concatenate them into a new list `list = list1.extend(list1.extend(list1))`，supporting self-multiplication `*=`

    ```python
    s = s1 * 3
    print(s)
    # OUTPUT:
    [1, 2, 3, 1, 2, 3, 1, 2, 3]
    
    s1 *= 2
    print(s1)
    # OUTPUT:
    [1, 2, 3, 1, 2, 3]
    ```

  - `in` and `not in` -- `res = obj in list` and `res = obj not in list`: Judge whether `obj` is in `list` or not，return bool value `res = True` or `res = False`

    ```python
    print(4 in s2)
    # OUTPUT:
    True
    
    print(4 not in s2)
    # OUTPUT:
    False
    
    print(1 in s2)
    # OUTPUT:
    False
    
    print(1 not in s2)
    # OUTPUT:
    True
    ```

## 2.2 String

### *2.2.1. Toggle Case*

- `str.capitalize()`: Convert the first character of the string to uppercase, the other letters to lowercase, and return the converted string.

  ```python
  s = 'i Love You'
  s.capitalize()
  # OUTPUT:
  'I love you'
  ```

- `str.lower()`: Convert all uppercase characters in the string to lowercase and return the converted string. If there are no uppercase letters, return the original string

  ```python
  s = 'I Love You'
  s.lower()
  # OUTPUT:
  'i love you'
  ```

- `str.upper()`: Convert all lowercase characters in the string to uppercase and return the converted string. If there are no lowercase letters, return the original string

  ```python
  s = 'I Love You'
  s.upper()
  # OUTPUT:
  'I LOVE YOU'
  ```

- `str.swapcase()`: Convert uppercase to lowercase, lowercase to uppercase, and return the converted string.

  ```python
  s = 'I Love You'
  s.swapcase()
  # OUTPUT:
  'i lOVE yOU'
  ```

### *2.2.2. Checking Characters*

- `str.count(str, beg=0, end=len(string))`: Return the number of times `str` appears in a string. If `beg` or `end` is specified, returns the number of times `str` appears within the specified range of $[begin, end-1)$.

  ```python
  s = 'I Love You'
  s.count('o')
  # OUTPUT:
  2
  
  s.count('o',4)
  # OUTPUT:
  1
  
  s.count('o', 4, 7)
  # OUTPUT:
  0
  ```

- `str.endswith(suffix, beg=0, end=len(string))`: Check if the string ends with the specified substring `suffix`. If so, return `True`; otherwise, return `False`. If `beg` or `end` is specified, returns the number of times `str` appears within the specified range of $[begin, end-1)$.


  ```python
  s = 'I Love You'
  s.endswith('you')
  # OUTPUT:
  False
  
  s.endswith('You')
  # OUTPUT:
  True
  
  s.endswith('You', 0, 8)
  # OUTPUT:
  False
  
  s.endswith('Yo', 0, 8)
  # OUTPUT:
  False
  
  s.endswith('Yo', 0, 9)
  # OUTPUT:
  True
  ```

- `str.startswith(substr, beg=0,end=len(string)) `: Check if the string begins with the specified substring `substr`. If so, return `True`; otherwise, return `False`. If `beg` or `end` is specified, returns the number of times `str` appears within the specified range of $[begin, end-1)$.

  ```python
  s = 'I Love You'
  s.startswith('y')
  # OUTPUT:
  False
  
  s.startswith('I ')
  # OUTPUT:
  True
  
  s.startswith('I ',3)
  # OUTPUT:
  False
  ```

- `str.find(str, beg=0, end=len(string))`: Check if `str` is included in the string. If the ranges `beg` and `End` are specified, check if they are included. If they are, return the starting index value. Otherwise, return `-1`.

  ```python
  s = 'I Love You'
  s.find('Love')
  # OUTPUT:
  2
  
  s.find('Hate')
  # OUTPUT:
  -1
  
  s.find('Love',7)
  # OUTPUT:
  -1
  ```

- `str.rfind(str, beg=0,end=len(string))` is similar to `find() `，but it check **from the right**。

  ```python
  s = 'I Love You'
  s.rfind('Love')
  # OUTPUT:
  2
  
  s.rfind('Hate')
  # OUTPUT:
  -1
  
  s.rfind('Love',7)
  # OUTPUT:
  -1
  ```

- `str.isnumeric()`: If the string contains only numeric characters, return `True`; otherwise, return `False`.

  ```python
  s = 'I Love You'
  s1 = '520'
  s.isnumeric()
  # OUTPUT:
  False
  
  s1.isnumeric()
  # OUTPUT:
  True
  ```

### *2.2.3. Expanding*

- `str.ljust(width[, fillchar])`: Return a string which aligned with the original string from the left and fill it with a new string of length `width` using `fillchar` (**default** space).

  ```python
  s = 'I Love You'
  s.ljust(15)
  # OUTPUT:
  'I Love You     '
  
  s.ljust(15,'~')
  # OUTPUT:
  'I Love You~~~~~'
  ```

- `str.rjust(width[, fillchar])`: Return a string which aligned with the original string from the right and fill it with a new string of length `width` using `fillchar` (**default** space).

  ```python
  s = 'I Love You'
  s.rjust(15)
  # OUTPUT:
  '     I Love You'
  
  s.rjust(15,'.')
  # OUTPUT:
  '.....I Love You'
  ```

### *2.2.4. Striping*

- `str.lstrip([chars])`: Remove spaces or specified characters at the start of the string.

  ```python
  s = 'I Love You'
  s.lstrip('I ')
  # OUTPUT:
  'Love You'
  
  s.lstrip('Love')
  # OUTPUT:
  'I Love You'
  ```

- `str.rstrip([chars])`: Remove spaces or specified characters at the end of the string.

  ```python
  s = 'I Love You'
  s.rstrip('u')
  # OUTPUT:
  'I Love Yo'
  
  s.rstrip('Love')
  # OUTPUT:
  'I Love You'
  ```

- `str.strip([chars])`: Perform both `lstrip()` and `rstrip()`。

  ```python
  s = 'I Love You'
  s.strip('I')
  # OUTPUT:
  ' Love You'
  
  s.strip('You')
  # OUTPUT:
  'I Love '
  ```

### *2.2.5. Segemntation*

- `str.partition(sub)`: Find the substring `sub` and divides the string into a triplet`(pre_sub,sub,fol_sub)`. If the string does not contain `sub`, `('str','','')` is returned。

  ```python
  s = 'I Love You'
  s.partition('Love')
  # OUTPUT:
  ('I ', 'Love', ' You')
  
  s.partition('Him')
  # OUTPUT:
  ('I Love You', '', '')
  ```

- `str.rpartition(sub)` is similar to `str.partition() `，but it search **from the right**

- `str.split(str="", num)`: Slice the string with `str` (**default**: space) as the delimiter. If the `num` parameter is set, only `num` times are separated, and the list of concatenated substrings after slicing is returned.

  ```python
  s = 'I Love You'
  s.split(' ')
  # OUTPUT:
  ['I', 'Love', 'You']
  
  s.split(' ',1)
  # OUTPUT:
  ['I', 'Love You']
  ```

### *2.2.6. Replacing elements*

- `replace(old, new [, max])`: Replace `old` to `new`. If the `max` parameter is specified, not more than `max` `old` will be replaced (from left to right)。

  ```python
  s = 'I Love You'
  s.replace('o', '0')
  # OUTPUT:
  'I L0ve Y0u'
  
  s.replace('o', '0', 1)
  # OUTPUT:
  'I L0ve You'
  ```

### *2.2.7. Operators*

- `str1+str2`: Merge `str1` and `str2` into one string.

  ```python
  s1 = 'Love'
  s2 = 'U'
  s = s1 + s2
  print(s)
  # OUTPUT:
  'LoveU'
  ```

  

### *2.2.8. Formatting of String*

- Format the string with `str.format()` method `'... {key1:type1} ... {key2:type2} ...'.format(key1 = ch1, key2 = ch2)`

- Format the string with `%` identifier `'... %type1 ... %type2 ...'%(ch1, ch2)`

- Meanings of identifier：`<~>` represent the custom value.
  - `%d`：integral --> character or string
  
    ```python
    s1 = '%d years old' % (23)
    print(s1)
    # OUTPUT:
    23 years old
    
    s2 = '{a:d} years old'.format(a=23)
    print(s2)
    # OUTPUT:
    23 years old
    ```
  
  - `%c`：ASCII --> character or string
  
    ```python
    s1 = 'It is %c' % (97)
    print(s1)
    # OUTPUT:
    It is a
    
    s2 = 'It is {key:c}'.format(key=97)
    print(s2)
    # OUTPUT:
    It is a
    ```
  
  - `%o`：integral --> Octal number --> character or string
  
  - `%x`：integral --> Hexadecimal number --> character or string (lowercase letter)
  
  - `%X`：integral --> Hexadecimal number --> character or string (uppercase letter)
  
    ```python
    '%o' % (11)
    # OUTPUT:
    '13'
    
    '%x' % (11)
    # OUTPUT:
    'b'
    
    '%X' % (11)
    # OUTPUT:
    'B'
    ```
  
  - `%.<k>f`：Keep `k` decimal places --> character or string
  
    ```python
    '%.2f' % (11.4514)
    # OUTPUT:
    Out[9]: '11.45'
    ```
  
  - `%<m>.<k>f`：Keep `k` decimal places --> character or string (right shift of string `m` bit with space filling)
  
    ```python
    '%8.2f' % (11.4514)
    # OUTPUT:
    '   11.45'
    ```
  
  - `%.<k>e`：Scientific Notation Form with `k` Decimal Places --> character or string 
  
    ```python
    '%.3e' % (114514)
    # OUTPUT:
    '1.145e+05'
    ```
  
  - `%<m>d`：integral --> character or string (right shift of string `m` bit with space filling, left shift if `m`<0）
  
    ```python
    '%4d' % (12)
    # OUTPUT:
    '  12'
    '%-4d' % (12)
    # OUTPUT:
    '12  '
    ```
  
  - `%s`：Direct filling
  
  - `%r`：Add string as reference content（`'...'str'...'`）
  
    ```python
    'I say: %r' % ('I Love U!')
    # OUTPUT:
    "I say: 'I Love U!'"
    ```

```python
'I wiil %s you %d times' % ('LOVE',3000)
# OUTPUT:
'I wiil LOVE you 3000 times'

'I wiil {0} you {b:.2f} times'.format('LOVE',b=3000)
# OUTPUT:
'I wiil LOVE you 3000.00 times'

'I wiil {a:s} you {b:.2f} times'.format(a='LOVE',b=3000)
# OUTPUT:
'I wiil LOVE you 3000.00 times'

'I wiil {0:s} you {1:.2f} times'.format('LOVE',3000)
# OUTPUT:
'I wiil LOVE you 3000.00 times'
```



### *2.2.9. Type Judgment and Transformation*

- `ch.isupper()`: Check whether `ch` is uppercase or not.

- `ch.islower()`: Check whether `ch` is lowercase or not.

- `ch.isdigit()`: Check whether `ch` is number or not.

- `ord(ch)`: Transform `ch` into corresponding ASCII

  ```python
  s = 'Ab4*'
  for ch in s:
      if ch.isupper():
          print(ch+' is an upper letter')
      elif ch.islower():
          print(ch+' is a lower letter')
      elif ch.isdigit():
          print(ch+' is a number')
      else:
          print('ASCII of %s is %d' % (ch,ord(ch)))
  
  # OUTPUT:
  A is an upper letter
  b is a lower letter
  4 is a number
  ASCII of * is 42
  ```

  

## 2.3 Dictionary and Default Dictionary

### *2.3.1. Creation*

- `dict.fromkeys(seq[, value])`: Create a new dictionary，`seq` is keys of the dictionary，`value` is initial value of all keys。

  ```python
  seq = ['a', 'b', 'c']
  dict.fromkeys(seq,[1, 2, 3])
  # OUTPUT:
  {'a': [1, 2, 3], 'b': [1, 2, 3], 'c': [1, 2, 3]}
  ```

- `dict.setdefault(dict, key, default=None)` and `dict.get(dict, key, default=None)`: If `key` is not in the dictionary，`key` will be added and initialized with value `default`.

  ```python
  dic = {'a': 1, 'b': 2, 'c': 3}
  dict.setdefault(dic,'d',6)
  dic['d']
  # OUTPUT:
  6
  ```

- `collections.defaultdict(type)`: Constraint the type `type` of value in the dictionary. If `key` doesn't exist，set value of `key` as default：

  ```python
  import collections
  ```

  1.`list` -- `[]`

  ```python
  dic = collections.defaultdict(list)
  dic['a']
  # OUTPUT:
  []
  ```
  
  2.`int` -- `0`
  
  ```python
  dic = collections.defaultdict(int)
  dic['a']
  # OUTPUT:
  0
  ```
  
  3.`str` -- `''`
  
  ```python
  dic = collections.defaultdict(str)
  dic['a']
  # OUTPUT:
  ''
  ```
  
  4.`set` -- `set()`
  
  ```python
  dic = collections.defaultdict(set)
  dic['a']
  # OUTPUT:
  set()
  ```

### *2.3.2. Indexing*

```python
dic = {'a': 1, 'b': 2, 'c': 3}
```

- `dict[key]`: Index the corresponding value of the `key` in the dictionary.

  ```python
  dic['b']
  # OUTPUT:
  2
  ```

- `dict.keys()` returns all keys in the dictionary as a iterable object，which can be transformed into a list with `list()`.

  ```python
  dic.keys()
  # OUTPUT:
  dict_keys(['a', 'b', 'c'])
  
  list(dic.keys())
  # OUTPUT:
  ['a', 'b', 'c']
  ```

- `dict.values()` returns all values in the dictionary as a iterable object, which can be transformed into a list with `list()`.

  ```python
  dic.values()
  # OUTPUT:
  dict_values([1, 2, 3])
  
  list(dic.values())
  # OUTPUT:
  [1, 2, 3]
  ```

- `key in dict` or `key not in dict`: Check whether `key` is in the dictionary or not.

  ```python
  print('b' in dic)
  # OUTPUT:
  True
  
  print('d' in dic)
  # OUTPUT:
  False
  
  print('c' not in dic)
  # OUTPUT:
  False
  
  print('d' not in dic)
  # OUTPUT:
  True
  ```

### *2.2.3. Deleting Elements*

```python
dic = {'a': 1, 'b': 2, 'c': 3}
```

- `dict.pop(key[,default])`: Delete corresponding value of the `key`，returning deleted value. `key` must be provided. If `key` doesn't exist，return `default`。

  ```python
  dic = {'a': 1, 'b': 2, 'c': 3}
  d = dic.pop('d', -1)
  print(d)
  # OUTPUT:
  -1
  
  a = dic.pop('a', -1)
  print(a)
  # OUTPUT:
  1
  
  dic
  # OUTPUT:
  {'b': 2, 'c': 3}
  ```

- `del dict[key]`: Delete corresponding value of the `key`.

  ```python
  del dic['b']
  dic
  # OUTPUT:
  {'a': 1, 'c': 3}
  ```

- `dict.popitem()`: Randomly return and delete a set of key and corresponding value as `(key, value)`. If the dictionary is null, return `KeyError`.

  ```python
  dic = {'a': 1, 'b': 2, 'c': 3}
  new = dic.popitem()
  print(new)
  # OUTPUT:
  ('c', 3)
  
  dic
  # OUTPUT:
  {'a': 1, 'b': 2}
  ```

- `dict.clear()`: Delete all.

  ```python
  dic.clear()
  dic
  # OUTPUT:
  {}
  ```

### *2.3.4. Expanding*

- `dict.update(dict2)` update `dict` with `key:value` in `dict2`.

  ```python
  dic = {'a': 1, 'b': 2, 'c': 3}
  dic2 = {'d': 4, 'e': 5}
  dic.update(dic2)
  dic
  # OUTPUT:
  {'a': 1, 'b': 2, 'c': 3, 'd': 4, 'e': 5}
  ```

  

## 2.4 Set

### *2.4.1. Creation*

- `set()`: Create a null set. `{}` is not ok, because it will be seem as dictionary.
- `set={a,b,c,...}`: Create a set with elements.

### *2.2.2. Adding Elements*

- `set.add(element)`: Add `element` into the `set`. Existed element will not be added repeatly.

  ```python
  s = set()
  s.add(1)
  print(s)
  # OUTPUT:
  {1}
  
  s.add(1)
  print(s)
  # OUTPUT:
  {1}
  ```

- `set.update(set2)` add elements of `set2` into `set1`. Existed elements will not be added repeatly.

  ```python
  s = {1,2,3}
  s2 = {3,4,5}
  s.update(s2)
  print(s)
  # OUTPUT:
  {1, 2, 3, 4, 5}
  ```

### *2.2.3. Deleting Elements*
- `set.remove(item) `: Remove `item` in the `set`. **`item` must exist in the `set`**

  ```python
  s = {1,2,3}
  s.remove(2)
  print(s)
  # OUTPUT:
  {1, 3}
  ```

- `set.discard(value)` Remove `value` in the `set`。 **`value` doesn't need to exist in the `set`**

  ```python
  s = {1,2,3}
  s.discard(2)
  print(s)
  # OUTPUT:
  {1, 3}
  
  s.discard(4)
  print(s)
  # OUTPUT:
  {1, 3}
  ```

- `set.pop()`: Randomly remove an element in the `set`.

  ```python
  s = {1,2,3}
  s.pop()
  print(s)
  # OUTPUT:
  {2, 3}
  ```

### *2.2.4. Mathametical Operation*

```python
set1 = {1, 2, 3, 4}
set2 = {2, 4, 6, 8}
```

- `set = set1.intersection(set2)` or `set = set1 & set2`: $set1 \cap set2$

  ```python
  set = set1.intersection(set2)
  print(set)
  # OUTPUT:
  {2, 4}
  
  set = set1 & set2
  print(set)
  # OUTPUT:
  {2, 4}
  ```

- `set1.intersection_update(set2)`: Remove non-overlapping elements to update `set1`.

- `set = set1.union(set2)` or `set = set1 | set2`: $set1 \cup set2$

  ```python
  set = set1.union(set2)
  print(set)
  # OUTPUT:
  {1, 2, 3, 4, 6, 8}
  
  set = set1 | set2
  print(set)
  # OUTPUT:
  {1, 2, 3, 4, 6, 8}
  ```

- `set = set1.difference(set2)` or `set = set1 - set2`: Return difference of two sets

  ```python
  set = set1.difference(set2)
  print(set)
  # OUTPUT:
  {1, 3}
  
  set = set1 - set2
  print(set)
  # OUTPUT:
  {1, 3}
  ```

- `set1.difference_update(set2)` update `set1` to the difference of two sets.

- `set1.issuperset(set2)` or `set1 >= set2`: Check whether $set2 \subset set1$ or not.

  ```python
  set1.issuperset(set2)
  # OUTPUT:
  False
  
  set1 >= set2
  # OUTPUT:
  False
  ```

- `set1.isdisjoint(set2)`: Check two sets are intersect or not.

  ```python
  set1.isdisjoint(set2)
  # OUTPUT:
  False
  ```

## 2.5 Tuple

- Creation：`tuple=(a,b,[c,d],...)`

- Index like **List**
  
- Operators

  ```python 
  tup1 = (1, 2, [3, 4])
  tup2 = ({'a':1, 'b':2, 'c':3}, {4, 5, 6}, 2, [3, 4])
  ```

  - `+` -- `tuple = tuple1+tuple2`: Concatenate

    ```python
    tup = tup1 + tup2
    print(tup)
    # OUTPUT:
    (1, 2, [3, 4], {'a': 1, 'b': 2, 'c': 3}, {4, 5, 6}, 2, [3, 4])
    ```

  - `*`-- `tuple = tuple1*3`: Copy and Concatenate

    ```python
    tup = tup1 * 3
    print(tup)
    # OUTPUT:
    (1, 2, [3, 4], 1, 2, [3, 4], 1, 2, [3, 4])
    
    tup1 *= 2
    print(tup)
    # OUTPUT:
    (1, 2, [3, 4], 1, 2, [3, 4], 1, 2, [3, 4])
    ```

  - `in` and `not in` -- `res = obj in tuple` and `res = obj not in tuple`: Check Existence

- Tuple cannot be changed, but queried
  
  ```python
  tup = (1, 2, [3, 4], {'a': 1, 'b': 2, 'c': 3}, {4, 5, 6}, 2, [3, 4])
  ```
  
  - `num=tuple.count(obj)`: Count number of `obj` in the `tuple`
  
    ```python
    num = tup.count([3,4])
    print(tup)
    # OUTPUT:
    2
    ```
  
  - `ind=tuple.index(obj)`: Find the index of `obj` that firstly appears from left to right in the `tuple`
  
    ```python
    ind = tup.index([3,4])
    print(ind)
    # OUTPUT:
    2
    ```
  
- Unzip：Assign elements of the tuple to corresponding variable **based on the structure of the tuple**

  ```python
  tup = (1, 2, [3, 4], {'a': 1, 'b': 2, 'c': 3}, {4, 5, 6})
  (a,b,[c,d],dic,s) = tup
  ```

## 3 General Operations

- `len(s)`: Return the number of elements.

- `sorted(iterable, key=None, reverse=False)`: Sort any iterable object.

  `iterable` -- iterable object
  `key` -- Basis for sort. `lambda x: f(x)`: sort `x` based on `f(x)`
  `reverse` -- `reverse = True` descend order， `reverse = False` ascend order（default）。

  ```python
  dic = {'a':2, 'b':5, 'c':1}
  sorted(dic,key = lambda x: dic[x])
  # OUTPUT:
  ['c', 'a', 'b']
  ```

- `reversed(seq)`: Return a reversed sequence，`seq` can be tuple, str, list or range。

- `enumerate(sequence, [start=0])`: Create a tuple `((0,sequence[0]),...)` with combination of the index `i` and corresponding value`sequence[i]`

  ```python
  s = ['a', 'b', 'c']
  for i,e in enumerate(s):
      print(i,e)
  # OUTPUT:    
  0 a
  1 b
  2 c
  ```

- `zip(iter1 [,iter2 [...]])`: Zip corresponding element of multiple sequences into a tuple `((seq1[0],seq2[0],seq3[0]),(seq1[1],seq2[1],seq3[1]),...)`, which can be unzipped by  `*zip()`

  ```python
  s1 = [1, 2, 3]
  s2 = [3, 4, 5, 6]
  s = zip(s1,s2)
  print(list(s))
  # OUTPUT:
  [(1, 3), (2, 4), (3, 5)]
  
  print(*zip(s1))
  # OUTPUT:
  (1,) (2,) (3,)
  
  print(*zip(s2))
  # OUTPUT:
  (3,) (4,) (5,) (6,)
  
  print(*zip(s1,s2))
  # OUTPUT:
  (1, 3) (2, 4) (3, 5)
  
  a1, a2 = zip(*zip(s1,s2))
  print(list(a2))
  # OUTPUT:
  [3, 4, 5]
  ```

  
