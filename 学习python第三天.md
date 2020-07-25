# 学习python第三天
***
##  异常处理
###  1. Python标准异常总结
* BaseExpection
* Expection
* StandardError
* ArithmeticError
* FloatingPointError
* OverflowError
* ZeroDivisionError
* AssertionError
* AttributeError
* EnvironmentError
* IOError
* OSError
* WindowsError
* ImportError
* KeyboardInterrupt
* LookupError
* IndexError
* KeyError
* MemoryError
* NameError
* UnboundLocalError
* ReferenceError
* RuntimeError
* NotImplementedError
* SyntaxError
* IndentationError
* TabError
* SystemError
* TypeError
* ValueError
* UnicodeError
* UnicodeDecodeError
* UnicodeEncodeError
* UnicodeTranslateError
> python中异常的类关系

![expection的层次（从上到下）](https://camo.githubusercontent.com/e9b48743c3300f4d9a3ad201246277b2bc5245e1/68747470733a2f2f696d672d626c6f672e6373646e696d672e636e2f32303230303731303133313430343534382e706e67)
***
##  2. try语句
###  try-expect
```
try:
    检测范围
except Exception[as reason]:
    出现异常后的处理代码
```
try和expect之间的语句为try的子句，也就是检测对象，当子句中没有异常发生时子句循环之后结束，跳过except。
当子句中有异常出现时，异常语句后的内容被忽略：
  * 若异常与Expect匹配，则执行expect后的语句，然后结束。
  * 若抛出的异常没有与之匹配的Expect，则异常传回try。
`as reason`为异常原因，`reason`可设一个变量来储存，并打印(str(resason))。

一个try可以有多个expect语句，针对多种异常，但只有一个分支会被执行
> 使用多个代码块时，子句中抛出的异常，可被该异常或该异常的基类所捕捉，所以在expect编写时应注意排版，使子类在基类上方，让异常捕捉更准确。
> 若expect后没有任何异常类型，则该语句可以捕捉任何一种类型的异常，但这不是一个很好的方式，因为我们不能准确的识别异常类型。
一个expect也可以做到同时处理多个异常，将这些异常放在一个括号里成为元组。
```python
try:
    s = 1 + '1'
    int("abc")                  #在此处抛出异常，try子句停止运行
    f = open('test.txt')        #若删除第一句，则异常在此处抛出，异常信息变为"  invalid literal for int() with base 10: 'abc'  "
    print(f.read())             #此处同理
    f.close()
except (OSError, TypeError, ValueError) as error:
    print('出错了！\n原因是：' + str(error))

# 出错了！
# 原因是：unsupported operand type(s) for +: 'int' and 'str'
```
###  try-except-finally and try-except-else
#### finally 
不管try子句里面有没有发生异常，finally子句都会执行。
如果一个异常在try子句里被抛出，而又没有任何的except把它截住，那么这个异常会在finally子句执行后被抛出，在finally语句执行后，会打印未被except拦截的异常
***
#### else
* 当try没有异常发生时，else后的语句会被执行。
* 需要注意的是，`else`语句必须以`expect` **存在为前提**，若在没有`expect`的try语句中使用`else`会引发**语法错误**
##  3. raise
python中使用`raise`来手动抛出一个异常
```python
try:
    raise NameError('HiThere')
except NameError:
    print('An exception flew by!')
    
# An exception flew by!
```
raise 语句的基本语法格式为： ·raise [exceptionName [(reason)]]`
其中，用 [] 括起来的为可选参数，其作用是指定抛出的异常名称，以及异常信息的相关描述。如果可选参数全部省略，则 raise 会把当前错误原样抛出(默认引发 RuntimeError 异常)；如果仅省略 (reason)，则在抛出异常时，将不附带任何的异常描述信息。
***

##  猜数字游戏
电脑产生一个零到100之间的随机数字，然后让用户来猜，如果用户猜的数字比这个数字大，提示太大，否则提示太小，当用户正好猜中电脑会提示，"恭喜你猜到了这个数是......"。在用户每次猜测之前程序会输出用户是第几次猜测，如果用户输入的根本不是一个数字，程序会告诉用户"输入无效"。

(尝试使用try catch异常处理结构对输入情况进行处理)

获取随机数采用random模块。
> random() 方法返回随机生成的一个实数，它在[0,1)范围内。
> ```
> import random
> 
> random.random()
> ```
> random()是不能直接访问的，需要导入 random 模块，然后通过 random 静态对象调用该方法。

[解题]
```

```
