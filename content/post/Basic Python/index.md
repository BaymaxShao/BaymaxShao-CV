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

# **1 基本概念以及对比**

1. **集合**set：`set = {a, b, c, ‘d', ...}`

   - 可以包含**多种数据类型**
   - 元素是**无序**的，**不含有重复元素，会自动覆盖**
   - 在程序语言中并**不直接体现**，是其他数据结构的基础

2. **列表**list：`list = [a1, a2, 'a3', ...]`

   - 可以包含**多种数据类型**
   - 元素是**有序**的
   - **长度可变**，可以进行增删操作
   - 特殊的列表形式：**栈与队列**  

3. **数组**array：`array = [a[0], a[1], a[2], ...]`

   - 仅包含**一种数据类型**

   - 元素是**有序**的

   - 连续存储，只记录首位元素的地址

   - 数组是**列表的表现形式**之一，在**Python**中数组表示为**列表类型**
   
   - 与列表的**关键不同点**：数组具有**索引**     
   
4. **字典**dictionary： `dict = {key1:val1, key2:val2, ...}`

   - 可以包含**多种数据类型**
   - 元素是**无序**的
   - 实现**哈希表**的数据结构，利用**键`keyi`**查询对应的**值`vali=dict[keyi]`**

5. **元组**tuple：`tuple = (obj[0], obj[1], [obj[2][0], obj[2][1], ...])`

   - 可以包含**多种数据类型**
   - 元素是**有序**的
   - 元组不可更改，**不可直接对元素赋值**，但元组中**元素（比如`obj[2]`这样的数组或者字典等类型）的元素**可以更改

# 2 Python中各种数据结构的操作

## 2.1 列表list

### 1.创建列表

- 创建方式：
  - `list=[]`创建空列表
  
  - `list=[a0] * N`创建具有`N`个初始化值为`a0`的元素的列表
  
    ```python
    s = [0] * 5
    print(s)
    # OUTPUT:
    [0, 0, 0, 0, 0]
    ```

### 2.索引列表元素

- 索引方式`index=start:stop:step`或`index=num`
  
  ```python
  s = [1,2,3,4,5]
  ```
  
  - `start`为起始索引（默认为首位），`stop`为结束索引（默认为尾位+1），`step`为索引步长，最后最多只索引到**stop-1**
  
  - 索引序列为：{start, start**+step**, start**+2*step**, ..., start**+n\*step**, **stop-1** }，若start+ **(n+1)\*step** > **stop-1** ，则最后一项为start+ **n\*step**
  
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
  
  - 列表索引序列为{0, 1, 2, ..., 列表长度-1}或{-列表长度, ..., -2, -1}
  
    ```python
    print(s[-2])
    # OUTPUT:
    4
    
    print(s[3])
    # OUTPUT:
    4
    ```
  
  - `:`表示索引列表的所有元素，`list[a:]`表示从下标a索引到列表末尾，`list[::-1]`索引`list`对应的的逆序列表
  
    ```python
    print(s[2:])
    # OUTPUT:
    [3, 4, 5]
    
    print(s[2::])
    # OUTPUT:
    [3, 4, 5]
    ```

### 3.向列表中填充元素

- `list.append(obj)` 在列表末尾添加新的对象，只接受一个参数，参数可以是任何数据类型，被追加的元素在 list 中保持着原结构类型。

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

  常和`list.pop(obj)`搭配实现**栈的后入先出**

- `list.extend(seq)` 在列表末尾一次性追加另一个列表序列`seq`中的多个值
  
  常用来利用新列表拓展原列表
  
  ```python
  s1 = [1, 2, 3]
  s2 = [4, 5]
  s1.extend(s2)
  print(s1)
  # OUTPUT:
  [1, 2, 3, 4, 5]
  ```
  
- `list.insert(index, obj)` 在索引为 `index` 位置插入 `obj`。

  ```python
  s = [1,2,4]
  s.insert(2,3)
  print(s)
  # OUTPUT:
  [1, 2, 3, 4]
  ```

### 4.从列表中消除元素

- `list.remove(obj)` 移除列表中`obj`的**第一个匹配项**

  ```python
  s = [1,2,4,3,4]
  s.remove(4)
  print(s)
  # OUTPUT:
  [1, 2, 3, 4]
  ```

