# 面向对象OOP（Object Oriented Programming）
## 类与对象概述
* 类：类是对象的抽象，比如飞机图纸，月饼模具
* 对象：对象是类的实例，比如飞机、月饼
* 面向对象的三大特点：封装、继承（默认继承object）、多态
* 关系：类是对象的模型，对象是类的具体实例化
## 语法
```
class  类名(基类、父类)
    # 实例属性
    def __int__(self):   # self => this 实例 ;  __int__ => constructor (构造函数)
        self.name='wss'
        self.age = 18
    # 实例方法
    def say(self):
        print(self.name)
```
实际操作示范
```
# class Person:
#     def __init__(self,name='wss',age=18):
#         self.name= name
#         self.age = age
#     def say(self):
#         print("my name is %s"%self.name)
#     def a(self):
#         print("I am %s years old"%self.age)
# # 实例化，创建对象
# xm = Person('小明',17)
# xm.say()
# xm.a()
```
## 案例
### 时钟
```
## 创建一个时钟类
# 属性  小时:分钟:秒钟
# 方法
# run  表跑起来
# set  设置时间
# print（obj）  输出现在的时间
# class Clock:
#     def __init__(self,hou=0,min=0,sec=0):     # 魔法方法
#         self.hou = hou
#         self.min = min
#         self.sec = sec
#     def __str__(self):    # 对实例的描述  print(obj) 打印 __str__()魔法方法的返回值
#         return '%0.2d:%0.2d:%0.2d'%(self.hou,self.min,self.sec)
#     def run(self):
#         while True:
#             print(self)
#             time.sleep(1)   # 阻塞代码
#             self.sec += 1
#             if self.sec>59:
#                 self.min+=1
#                 self.sec=0
#                 if self.min>59:
#                     self.hou+=1
#                     self.min=0
#                     if self.hou>23:
#                         self.hou=0
#
#
# c1 = Clock(0,0,0)
# c1.run()
```
### 烤地瓜
```
## 创建一个烤地瓜类
# 属性：
# cookedLevel：这是数字；0~3表示还是生的，超过3表示半生不熟，超过5 表示已经烤好了，超过8表示已经烤成了木炭！地瓜刚开始的时候是生的。
# cookedString：这是字符串；描述地瓜的生熟程度
# condiments:这是地瓜的配料表，比如番茄酱、芥末酱
# 方法：
# cook() 把地瓜烤一段时间
# addCondiments() 给地瓜添加配料
# __init__() 设置默认属性
# __str__() 让print的结果看起来更好一些

class Potato:
    def __init__(self,cookedLevel=0,cookedString='生',condiments='番茄酱'):
        self.cookedLevel = cookedLevel
        self.cookedString = cookedString
        self.condiments = condiments
        self.condimentsList = ['芥末酱','番茄酱','甘梅酱']
    def __str__(self):
        return '您好，这是您的%s口味的%s的地瓜'%(self.condiments,self.cookedString)
    def cook(self,min):
        # while True:                    # 没有这行代码，结果打印一行
        #     time.sleep(1)                     # 阻塞代码
            self.cookedLevel += min             # 每秒加一
            if self.cookedLevel>=0 and self.cookedLevel<4:
                self.cookedString = '生'
            elif self.cookedLevel<6:
                self.cookedString = '半生不熟'
            elif self.cookedLevel<8:
                self.cookedString = '可以享用了'
            elif self.cookedLevel>=8:
                self.cookedString = '糊巴了'
    def addCondiments(self,num):
        self.condiments = self.condimentsList[num]


# 客户来了
p1 = Potato()
p2 = Potato()
p3 = Potato()
p4 = Potato()

p1.cook(2)
p2.cook(5)
p3.cook(7)
p4.cook(9)

p1.addCondiments(0)
p2.addCondiments(2)
p3.addCondiments(1)
p4.addCondiments(2)

print(p1)
print(p2)
print(p3)
print(p4)
```

