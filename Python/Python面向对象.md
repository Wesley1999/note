# Python面向对象

## 类
```
class Linux:
    pass
```

初始化
```
def __init__(self, a):
    pass
```

创建实例
```
linux = Linux()
```

## 封装
```
class Linux:
    a = None
    def setA(self, a):
        self.a = a
```
## 继承
```
class Linux:
    def fun1(self):
        pass
class Ubuntu(Linux):
    def fun1(self):
        print (1)
```
`Ubuntu`继承了`Linux`类并重写了父类的`fun1()`方法

> 在类中用def定义的称为方法，类外面用def定义的称为函数

## 多态
```
linuxes = [Ubuntu(), Opensuse(), Suse()]
for linux in linuxes:
    linux.fun1()
```
在调用`linux.fun1()`时，如果子类重写了父类的fun1()方法，调用的就是子类的方法，否则调用的是父类的方法。