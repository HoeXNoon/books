#### set 集合

```python
#集合：无序，值唯一
s = {10, 1, 2, 4, 4}
print(s)

#集合中元素不能通过下标访问，因为无序

#集合中的内容可变
#添加元素
s.add(34)
print(s)

#将序列中的单个元素添加到原来的集合中
s.update('abc')
print(s)

#删除元素
s.remove(34)
print(s)

s1 = {2, 10, 13, 'abc', 'dd'}
#合集，将多个集合合并为一个集合
s2 = s | s1
print(s2)

#交集,获取两个集合中相同的元素
s3 = s & s1
print(s3)

#差集，从s中删除，s和s1中都有的元素
s4 = s - s1
print(s4)
```