### 绝地求生
```

class Ren:
    def __init__(self,name):
        self.name = name
        self.xue = 100
        self.qiang = None
    def __str__(self):
        return self.name + "剩余血量" + str(self.xue)
 
    def anzidan(self,danjia,zidan):
        danjia.baocunzidan(zidan)
 
    def andanjia(self,qiang,danjia):
        qiang.lianjiedanjia(danjia)
 
    def naqiang(self,qiang):
        self.qiang = qiang
 
    def kaiqiang(self,diren):
        self.qiang.she(diren)
 
    def diaoxue(self,shashangli):
        self.xue -= shashangli
 
class Danjia:
    
    def __init__(self,rongliang):
        self.rongliang = rongliang
        self.rongnaList = []
 
    def __str__(self):
        return "弹夹当前的子弹数量为:"+str(len(self.rongnaList))+"/"+str(self.rongliang)
 
    def baocunzidan(self,zidan):
        if len(self.rongnaList)<self.rongliang:
            self.rongnaList.append(zidan)
 
    def chuzidan(self):
        #判断当前弹夹中是否还有子弹
        if len(self.rongnaList) >0:
            zidan = self.rongnaList[-1]
            self.rongnaList.pop()
            return zidan
        else:
            return None
 
class Zidan:
 
    def __init__(self,shashangli):
        self.shashangli = shashangli
 
    def shanghai(self,diren):
        diren.diaoxue(self.shashangli)
 
 
class Qiang:
    def __init__(self):
        self.danjia = None
 
    def __str__(self):
        if self.danjia:
            return "枪当前有弹夹" 
        else:
            return "枪当前没有弹夹"
 
    def lianjiedanjia(self,danjia):
        if not self.danjia:
            self.danjia = danjia
    def she(self,diren):
        zidan = self.danjia.chuzidan()
        if zidan:
            zidan.shanghai(diren)
        else:
            print("没与子弹了,放了空气那个....")
 
 
#创建一个人，老王
laowang = Ren("老王")
#创建一个弹夹，有20发容量
danjia = Danjia(20)
#打印当前弹夹容量
print(danjia)
 
#把子弹装入弹夹
i=0
while i<5:
    zidan = Zidan(5)
    laowang.anzidan(danjia,zidan)
    i+=1
 
#打印当前弹夹容量
print(danjia)
 
#创建一把枪
qiang = Qiang()
#打印枪的情况
print(qiang)
#老王装弹夹
laowang.andanjia(qiang,danjia)
#打印枪的情况
print(qiang)
 
#创建一个敌人
diren = Ren("敌人")
print(diren)
#老王拿枪
laowang.naqiang(qiang)
#老王开枪
laowang.kaiqiang(diren)
laowang.kaiqiang(diren)
print(diren)
--------------------- 
作者：weixin_33965305 
来源：CSDN 
原文：https://blog.csdn.net/weixin_33965305/article/details/88115529 
版权声明：本文为博主原创文章，转载请附上博文链接！
```
## 类变量与实例变量

**类变量**：定义在类中，可以被类方法（修改），可以被实例访问  
**实例变量**：实例变量只能实例调用，且权重大（优先级大），它是后写的，可以把之前的内容覆盖掉
### 案例

```
# class P:
#     sex = '男'       # 类变量，能够被实例继承（图纸）
#
#     def __init__(self):
#         self.name = 'xm'        # 实例属性，实例变量
#         self.sex = '男'          # 实例变量只能实例调用，且权重大（优先级大），它是后写的，可以把之前的内容覆盖掉
#
#     @staticmethod  # 静态类方法，什么都不能调用，就是一个普通的公共函数功能， 连指针都没有
#     def say2():
#         print("this is static")
#
#     @classmethod        # 类方法，可调用类变量
#     def setSex(cls,sex):
#         print(cls.name)
#         cls.sex = sex
#
#     def say1(self):      # 实例方法，可调用实例的方法和属性，还可以调用继承过来的类变量
#         print(self.name)
#         print(self.sex)


# xm = P()
# # xm.sex = '女'        # 创建了实例属性（实例对象），给实例重新赋予属性
# P.sex = '女'       # 所有的实例用的都是同一个类变量
# print(xm.sex)       # 类变量可以被实例调用，实例变量与类变量重名时，优先调用实例变量
# print(P.sex)        # 类变量也可以被类调用

# xh = P()
# xh.say1()
# xh.say2()

# xm = P()
# print(xm.name)
# print(xm.sex)   # 小明的sex继承的类变量
# P.setSex('女')   # 调用类方法，修改类变量
# print(xm.sex)
# xm.setSex('男')     # xm这个实例调用了继承的类方法，修改了类变量
# print(xm.sex)
# xm.sex = '女'    # 添加了实例属性sex，覆盖了继承来的类变量sex，并没有修改了类变量
# print(xm.sex)
# print(P.sex)
```
## 静态类方法、类方法、实例方法
* 静态类方法:通过@staticmethod 装饰，不依赖于类变量、类方法，实例变量、实例方法
	* @staticmethod
* 类方法:通过@classmethod 装饰，修改类变量
	* @classmethod
* 实例方法 ：可调用实例的方法和属性，还可以调用继承过来的类变量 
## 私有属性和私有方法(__spam)
### 定义：
所谓私有，就是在外部不能调用，方法之间可以使用的
私有方法以及属性需要在方法名或属性名前加"__",但是python中没有真正的私有方法、私有属性
### 案例
```
# class P():
#     def __init__(self,name,age):
#         self.__name = name
#         self.__age = age
#     def say(self):
#         print("my name is %s"%self.__name)      #内部可以使用__name
#
# p = P('小红',19)
# print(dir(p))
# p.__name = "肖红"     # 外部不可使用__name
# p._P__name = "肖红"       # 君子协议，但是可以强制改
# p.say()
```
## 继承与多重继承(深度优先、从左至右)
```
# 多重继承：从左至右，深度优先（python3）
# class A:
#     def __init__(self):
#         pass
#     def run(self):
#         print("A")
#
# class B:
#     def __init__(self):
#         pass
#     def run(self):
#         print("B")
#
# class C(A):
#     def __init__(self):
#         pass
#     def say(self):
#         print("C")
#
# class D(B):
#     def __init__(self):
#         pass
#     def say(self):
#         print("D")
#     def run(self):
#         print("D->run")
#
# class F(C,D):
#     def __init__(self):
#         pass
#
#
# print(dir(C))
# print(dir(D))
# f = F()
# f.say()     # 从左至右
# f.run()     # 从上到下,深度优先
```