- `list.pop(index)` 移除列表中索引为`index`的元素（默认最后一个元素），**并且返回该元素的值**

  ```python
  s = [1,2,4,3,4]
  k = s.pop(2)
  print(k,s)
  # OUTPUT:
  4 [1, 2, 3, 4]
  ```

- `del list[index]` 删除单个或多个对象。

  ```python
  s = [1, 2, 4, 5, 3, 4, 5]
  del s[2:4]
  print(s)
  # OUTPUT:
  [1, 2, 3, 4, 5]
  ```

### 5.查找元素与统计元素数目

- `list.count(obj)`统计某个元素在列表中出现的次数

  ```python
  s = [1, 3, 4, 3, 4, 5, 6, 4]
  print(s.count(4))
  # OUTPUT:
  3
  ```

- `list.index(x, start, end)`从列表中找出某个值**第一个匹配项**的索引位置，`start`不写默认为0，`end`不写默认为列表末尾

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

### 6.排列列表元素：反向与排序

- `list.reverse()`反向列表中元素

  ```python
  s = [1, 2, 3, 4, 5]
  s.reverse()
  print(s)
  # OUTPUT:
  [5, 4, 3, 2, 1]
  ```

- `list.sort(key=None, reverse=False)`对原列表进行排序
  
  ```python
  s = [4, 2, 5, 3, 1]
  s.sort()
  print(s)
  # OUTPUT:
  [1, 2, 3, 4, 5]
  ```
  
  - 默认升序，`reverse=True`则降序排列。
  
    ```python
    s = [4, 2, 5, 3, 1]
    s.sort(reverse=True)
    print(s)
    # OUTPUT:
    [5, 4, 3, 2, 1]
    ```
  
  - key为排序参考，适用于列表元素为列表（二维列表）的情况
  
    ```python
    s = [[4, 'a'], [2, 'b'], [5, 'c'], [3, 'd'], [1, 'e']]
    s.sort(key=lambda x: x[0])
    print(s)
    # OUTPUT:
    [[1, 'e'], [2, 'b'], [3, 'd'], [4, 'a'], [5, 'c']]
    ```

### 7.常用操作符

- 列表常用操作符

  ```python
  s1 = [1, 2, 3]
  s2 = [4, 5, 6]
  ```

  - `+` -- `list = list1+list2`，将`list1`和`list2`拼接成新列表`list = list1.extend(list2)`

    ```python
    s = s1 + s2
    print(s)
    # OUTPUT:
    [1, 2, 3, 4, 5, 6]
    ```

  - `*`-- `list = list1*3`，将`list1`的内容复制三份并拼接成新列表`list = list1.extend(list1.extend(list1))`，支持自乘`*=`运算

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

  - `in`和`not in` -- `res = obj in list` 和 `res = obj not in list`, 判断元素`obj`是否在或着不在列表`list`中，返回`bool`值`res = True`或`res = False`

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

## 2.2 字符串str

### 1.字符串大小写转换

- `str.capitalize()`将字符串的第一个字符转换为大写，其他字母转换为小写，并返回转换后的字符串。

  ```python
  s = 'i Love You'
  s.capitalize()
  # OUTPUT:
  'I love you'
  ```

- `str.lower() `转换字符串中所有大写字符为小写，并返回转换后的字符串，无大写字母返回原字符串

  ```python
  s = 'I Love You'
  s.lower()
  # OUTPUT:
  'i love you'
  ```

- `str.upper() `转换字符串中的小写字母为大写，并返回转换后的字符串，无小写字母返回原字符串

  ```python
  s = 'I Love You'
  s.upper()
  # OUTPUT:
  'I LOVE YOU'
  ```

- `str.swapcase()` 将字符串中大写转换为小写，小写转换为大写，并返回转换后的字符串。

  ```python
  s = 'I Love You'
  s.swapcase()
  # OUTPUT:
  'i lOVE yOU'
  ```

### 2.检索字符串中的字符

- `str.count(str, beg=0, end=len(string)) `返回`str`在字符串里面出现的次数，如果`beg`或者`end`指定则返回指定范围$[begin, end-1)$内`str`出现的次数。

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

