# 学习python第四天
##  列表List
###  定义
列表是没有固定大小的有序集合，可保存任意类型的对象
形如`x=[4,'b']`
###  列表的创建
* 列表由 **[]** 括起来，各元素之间用 **,** 间隔
* 用`range()`创建列表
```python
x = list(range(10))      #list()作用是改变数据类型为<class 'list'>
print(x, type(x))
# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] <class 'list'>

x = list(range(1, 11, 2))
print(x, type(x))
# [1, 3, 5, 7, 9] <class 'list'>

x = list(range(10, 1, -2))   #每次减2
print(x, type(x))
# [10, 8, 6, 4, 2] <class 'list'>

x = [i for i in range(100) if (i % 2) != 0 and (i % 3) == 0]
print(x, type(x))

# [3, 9, 15, 21, 27, 33, 39, 45, 51, 57, 63, 69, 75, 81, 87, 93, 99] <class 'list'>
```
* 推导式创建
   * 创建一个1*n的列表
    ```python
    x=[3]*n  #n可以为任意正整数
    
    x=[3 for i range(n)] #n为任意整数
    ```
    * 创建一个n*m的二维数组
    ```python
    x=[[1,2,3],[4,5,6]]   #一个2*3的数组
    print(x, type(x))
    # [[1, 2, 3], [4, 5, 6]] <class 'list'> # 每一个中括号中的元素为一行，一行视为最外层[]的一个元素，每行之间用,隔开
    for i in x:
    print(i, type(i))
    # [1, 2, 3] <class 'list'>
    # [4, 5, 6] <class 'list'>
    ```
    *快速创建一个所有元素相同的多行多列数组
    ```python
    #方法一
    x=[[0 for i in range(5)] for j in range(6)]   #创建6*5的数组
    print(x,type(x))
    # [[0, 0, 0, 0, 0], [0, 0, 0, 0, 0], [0, 0, 0, 0, 0], [0, 0, 0, 0, 0], [0, 0, 0, 0, 0], [0, 0, 0, 0, 0]] <class 'list'>
    
    #方法二
    x=[[0]*5 for j in range(6)]   #创建6*5的数组
    print(x,type(x))
    # [[0, 0, 0, 0, 0], [0, 0, 0, 0, 0], [0, 0, 0, 0, 0], [0, 0, 0, 0, 0], [0, 0, 0, 0, 0], [0, 0, 0, 0, 0]] <class 'list'> 
    x[1][3]=1  # 改变下角标为1，3的元素数值
    print(x)
    # [[0, 0, 0, 0, 0], [0, 0, 0, 1, 0], [0, 0, 0, 0, 0], [0, 0, 0, 0, 0], [0, 0, 0, 0, 0], [0, 0, 0, 0, 0]]
    ```
    列表中保存的是对象的指针，所以，如果该指针所指的内存中的数值发生改变则类表中的数值也应有相应的改变。
    ```python
    x = [[0] * 3] * 4     
    print(x, type(x))
    # [[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]] <class 'list'>

    x[0][0] = 1         #这里改变了数组[0]*3中的值发生了改变，而x指向了[[0]*3]所以，在x的每一行中，都会产生
    print(x, type(x))
    # [[1, 0, 0], [1, 0, 0], [1, 0, 0], [1, 0, 0]] <class 'list'>

    a = [0] * 3
    x = [a] * 4
    print(x, type(x))
    # [[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]] <class 'list'>

    x[0][0] = 1
    print(x, type(x))
    # [[1, 0, 0], [1, 0, 0], [1, 0, 0], [1, 0, 0]] <class 'list'>
    ```
    **与上一个同理，此处x[0]与a地址相同，指向同一内存区域，所以在此区内的值发生了改变，a和x应一起改变。在前两天我们学的`is`语句**
    **恰好可以证明此问题**
    ```python
    a = [0] * 3
    x = [a] * 4
    p= a is x[0]    #is语句用来判断两个变量地址是否一直，若一致返回True 反之False
    print(p)
    # True
    ```
    * 创建一个空列表
    ```python
    empty = []
    print(empty, type(empty))  # [] <class 'list'>
    ```
 ***
 列表不像元组，列表内容可更改 (mutable)，因此附加 (append, extend)、插入 (insert)、删除 (remove, pop) 这些操作都可以用在它身上。
 ###  向列表中添加元素
 * list.append(obj) 在列表末尾添加新的对象，只接受一个参数，参数可以是任何数据类型，被追加的元素在 list 中保持着原结构类型。
 ```pyython
 x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
x.append('Thursday')
print(x)  
# ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Thursday']
print(len(x))  # 6


x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
x.append(['Thursday', 'Sunday'])
print(x)  
# ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', ['Thursday', 'Sunday']]
print(len(x))  # 6
```
* list.extend(seq) 在列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表）
```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
x.extend(['Thursday', 'Sunday'])
print(x)  
# ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Thursday', 'Sunday']
print(len(x))  # 7
```
* list.insert(index, obj) 在编号 index 位置插入 obj 此处的index最大值应该为列表元素个数与插入个数的和。
```python
x=[0,1,2,3,4]   #x原本下角标最多到4
x.insert(5,8)   #因为加入了一个元素所以最多可以到5
print(x)
# [0, 1, 2, 3, 4, 8]
```
### 删除列表中的元素
* list.remove(obj)删除列表中第一个符合obj的元素
* list.pop([index=-1])删除列表中的一个元素（默认最后一个（-1））并返回该值
* del可以删除一个或多个元素
```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
del x[2]
print(x)
# ['Monday', 'Tuesday', 'Thursday', 'Friday']

x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
del x[0:2]
print(x)
# ['Wednesday', 'Thursday', 'Friday']
```
如果你要从列表中删除一个元素，且不再以任何方式使用它，就使用del语句；如果你要在删除元素后还能继续使用它，就使用方法pop()。
###  获取列表中的元素
通过元素的索引值，从列表获取单个元素，注意，列表索引值是从0开始的。
通过将索引指定为-1，可让Python返回最后一个列表元素，索引 -2 返回倒数第二个列表元素，以此类推。
* 索引单一值
```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
print(x[1])
print(x[-1])
# Tuesday
# Friday
```
* 索引多个值
```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
print(x[:2])
print(x[2:])
print(x[1:3])
print(x[0:4:2])

# ['Monday', 'Tuesday']
# ['Wednesday', 'Thursday', 'Friday']
# ['Tuesday', 'Wednesday']
# ['Monday', 'Wednesday']
```
* 拷贝':'
```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
y=x[:]
print(y)
# ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
```
>思考：什么是浅拷贝，什么是深拷贝？他们的区别是什么？
###  列表的常用操作符
等号操作符：==   # 相等返回True，不相等返回False
连接操作符 +     # extend
重复操作符 * 
成员关系操作符 in、not in   # 返回True，False
前面三种方法（append, extend, insert）可对列表增加元素，它们没有返回值，是直接修改了原数据对象。 而将两个list相加，需要创建新的 list 对象，从而需要消耗额外的内存，特别是当 list 较大时，尽量不要使用 “+” 来添加list。
###  列表的其它方法
list.count(obj) 统计某个元素在列表中出现的次数
```python
list1 = [123, 456] * 3
print(list1)  # [123, 456, 123, 456, 123, 456]
num = list1.count(123)
print(num)  # 3
```

