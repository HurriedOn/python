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

- 子类实例属于父类
- 父类实例属于父类
- 父类实例不属于子类

```py
>>>class A:
...  def __init__(self):
...    print('This is A')

>>>class B:
...  def __init__(self):
...    print('This is B')
 
 >>>a=A()
This is A
>>>b=B()
This is B
>>>isinstance(a,A)
True
```