- `str.endswith(suffix, beg=0, end=len(string))` 检查字符串是否以指定子字符串 `suffix` 结束，如果是，返回 `True`，否则返回 `False`。如果 `beg` 和 `end` 指定值，则在指定范围$[begin, end-1)$内检查。

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

- `str.startswith(substr, beg=0,end=len(string)) `检查字符串是否以指定子字符串 `substr` 开头，如果是，返回 `True`，否则返回 `False`。如果 `beg` 和 `end` 指定值，则在指定范围$[begin, end-1)$内检查。

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

- `str.find(str, beg=0, end=len(string))` 检测 `str` 是否包含在字符串中，如果指定范围 `beg` 和 `end`，则检查是否包含在指定范围内，如果包含，返回开始的索引值，否则返回 -1。

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

- `str.rfind(str, beg=0,end=len(string))` 类似于 `find() `函数，不过是从右边开始查找。

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

- `str.isnumeric()` 如果字符串中只包含数字字符，则返回 True，否则返回 False。

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

### 3.用'空格'扩充字符串

- `str.ljust(width[, fillchar])`返回一个原字符串左对齐，并使用`fillchar`（默认空格）填充至长度width的新字符串。

  ```python
  s = 'I Love You'
  s.ljust(15)
  # OUTPUT:
  'I Love You     '
  
  s.ljust(15,'~')
  # OUTPUT:
  'I Love You~~~~~'
  ```

- `str.rjust(width[, fillchar])`返回一个原字符串右对齐，并使用`fillchar`（默认空格）填充至长度width的新字符串

  ```python
  s = 'I Love You'
  s.rjust(15)
  # OUTPUT:
  '     I Love You'
  
  s.rjust(15,'.')
  # OUTPUT:
  '.....I Love You'
  ```

### 4.字符串去头去尾操作

- `str.lstrip([chars])` 截掉字符串左边的空格或指定字符。

  ```python
  s = 'I Love You'
  s.lstrip('I ')
  # OUTPUT:
  'Love You'
  
  s.lstrip('Love')
  # OUTPUT:
  'I Love You'
  ```

- `str.rstrip([chars])` 删除字符串末尾的空格或指定字符。

  ```python
  s = 'I Love You'
  s.rstrip('u')
  # OUTPUT:
  'I Love Yo'
  
  s.rstrip('Love')
  # OUTPUT:
  'I Love You'
  ```

- `str.strip([chars])` 在字符串上执行`lstrip()`和`rstrip()`。

  ```python
  s = 'I Love You'
  s.strip('I')
  # OUTPUT:
  ' Love You'
  
  s.strip('You')
  # OUTPUT:
  'I Love '
  ```

### 5.分割字符串

- `str.partition(sub)` 找到子字符串sub，把字符串分为一个三元组`(pre_sub,sub,fol_sub)`，如果字符串中不包含sub则返回`('原字符串','','')`。

  ```python
  s = 'I Love You'
  s.partition('Love')
  # OUTPUT:
  ('I ', 'Love', ' You')
  
  s.partition('Him')
  # OUTPUT:
  ('I Love You', '', '')
  ```

- `str.rpartition(sub)`类似于`partition()`方法，不过是从右边开始查找。

- `str.split(str="", num)` 不带参数默认是以空格为分隔符切片字符串，如果`num`参数有设置，则仅分隔`num`次，返回切片后的子字符串拼接的列表。

  ```python
  s = 'I Love You'
  s.split(' ')
  # OUTPUT:
  ['I', 'Love', 'You']
  
  s.split(' ',1)
  # OUTPUT:
  ['I', 'Love You']
  ```

### 6.字符串替换操作

- `replace(old, new [, max])` 把 将字符串中的`old`替换成`new`，如果`max`指定，则替换不超过`max`次。

  ```python
  s = 'I Love You'
  s.replace('o', '0')
  # OUTPUT:
  'I L0ve Y0u'
  
  s.replace('o', '0', 1)
  # OUTPUT:
  'I L0ve You'
  ```

### 7.字符串操作符