list.index(x[, start[, end]]) 从列表中找出某个值第一个匹配项的索引位置
```python
ist1 = [123, 456] * 5
print(list1.index(123))  # 0
print(list1.index(123, 1))  # 2
print(list1.index(123, 3, 7))  # 4
```

list.reverse() 反向列表中元素
```python
x = [123, 456, 789]
x.reverse()
print(x)  # [789, 456, 123]
```

list.sort(key=None, reverse=False) 对原列表进行排序。

key -- 主要是用来进行比较的元素，只有一个参数，具体的函数的参数就是取自于可迭代对象中，指定可迭代对象中的一个元素来进行排序。
reverse -- 排序规则，reverse = True 降序， reverse = False 升序（默认）。
该方法没有返回值，但是会对列表的对象进行排序。
```python
x = [123, 456, 789, 213]
x.sort()
print(x)
# [123, 213, 456, 789]

x.sort(reverse=True)
print(x)
# [789, 456, 213, 123]


# 获取列表的第二个元素
def takeSecond(elem):
    return elem[1]


x = [(2, 2), (3, 4), (4, 1), (1, 3)]
x.sort(key=takeSecond)
print(x)
# [(4, 1), (2, 2), (1, 3), (3, 4)]

x.sort(key=lambda a: a[0])
print(x)
# [(1, 3), (2, 2), (3, 4), (4, 1)]
```
### 练习题
1、列表操作练习

列表lst 内容如下

lst = [2, 5, 6, 7, 8, 9, 2, 9, 9]

请写程序完成下列操作：

在列表的末尾增加元素15
在列表的中间位置插入元素20
将列表[2, 5, 6]合并到lst中
移除列表中索引为3的元素
翻转列表里的所有元素
对列表里的元素进行排序，从小到大一次，从大到小一次
```python
# _*_  coding:utf-8 _*_
#在列表的末尾增加元素15
lst = [2, 5, 6, 7, 8, 9, 2, 9, 9]
lst.append(15)
print(lst)
#在列表的中间位置插入元素20
lst.insert(5,20)
print(lst)
#将列表[2, 5, 6]合并到lst中
lst.extend([2,5,6])
print(lst)
#移除列表中索引为3的元素
del lst[3]
print(lst)
#翻转列表里的所有元素
lst.reverse()
print(lst)
#对列表里的元素进行排序，从小到大一次，从大到小一次
lst.sort()
print(lst)

lst.sort(reverse=True)
print(lst)


# [2, 5, 6, 7, 8, 9, 2, 9, 9, 15]
# [2, 5, 6, 7, 8, 20, 9, 2, 9, 9, 15]
# [2, 5, 6, 7, 8, 20, 9, 2, 9, 9, 15, 2, 5, 6]
# [2, 5, 6, 8, 20, 9, 2, 9, 9, 15, 2, 5, 6]
# [6, 5, 2, 15, 9, 9, 2, 9, 20, 8, 6, 5, 2]
# [2, 2, 2, 5, 5, 6, 6, 8, 9, 9, 9, 15, 20]
# [20, 15, 9, 9, 9, 8, 6, 6, 5, 5, 2, 2, 2]
```
