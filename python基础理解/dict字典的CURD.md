**dict字典的CURD**

```python
d = {'name':'Tom', 'age':10}
#默认遍历键的值
for k in d:
	print(k)-----

for k in d.keys():
	print(k)

for v in d.values():
	print(v)

for k, v in d.items():
	print(k, v)

#字典中内容可变
#根据key值获取value的值

print(d['name'])
#print(d['aaa']) #如果key不存在，异常

#根据key获取对应的value
print(d.get('age'))
print(d.get('aaa'))# 

#如果key值存在，相当于修改元素的值；如果不存在，相当于添加键值对
d['qq'] = '1212121'
print(d)
d['age'] = 13
print(d)

#删除元素
del d['qq']
print(d)

#清空键值对
d.clear()
print(d)

#将字符串中单词和单词出现的次数保存到字典中

s = 'renge is a good man renge is a handsome man'

#根据空格拆分
l = s.split(' ')
print(l)
#内容为空的字典
numDic = {}
for item in l:
	ret = numDic.get(item)
	#如果key值不存在，添加到字典中，值设为1；如果存在，加1
	if ret == None:
		numDic[item] = 1
	else:
		numDic[item] += 1

print(numDic)

d = {'a':1}
d = dict(a = 1)
两种字典表示方法
```

**创建字典的方法**

```python
1.  d = {key : value for (key,value) in iterable}
2.  dict = {"name":"lily","age":"30"}
3.  #工厂方法
 (1)items = [('name','lily'),('age','30')]
  	dict2 = dict(items)
 (2)dict1 = dict((['name','lily'],['age','30']))
4.  # fromkeys()方法
    dict1 = {}.fromkeys(('x','y'),-1) # {'x': -1, 'y': -1}
  
```

**字典去重**

```Python
# list去重
list(set(l))

#字典去重
l1 = ['b','c','d','b','c','c']
l2 = {}.fromkeys(l1).keys()
print(l2)

# 用字典并保持顺序
l1 = ['b','c','d','b','c','c']
l2 = list(set(l1))
l2.sort(key = l1.index)
print(l2)

# 用字典先排序后删除
l1 = ['b','d','d','b','c','c']
l1.sort()
l2 = []
[l2.append(i) for i in l1 if not i in l2]
print(l2)
```



**字典合并**

```python
1. # 使用Counter内置函数
from collections import Counter
x = {'apple' : 1, 'banana' : 2}
y = {'banana' : 10, 'pear' : 11}
X,Y = Counter(x),Counter(y)
z = dict(X + Y)
print(z)   ### {'apple': 1, 'banana': 12, 'pear': 11}

2. 
x = {'apple' : 1, 'banana' : 2}
y = {'banana' : 10, 'pear' : 11}
dict1 = dict(x,**y)  # ==》
print(dict1)   ### {'apple': 1, 'banana': 10, 'pear': 11}

# dict1 = x.copy()  ### {'apple': 1, 'banana': 10, 'pear': 11}
# dict1.update(y)
# print(dict1)

# dict1 = dict(x)  ### {'apple': 1, 'banana': 10, 'pear': 11}
# dict1.update(y)
# print(dict1)

```