- `str1+str2`可以将两个字符串`str1`和`str2`合并成一个字符串

  ```python
  s1 = 'Love'
  s2 = 'U'
  s = s1 + s2
  print(s)
  # OUTPUT:
  'LoveU'
  ```

  

### 8.字符串规范化

- 利用`format`方法实现字符串规范化`'... {key1:type1} ... {key2:type2} ...'.format(key1 = ch1, key2 = ch2)`

- 利用`%标识符`实现字符串规范化`'... %type1 ... %type2 ...'%(ch1, ch2)`

- 标识符含义：`<~>`表示自定义输入数值
  - `%d`：整数 转 字符
  
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
  
  - `%c`：ASCII码 转 字符
  
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
  
  - `%o`：整数 转 8进制 转 字符
  
  - `%x`：整数 转 16进制 转 字符
  
  - `%X`：整数 转 16进制 转 字符（字母大写）
  
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
  
  - `%.<k>f`： 保留`k`位小数 转 字符
  
    ```python
    '%.2f' % (11.4514)
    # OUTPUT:
    Out[9]: '11.45'
    ```
  
  - `%<m>.<k>f`：保留`k`位小数 转 字符 并将字符串右移`m`位用空格补全
  
    ```python
    '%8.2f' % (11.4514)
    # OUTPUT:
    '   11.45'
    ```
  
  - `%.<k>e`：保留`k`位小数的科学计数法形式 转 字符
  
    ```python
    '%.3e' % (114514)
    # OUTPUT:
    '1.145e+05'
    ```
  
  - `%<m>d`：整数转字符，并将字符串右移`m`位（`m`为负数则左移）
  
    ```python
    '%4d' % (12)
    # OUTPUT:
    '  12'
    '%-4d' % (12)
    # OUTPUT:
    '12  '
    ```
  
  - `%s`：直接填充字符串
  
  - `%r`：将字符串作为引用内容加入（即`'...'str'...'`）
  
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



### 9.字符类型判断与转化

- `ch.isupper()`判断字符`ch`是否为大写字母

- `ch.islower()`判断字符`ch`是否为小写字母

- `ch.isdigit()`判断字符`ch`是否为数字

- `ord(ch)`将字符`ch`转换为对应ASCII码

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

  

## 2.3 字典dict和默认字典defaultdict

### 1.创建字典

- `dict.fromkeys(seq[, value])` 用于创建一个新字典，以序列 `seq` 中元素做字典的键，`value` 为字典所有键对应的初始值。

  ```python
  seq = ['a', 'b', 'c']
  dict.fromkeys(seq,[1, 2, 3])
  # OUTPUT:
  {'a': [1, 2, 3], 'b': [1, 2, 3], 'c': [1, 2, 3]}
  ```

- `dict.setdefault(dict, key, default=None)`和`dict.get(dict, key, default=None)`, 如果键`key`不存在于字典中，将会添加键并将值设为默认值`default`。

  ```python
  dic = {'a': 1, 'b': 2, 'c': 3}
  dict.setdefault(dic,'d',6)
  dic['d']
  # OUTPUT:
  6
  ```

- `collections.defaultdict(type)`，限定字典中值的数据类型为`type`，若键`key`不存在，将对应`val`值设置为对应的默认值：

  ```python
  import collections
  ```

  1.`list`对应`[]`

  ```python
  dic = collections.defaultdict(list)
  dic['a']
  # OUTPUT:
  []
  ```
  
  2.`int`对应`0`
  
  ```python
  dic = collections.defaultdict(int)
  dic['a']
  # OUTPUT:
  0
  ```
  
  3.`str`对应`''`
  
  ```python
  dic = collections.defaultdict(str)
  dic['a']
  # OUTPUT:
  ''
  ```
  
  4.`set`对应`set()`
  
  ```python
  dic = collections.defaultdict(set)
  dic['a']
  # OUTPUT:
  set()
  ```

### 2.字典的索引

```python
dic = {'a': 1, 'b': 2, 'c': 3}
```

- 直接用`dict[key]`就能索引对应的值`val`。

  ```python
  dic['b']
  # OUTPUT:
  2
  ```

