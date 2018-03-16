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
bibo1()

#例2：
def func1(num1):
    def func2(num2):
        print(num1,'+',num2,'=',num1+num2)
    return func2
bibo2=func1(10)
bibo2(2)
```
