# 代码规范

### Python 代码规范

* Pep8 代码应当遵循Pep8规范
* Pylint 代码质量分析

[Google Coding Style](
https://google-styleguide.googlecode.com/svn/trunk/pyguide.html)


[High Quality Python Coding Guide](
http://docs.python-guide.org/en/latest/writing/style/)


推荐阅读 **代码整洁之道 Clean Code **:

[百度百科介绍](http://baike.baidu.com/view/2708403.htm?fr=aladdin)

Tips:
----------
如何分析代码质量:

安装Python packages:

    $ pip install pep8
    $ pip install pylint

Pep8 code analysis:

    $ pep8 --show-source --show-pep8 a.py
    testsuite/E40.py:2:10: E401 multiple imports on one line
    import os, sys
         ^
    Imports should usually be on separate lines.

    Okay: import os\nimport sys
    E401: import sys, os

Pylint code analysis:

创建一个simple.py 文件。

```python
1  #!/usr/bin/env python
2
3  import string
4
5  shift = 3
6  choice = raw_input("would you like to encode or decode?")
7  word = (raw_input("Please enter text"))
8  letters = string.ascii_letters + string.punctuation + string.digits
9  encoded = ''
10  if choice == "encode":
11      for letter in word:
12          if letter == ' ':
13              encoded = encoded + ' '
14          else:
15              x = letters.index(letter) + shift
16              encoded=encoded + letters[x]
17  if choice == "decode":
18      for letter in word:
19          if letter == ' ':
20              encoded = encoded + ' '
21          else:
22              x = letters.index(letter) - shift
23              encoded = encoded + letters[x]
24
25  print encoded
```

    $ pylint simple.py

    No config file found, using default configuration
    ************* Module simplecaeser
    C:  1, 0: Missing module docstring (missing-docstring)
    W:  3, 0: Uses of a deprecated module 'string' (deprecated-module)
    C:  5, 0: Invalid constant name "shift" (invalid-name)
    C:  6, 0: Invalid constant name "choice" (invalid-name)
    C:  7, 0: Invalid constant name "word" (invalid-name)
    C:  8, 0: Invalid constant name "letters" (invalid-name)
    C:  9, 0: Invalid constant name "encoded" (invalid-name)
    C: 16,12: Operator not preceded by a space
            encoded=encoded + letters[x]
                   ^ (no-space-before-operator)

对于高质量的代码的标准是Pylint 评分标准需要大于8.6。



### 前端代码规范 HTML,CSS



### Javascript 规范



