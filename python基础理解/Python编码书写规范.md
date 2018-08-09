#### Python编码书写规范

```Python
​```
 美观
可读性
可维护性
健壮性 
​```

import os
import sys	# 自己的库  （每个独立的模块都需要断行）

from django.conf import settings  # 第三方库

from user.models import User  # 自己写的库

MOD_XX_YY = 0xffffffff   # 全局变量尽量都写成大写   运算符前后各保留一个空格


def foo(a, b=123):    # 顶级的函数和类 空两行 参数‘=’不要空格
    '''文档：功能（相当于函数内部的代码）'''
    c = {'x': 111, 'y': 222}
    d = [1, 3, 4]
    return a, b, c

def bar(x):
    '''sasd'''
    if x % 2 == 0:
    return True  # 换行尽量用4个空格，避免使用Tab


class ClassName(object):
    '''函数文档'''
    def __init__(self, arg):
        super(ClassName, self).__init__()
        self.arg = arg
        
    def xxx(self):
        pass
```

