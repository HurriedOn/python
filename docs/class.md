# Python面向对象

---

## 类属性中的变量

类和实例：
```py
>>>class A:
...  num=1
...
#创建一个类，具有一个类中属性num，值为1
>>>a=A()
>>>b=A()
>>>a.num
1
>>>b.num
1
#创建的两个实例a,b均可访问其中的num
```

---

## 构造函数__init__

 注意：特殊方法“__init__”前后分别有两个下划线！！！
 
 注意到__init__方法的第一个参数永远是self，表示创建的实例本身，因此，在__init__方法内部，就可以把各种属性绑定到self，因为self就指向创建的实例本身。

有了__init__方法，在创建实例的时候，就不能传入空的参数了，必须传入与__init__方法匹配的参数，但self不需要传，Python解释器自己会把实例变量传进去。

__init__(self)是一种特殊的方法，专门用在类中，称为类的构造函数或初始化方法，当你创建一个类的实例的时候就会调用这个方法；构造方法也支持重写，如果你没有重写自己的构造函数，系统会有默认的构造函数用来执行。不需要我们显示的调用，一般构造函数在生成实例的过程中为实例初始化数据。

注意：构造函数是不可以有返回值的

```py
>>>class A:
     def __init__(self):
        self.num=1
#这里我们通过构造函数来给实例对象初始化变量
>>>A.num
Traceback(most recent call last):
 File"<stdin>",line 1,in <module>
AtrributeError:type object 'A' has no attribute 'num'
#可以看到因为现在这个变量已经是定义给实例的，所有类已经不能使用了
#我们想使用这个变量只能是通过实例访问

```

```py
class Student(object):
    def __init__(self, name, score):
        self.name = name
        self.score = score
        
>>> bart = Student('Bart Simpson', 59)
>>> bart.name
'Bart Simpson'
>>> bart.score
59        
```

---

## 多态

多态：根据数据的类型执行不同的操作

实现多态：在面向对象中实现多态，通过对子类重新父类中已有函数

- 子类实例属于父类
- 父类实例属于父类
- 父类实例不属于子类

isinstance() 函数来判断一个对象是否是一个已知的类型，类似 type()。如果要判断两个类型是否相同推荐使用 isinstance()。

```py
>>>num = 2
>>> isinstance (num,int)
True
>>>
>>>
>>>class A:
...  def func(self):
...    print('This is A')

>>>class B(A):
...  def func(self):
...    print('This is B')
 
>>>a=A()
>>>a.func()
This is A
>>>b=B()
>>>b.func()
This is B

# a属于A   b属于B   B继承A
>>>isinstance(a,A)
True
>>>isinstance(b,B)
True
>>>isinstance(a,B)
False
>>>isinstance(B,A)
False
```

---

## 类中内建函数

\__call\__(self)：这个函数重载了()这个符号，实例出来的对象可以当作函数来用，默认系统是没有实现的

```py
>>>class B:
...  pass
>>>b=B()
>>>b()
TypError:'B' object is not callable
>>>
>>>
>>>class A:
...  def __call__(self):
...    print('AAA')
>>>a=A()
>>>a()
AAA
```

我们经常遇到的这个callable错误就说明你把一个没有重写call函数的对象实例当作函数方法来调用了


\__del\__(self)：在释放对象时调用，也支持重写，可以在里面进行一系列释放资源的操作；不需要显示的调用，也就是说他会自动在对象资源销毁时使用

\__new\__(self):之前我们都一直在用init函数，把他当作构造实例的一个函数。但其实在他之前，真正起到构造类实例的函数是__new__

```py
class A:
    def __del__(self):
        print('del')
    def __new__(self):   # new函数第一个执行，执行过程中，分配空间
        print('new')
        return super(A,self).__new__(self)
    def __init__(self):  # 数据初始化
        print('init')

a=A()
print('----')

# 输出
# new
# init
# ----
# del
# [Finished in 0.1s]

```

__slots__属性：可以把实例属性锁定到__slots__规定的范围内


