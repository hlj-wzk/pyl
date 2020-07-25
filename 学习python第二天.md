# 学习python第二天
## 条件语句
###  1. if语句
```
 if expression:   
    expr_true_suite
```
```
 if expression:    
    expr_true_suite 
  else    
    expr_false_suite
```
单个的语句中的条件表达式可用`and` `or` `not`进行多重判断
```
if expression1:    
    expr1_true_suite 
  elif expression2:    
    expr2_true_suite    
  .    
  . 
  elif expressionN:    
    exprN_true_suite 
  else:    
    expr_false_suite
```
elif为elseif
## 循环语句
###  1. while循环
···
while 布尔表达式:
    代码块
```
while 布尔表达式:
    代码块
else:
    代码块
```
当while循环正常执行完的情况下，执行else输出，如果while循环中执行了跳出循环的语句，比如 break，将不执行else代码块的内容
###  2. for循环
`for`循环是迭代循环，在Python中相当于一个通用的序列迭代器，可以遍历任何有序序列，如str、list、tuple等，也可以遍历任何可迭代对象，如`dict`
```
for 迭代变量 in 可迭代对象:
    代码块
```

```
for 迭代变量 in 可迭代对象:
    代码块
else:
    代码块
```
当for循环正常执行完的情况下，执行else输出，如果for循环中执行了跳出循环的语句，比如 break，将不执行else代码块的内容，与while - else语句一样。
###  3. range函数
`range([start,] stop[, step=1])`

`range` 这个BIF（Built-in functions）有三个参数，其中用中括号括起来的两个表示这两个参数是可选的，作用是生成一个从start参数的值开始到stop参数的值结束的数字序列，该序列包含start的值但不包含stop的值。
###  4.  enumerate()函数
`enumerate(sequence, [start=0])`
* sequence为可支持迭代的对象，
* start为下标起始位
####  与for联用
```
languages = ['Python', 'R', 'Matlab', 'C++']
for language in languages:
    print('I love', language)
print('Done!')

'''
I love Python
I love R
I love Matlab
I love C++
Done!
'''

for i, language in enumerate(languages, 2):
    print(i, 'I love', language)
print('Done!')

'''
2 I love Python
3 I love R
4 I love Matlab
5 I love C++
Done!
```
###  5. assert 关键词
* 当关键词条件FALSE时，程序自动崩溃并抛出AssertionError的异常。
###  6. break语句
```python
import random
secret = random.randint(1, 10) #[1,10]之间的随机数

while True:
    temp = input("不妨猜一下小哥哥现在心里想的是那个数字：")
    guess = int(temp)
    if guess > secret:
        print("大了，大了")
    else:
        if guess == secret:
            print("你这样懂小哥哥的心思啊？")
            print("哼，猜对也没有奖励！")
            break
        else:
            print("小了，小了")
print("游戏结束，不玩儿啦！")
```
* break **只能在while和for循环中使用**

###  7. continue 语句
```python
for i in range(10):
    if i % 2 != 0:
        print(i)
        continue
    i += 2
    print(i)

# 2
# 1
# 4
# 3
# 6
# 5
# 8
# 7
# 10
# 9
```
* 到continue直接结束本次循环
###  8. pass 语句
pass是空语句，不做任何操作，只起到占位的作用，其作用是为了保持程序结构的完整性。尽管pass语句不做任何操作，但如果暂时不确定要在一个位置放上什么样的代码，可以先放置一个pass语句，让代码可以正常运行。

###  9. 推导式
* 列表中 
>列表中的元素i可以同过for循环来完成，`for`中的 i 可以是一个变量，也可以是两个变量。可为 i 与i 的一元运算 也可以是两个不同变量，达到(a,b)的效果
>可迭代对象 可以是任意一个可迭代的 数值，函数，变量。


##  练习题
1. 编写一个Python程序来查找那些既可以被7整除又可以被5整除的数字，介于1500和2700之间
```python
# _*_  coding:utf-8 _*_
for i in range (1500,2700):
  if i%5==0 and i%7==0:
    print(i)
print('以上就是所有在500到2700之间既可以被5整除也可以被7整除的数')
```

2.龟兔赛跑游戏
