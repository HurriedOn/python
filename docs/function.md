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

实例1：
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

func2()   #输出：add  hell
#func1(func2)()
```
