# Bert学习python

## 1. copy

列表里面的列表. 其实,在内存里,列表里只是存储了自列表的内存地址,子列表在内存里是单独存储的.



```python

import copy
list = ['beijing','tianjin','hebei',['neimeng','xinjiang'],'wuhan','shandong']
list_copy = copy.copy(list)
list[3][0] = 'taiwan'
print(list)
print(list_copy)

结果显示：
['beijing', 'tianjin', 'hebei', ['taiwan', 'xinjiang'], 'wuhan', 'shandong']
['beijing', 'tianjin', 'hebei', ['taiwan', 'xinjiang'], 'wuhan', 'shandong']

```

```python
import copy
list = ['beijing','tianjin','hebei',['neimeng','xinjiang'],'wuhan','shandong']
list_copy = copy.deepcopy(list)
list[3][0] = 'taiwan'
print(list)
print(list_copy)

结果显示：
['beijing', 'tianjin', 'hebei', ['taiwan', 'xinjiang'], 'wuhan', 'shandong']
['beijing', 'tianjin', 'hebei', ['neimeng', 'xinjiang'], 'wuhan', 'shandong']
```

使用深度复制,就不会改变子列表的值了,因为deepcopy将子列表也复制了一份.

注意:deepcopy()方法,如果数据很大,完全复制就是存储两份数据,占用内存,慎用!

但如果是下面这种情况,将原来的列表重新赋值(而不是改变部分值),那么将不影响复制变量的值.

```python
import copy

list_1 = ['name', ['games', ['username', 'passwd']]]
list_2 = copy.copy(list_1)
list_1 = ["s"]
print("list1:  ", list_1)
print("list2:  ", list_2)

list1:   ['s']
list2:   ['name', ['games', ['username', 'passwd']]]

Process finished with exit code 0
```