- `dict.keys()`返回一个可迭代对象，可以使用 `list()` 来转换为列表，列表为字典中的所有键。

  ```python
  dic.keys()
  # OUTPUT:
  dict_keys(['a', 'b', 'c'])
  
  list(dic.keys())
  # OUTPUT:
  ['a', 'b', 'c']
  ```

- `dict.values()`返回一个可迭代对象，可以使用 `list()` 来转换为列表，列表为字典中的所有值。

  ```python
  dic.values()
  # OUTPUT:
  dict_values([1, 2, 3])
  
  list(dic.values())
  # OUTPUT:
  [1, 2, 3]
  ```

- `key in dict` 用于判断键是否存在于字典中，如果键在字典 `dict `里返回`true`，否则返回`false`。而`not in`操作符刚好相反，如果键在字典 `dict` 里返回`false`，否则返回`true`。

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

### 3.字典的删除操作

```python
dic = {'a': 1, 'b': 2, 'c': 3}
```

- `dict.pop(key[,default])`删除字典给定键 `key` 所对应的值，返回值为被删除的值。`key` 值必须给出。若`key`不存在，则返回 `default` 值。

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

- `del dict[key]` 删除字典给定键 `key` 所对应的值。

  ```python
  del dic['b']
  dic
  # OUTPUT:
  {'a': 1, 'c': 3}
  ```

- `dict.popitem()`随机返回并删除字典中的一对键和值，如果字典已经为空，却调用了此方法，就报出`KeyError`异常。

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

- `dict.clear()`用于删除字典内所有元素。

  ```python
  dic.clear()
  dic
  # OUTPUT:
  {}
  ```

### 4.字典的拓展

- `dict.update(dict2)`把字典参数 `dict2` 的` key:value`对 更新到字典 `dict` 里。

  ```python
  dic = {'a': 1, 'b': 2, 'c': 3}
  dic2 = {'d': 4, 'e': 5}
  dic.update(dic2)
  dic
  # OUTPUT:
  {'a': 1, 'b': 2, 'c': 3, 'd': 4, 'e': 5}
  ```

  

## 2.4 集合set

### 1.集合的创建

- `set()`创建空集合
- `set={a,b,c,...}`创建含元素的集合，不能使用`{}`，会默认创建字典

### 2.集合添加元素

- `set.add(element)`将元素`element`添加到集合中，原集合中存在的元素不重复添加

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

- `set.update(set2)`将`set2`中的元素添加到集合中，原集合中存在的元素不重复添加

  ```python
  s = {1,2,3}
  s2 = {3,4,5}
  s.update(s2)
  print(s)
  # OUTPUT:
  {1, 2, 3, 4, 5}
  ```

### 3.集合删除元素

- `set.remove(item) `用于移除集合中的指定元素。如果元素不存在，则会报错。

  ```python
  s = {1,2,3}
  s.remove(2)
  print(s)
  # OUTPUT:
  {1, 3}
  ```

- `set.discard(value)` 用于移除指定的集合元素。`remove()` 方法在移除一个不存在的元素时会发生错误，而 `discard()` 方法不会。

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

- `set.pop()` 用于随机移除一个元素。

  ```python
  s = {1,2,3}
  s.pop()
  print(s)
  # OUTPUT:
  {2, 3}
  ```

### 4.数学集合运算

```python
set1 = {1, 2, 3, 4}
set2 = {2, 4, 6, 8}
```

- `set = set1.intersection(set2)`或`set = set1 & set2`  返回两个集合的交集。

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

- `set1.intersection_update(set2)` 交集，在原始的集合`set1`上移除不重叠的元素。

- `set = set1.union(set2)` 或`set = set1 | set2` 返回两个集合的并集。

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

- `set = set1.difference(set2)` 或`set = set1 - set2` 返回集合的差集。

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

- `set1.difference_update(set2)` 集合的差集，直接在原来的集合`set1`中移除元素，没有返回值。

- `set1.issuperset(set2)`或`set1 >= set2` 用于判断集合是不是包含其他集合，如果是则返回 `True`，否则返回 `False`。

  ```python
  set1.issuperset(set2)
  # OUTPUT:
  False
  
  set1 >= set2
  # OUTPUT:
  False
  ```

