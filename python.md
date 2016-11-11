最後更新： 2016-11-07 

**python3-pip - alternative Python package installer - Python 3 version of the package**
**python3-dev - header files and a static library for Python (default)**

```console
shell> apt-get install python3-pip python3-dev
shell> pip install --upgrade pip
shell> pip3 install --upgrade pip
```
---

    
```python 
print "Test Message"
```

```python
# coding=utf_8
print "測試訊息"
```
```python
# -*- coding: utf_8 -*-
print "測試訊息"
```

```python
print 2 + 2
print 50 - 5*6
print (50 - 5*6) / 4
print 8 / 5
print 5 * 3 + 2
print 17 % 3
```

```python
squares = [1, 4, 9, 16, 25]
print squares
print squares[0]
print squares[-1]
```

```python
import random
import string
print random.sample(string.ascii_letters, 8)
print "".join(random.sample(string.ascii_letters, 8))
```

---

```console
shell> python -m timeit '"-".join(str(n) for n in range(100))'
```
### :books: 參考網站：
- https://docs.python.org/2/library/timeit.html

---

```console
shell> python -c "import random,string,crypt; print crypt.crypt('', '\$1\$%s\$' %  ''.join(random.sample(string.ascii_letters, 8)))"
shell> python -c "import random,string,crypt; print crypt.crypt('', '\$5\$%s\$' %  ''.join(random.sample(string.ascii_letters, 8)))"
shell> python -c "import random,string,crypt; print crypt.crypt('', '\$6\$%s\$' %  ''.join(random.sample(string.ascii_letters, 8)))"
``` 

### :books: 參考網站：
- https://docs.python.org/3/library/string.html
- https://docs.python.org/3/library/random.html
- https://docs.python.org/3/library/crypt.html

---
### :books: 參考網站：

- https://docs.python.org/release/3.4.2/tutorial/introduction.html
- https://www.python.org/dev/peps/pep-0263/