```
# 多重继承：从左至右
# class Car():
#     def __init__(self):
#         self.pp = ""
#         self.color = ""
#     def run(self):
#         print("启动")
#
# class FT(Car):
#     def __init__(self):
#         super().__init__()  #super 相当于this指针，用来引用父类而不必显式地指定它们的名称
#         self.type = ""
#
# class HG(FT):
#     def __init__(self):
#         super(HG,self).__init__()
#         self.price = ""
#
# hg1 = HG()
# print(dir(hg1))
```
## 魔法方法
```
__slots__  限制Class属性和方法
```

```
# class P:
#     """
#     Person类    人类
#     """
#     def __init__(self):
#         pass
#     __slots__ = ['name','sex']
#     __name__ = "Person"
#     def run(self):
#         print(self.__doc__)
#
# p = P()
# P.name = "wss"
# p.sex = "男"
# # p.age = 18
# print(dir(p))
# print(p.__doc__)
```

```
__name__   类名字
```
```
 print(self.__doc__)  类文档字符串、开头注释
 ```

 ```
 # 拿到函数的注释
# def fn():
#     """
#     this is fn
#     :return:
#     """
#     pass
# print(fn.__doc__)
```
```__new__  与  __init__  关系```
```
__new__   ：第一步、创建一个对象，必须有返回值。把实例创建出来，可能任何属性都没有
__init__    ：第二步、给实例初始化，赋予属性

# __new__  与  __init__  关系
# class Car:
#     def __init__(self):
#         self.color = ""
#
# class BMW(Car):
#     def __new__(cls, *args, **kwargs):      # 第一步、创建一个对象，必须有返回值。把实例创建出来，可能任何属性都没有
#         print("new")
#         return super().__new__(BMW)
#
#     def __init__(self):     # 第二步、给实例初始化，赋予属性
#         print("init")
#         self.pingpai = ''
#
#     def __del__(self):
#         print('del')
#
# b = BMW()       # b运行完被回收了
# # print(dir(b))
# del b
# print(b)
```
```
__str__   给实例一个描述
```
```
__del__   实例注销时调用
```
### 常用魔法方法
```
1 __init__
初始化类时定义一些操作。

```
```
2 算术运算
2.2.1 __add__
实现了类与类之间的加法运算.。需要注意的是，两个类要同类型啊。
class Vector2D:
    def __init__(self,x,y):
        self.x = x
        self.y = y
    def __add__(self,other):
        return Vector2D(self.x + other.x,self.y + other.y)

first = Vector2D(1,2)
second = Vector2D(4,6)
result = first + second
print(result.x)
print(result.y)

2.2 __sub__
类似的，这是类与类之间的减法运算.。

2.3 __mul__
类与类之间的乘法运算.。

2.4 __truediv__
类与类之间的真除。只有from future import division之后它才有效

2.5 __floordiv__
类与类之间的浮点除法运算.。

2.6 __mod__
类与类之间的取余运算.。

2.7 __pow__
类与类之间的指数运算.。

2.8 __and__
类与类之间的按位与运算.。

2.9 __xor__
类与类之间的按位异或运算.。

2.10 __or__
类与类之间的按位或运算.。
```
```
3 比较运算
3.1 __It__
定义了比较操作符<。

3.2 __gt__
定义了比较操作符>。.

3.3 __le__
定义了比较操作符<=。

3.4 __ge__
定义了比较操作符>=。

3.5 __eq__
定义了比较操作符==。

3.6 __ne__
定义了比较操作符!=。
```

```
4 容器所使用的一些魔法方法
在Python中，常见的容器类型有: 词典, 元组, 列表等。

4.1 __len__
返回容器的长度。

4.2 __getitem__
getitem(self, key),使用self[key]访问容器内容。

4.3 __setitem__
setitem(self, key, value)，使用self[nkey] = value赋值容器中的一项。

4.4 __delitem__
delitem(self, key)，删除self[nkey]。
```
## 验证
* ifinstance（）来检查一个实例的类型
	* print(isinstance(obj，class))  验证obj是否为class的实例
* lssubclass（）来检查类的继承关系
	* print(issubclass(P,A))
* type（）查看类型  
dir（）获取对象的属性和方法