- `set1.isdisjoint(set2)` 用于判断两个集合是不是不相交，如果是返回` True`，否则返回` False`。

  ```python
  set1.isdisjoint(set2)
  # OUTPUT:
  False
  ```

## 2.5 元组tuple

- 创建方式：`tuple=(a,b,[c,d],...)`

- 索引方式`index=start:stop:step`或`index=num`
  - `start`为起始索引，`stop`为结束索引，`step`为索引步长
  - 索引序列为：{start, start**+step**, start**+2*step**, ..., start**+n\*step**, **stop-1** }
  - 索引序列为{0, 1, 2, ..., 列表长度-1}或{-列表长度, ..., -2, -1}
  - `:`表示索引所有元素，`tuple[a:]`表示从下标a索引到末尾
  
- 元组常用操作符

  ```pythong 
  tup1 = (1, 2, [3, 4])
  tup2 = ({'a':1, 'b':2, 'c':3}, {4, 5, 6}, 2, [3, 4])
  ```

  - `+` -- `tuple = tuple1+tuple2`，将`tuple1`和`tuple2`拼接成新元组`tuple`

    ```python
    tup = tup1 + tup2
    print(tup)
    # OUTPUT:
    (1, 2, [3, 4], {'a': 1, 'b': 2, 'c': 3}, {4, 5, 6}, 2, [3, 4])
    ```

  - `*`-- `tuple = tuple1*3`，将`tuple1`的内容复制三份并拼接成新元组`tuple`，支持自乘`*=`运算

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

  - `in`和`not in` -- `res = obj in tuple` 和 `res = obj not in tuple`, 判断元素`obj`是否在或着不在元组`tuple`中，返回`bool`值`res = True`或`res = False`

- 元组大小和内容都不可更改，只存在查询操作：
  
  ```python
  tup = (1, 2, [3, 4], {'a': 1, 'b': 2, 'c': 3}, {4, 5, 6}, 2, [3, 4])
  ```
  
  - `num=tuple.count(obj)`统计元组`tuple`中`obj`元素的数目`num`
  
    ```python
    num = tup.count([3,4])
    print(tup)
    # OUTPUT:
    2
    ```
  
  - `ind=tuple.index(obj)`索引元素`obj`在元组`tuple`中的**从左往右首次出现**的下标`ind`
  
    ```python
    ind = tup.index([3,4])
    print(ind)
    # OUTPUT:
    2
    ```
  
- 解压元组：**按元组结构定义变量**并将元组元素赋值给对应变量

  ```python
  tup = (1, 2, [3, 4], {'a': 1, 'b': 2, 'c': 3}, {4, 5, 6})
  (a,b,[c,d],dic,s) = tup
  ```

## 2.6 通用操作

- `len(s)`返回对象（字符、列表、元组等）长度或元素个数。

- `sorted(iterable, key=None, reverse=False)`对所有可迭代的对象进行排序操作。

  `iterable` -- 可迭代对象。
  `key` -- 主要是用来进行比较的元素，只有一个参数，具体的函数的参数就是取自于可迭代对象中，指定可迭代对象中的一个元素来进行排序。常用`lambda x: f(x)`语法表达，表示排序对象为`x`，排序依据为`f(x)`
  `reverse` -- 排序规则，`reverse = True` 降序 ， `reverse = False` 升序（默认）。

  ```python
  dic = {'a':2, 'b':5, 'c':1}
  sorted(dic,key = lambda x: dic[x])
  # OUTPUT:
  ['c', 'a', 'b']
  ```

- `reversed(seq)`函数返回一个反转的迭代器，`seq` -- 要转换的序列，可以是 tuple, str, list 或 range。

- `enumerate(sequence, [start=0])`形成将序列`sequence`的内容和对应下标组成元组`(i, sequence[i])`

  ```python
  s = ['a', 'b', 'c']
  for i,e in enumerate(s):
      print(i,e)
  # OUTPUT:    
  0 a
  1 b
  2 c
  ```

- `zip(iter1 [,iter2 [...]])`将多个序列对应的元素打包成元组，返回长度与较短序列长度一致，可通过`*zip(archive)`进行解压

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

  
