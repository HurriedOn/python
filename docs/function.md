# Python函数

---

## 函数闭包

内部函数对外部函数作用域里变量的引用（非全局变量），则称内部函数为闭包。

一个闭包就是你调用了外部函数，外部函数返回内部函数。此时的内部函数就叫做闭包函数。

闭包在运行时可以有多个实例，不同的引用环境和相同的函数组合可以产生不同的实例。

例如：
```py
#例1：
def wai():
    a=1
    def nei():
        print(a)
    return nei
bibo1=wai()
bibo1()       # 输出：1

#例2：
def func1(num1):
    def func2(num2):
        print(num1,'+',num2,'=',num1+num2)
    return func2
bibo2=func1(10)
bibo2(2)         # 输出：10 + 2 = 12

#例3：
mylist=[1,2,3]
def func(obj):
    def func4():
        obj[0]+=1
        print(obj)
    return func4

bibo=func(mylist)
bibo()             # 输出：[2, 2, 3]
print(mylist)      # 输出：[2, 2, 3]
```
闭包私有化了变量，原来需要类对象完成的工作，闭包也可以完成

由于闭包引用了外部函数的局部变量，则外部函数的局部变量没有及时释放，消耗内存

在Python中，使用闭包的另一个场景就是装饰器，也叫语法糖@

---

## 装饰器

装饰器：在函数运行时增加功能且不影响这个函数原有内容，还可以进行函数执行后的清理工作

语法：
```py
@func1
def func2():
    pass
```

装饰器做的事情就是func1(func2)我们传递了一个函数对象到我们的装饰器里面然后先执行装饰器func1其中的内容，然后再执行函数func2

示例1：
```py
#func1：装饰器函数
#func2：被装饰的

def func1(func):
    def add_fun():
        print('add')
        return func()
        #func 函数名
        #func() 函数调用
    return add_fun
@func1
def func2():
    print('hell')

func2()   
#func1(func2)()
# 输出：
#    add  
#    hell
```
示例2（被装饰的函数带有参数）：
```py
def func1(func):
    def add_func(a,b):
        print(a,b)
        return func(a,b)
    return add_func

@func1
def func(x,y):
    print(x,'+',y,'=',x+y)

func(2,8)  
#func1(func(2,8))
# 输出：
#    2 8     
#    2 + 8 = 10
```
示例3（装饰器函数带参数）：
```py
def arg_func(arg):
    def _func(func):
        def add_func():
            if arg =='bad':
                print('do not go')
            if arg =='good':
                print('go')
            return func()
        return add_func
    return _func

@arg_func('bad')
def func1():
    print('bad day')

@arg_func('good')
def func2():
    print('good day')

func1() 
#输出：
#do not go
#bad day
func2()
#输出：
#go
#good day
```

---

## 正则

Python中，正则使用re模块，该模块为Python发行版本中自带的模块，不需要安装

#### re模块
re.compile(pattern):编译正则表达式

匹配match从字符串的开头进行匹配

搜索search从字符串的任意部位开始匹配

re.match（pattern，string）：尝试用正则表达式模式pattern匹配字符串string；匹配成功，则返回一个匹配对象，否则放回None；成功是可以使用结果的group函数获取匹配到的值

re.search(pattern,string)：返回字符串中正则表达式pattern的第一次出现

```py
>>>import re
>>>regex=re.compile('^a')
>>>res=re.match(regex,'abc')
>>>res.group()
'a'
>>>
>>>
>>>rul=re.comple('123')
>>>res=re.search(rul,'abcd123dfdg')
>>>res
<_sre.SRE_Match object;span=(4,7),match='123'>
```

re.findall(pattern,string):返回字符串中正则表达式pattern的所有(非重复）出现，并且总是返回一个列表

re.sub(str1,str2,str3)

re.subn(str1,str2,str3)

- str1:要替换的字符串
- str2:替换成什么
- str3:在哪个字符串例进行替换
    
这两个函数都可以实现搜索和替换功能，均返回一个替换之后的新字符，subn函数会返回一个表示替换的总数

```py
>>>import re
>>>regex=re.compile('[0-9]+')
>>>res=re.findall(regex,'a123bcd67efg5hj9ki')
>>>res
['123','67','5','9']
>>>
>>>
>>>mystr='a*b*c'
>>>re.sub('\*','-',mystr)
'a-b-c'
>>>mystr='abc123dfd8'
>>>re.sub('[0-9]+','',mystr)
'abcdfd'
>>>re.subn('[0-9]','',mystr)
('abcdfd',2)
```




