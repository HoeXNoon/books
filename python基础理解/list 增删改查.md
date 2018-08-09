####  list 增删改查

```python
l = [1, 2, 3, 5]
l[0] = 10
print(l)

#增删改查
#追加元素，加到最后
l.append(100)
print(l)
#列表中追加序列
l.extend([3, 6, 10])
print(l)

#在指定索引处添加元素
l.insert(1, 1000)
print(l)

# 删除指定的元素
l.remove(1000)
print(l)
#l.remove(120)#如果要删除的元素不存在，提示异常

# 删除最后的元素,返回删除的元素的值
a = l.pop()
print(l)
print('a=', a)

# 根据指定的索引删除元素，参数表示索引值
print(l.pop(4))
print(l)

#删除列表中的元素
del l[0]
print(l)

#清空列表
#l.clear()
#print(l)

#获取指定元素的个数
c = l.count(6)
print(c)

#列表中元素逆序
l.reverse()
print(l)

print(l[::-1])#生成一个新的列表
print(l)

#排序，默认升序
# l.sort()
# print(l)

l.sort(reverse=True)
print(l)


l = ['hello', 'world', 'lisi', 'Tom', 'Jerry']
print(l.sort())#None
print(l)
```

#### tuple 元组的内容不能修改，不可变

```python
tuple.index()
tuple.count()
del tuple
```

