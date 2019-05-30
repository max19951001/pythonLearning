### 升级版 家具

```python
# coding=utf-8


class Home:  # 定一个家类：home

    def __init__(self, area):
        self.area = area
        self.rongNaList = []
        self.light = "off"  # 灯的属性

    def __str__(self):
        msg = '家当前的可用面积为 ： ' + str(self.area) + '; 灯的状态为： ' + self.light
        if len(self.rongNaList) > 0:
            msg += "  ;当前有 ："
            for temp in self.rongNaList:   # 因为在append的时候，添加的是对象的引用，那么此时的temp就是对象的应用，可以理解为是一个对象。
                msg += temp.getBedName() + ', '
            msg = msg.strip(', ')
        return msg

    def containItem(self, item):
        bedArea = int(item.getBedArea())
        if self.area > bedArea:
            self.rongNaList.append(item)
            self.area -= bedArea
            print('当前添加物品成功。。。当前家可用面积为：%d' % self.area)

    def turnOn(self):
        self.light = 'on' # 把家里的灯打开了
        # 把家里的所有家具，都变为"亮"状态
        for temp in self.rongNaList:
            temp.setLightOn()


class Bed:  # 定义一个床类：bed

    def __init__(self,  area, name):
        self.area = area
        self.name = name
        self.light = 'off'

    def __str__(self):
        msg = self.name + '占用的面积为: ' + str(self.area) + ';当前明暗程度 ' + self.light
        return msg

    def getBedArea(self):
        return self.area

    def getBedName(self):
        return self.name

    def setLightOn(self):
        self.light = 'on'

    def setLightOff(self):
        self.light = 'off'


home = Home(180)
print(home)
bed = Bed("4", "席梦思床")
print(bed)

home.containItem(bed)
print(home)# coding=utf-8


class Home:  # 定一个家类：home

    def __init__(self, area):
        self.area = area
        self.rongNaList = []

    def __str__(self):
        msg = '家当前的可用面积为 ： ' + str(self.area)
        if len(self.rongNaList) > 0:
            msg += "  ;当前有 ："
            for temp in self.rongNaList:   # 因为在append的时候，添加的是对象的引用，那么此时的temp就是对象的应用，可以理解为是一个对象。
                msg += temp.getBedName() + ', '
            msg = msg.strip(', ')
        return msg

    def containItem(self, item):
        bedArea = int(item.getBedArea())
        if self.area > bedArea:
            self.rongNaList.append(item)
            self.area -= bedArea
            print('当前添加物品成功。。。当前家可用面积为：%d' % self.area)


class Bed:  # 定义一个床类：bed

    def __init__(self,  area, name):
        self.area = area
        self.name = name

    def __str__(self):
        msg = self.name + '占用的面积为: ' + str(self.area)
        return msg

    def getBedArea(self):
        return self.area

    def getBedName(self):
        return self.name


home = Home(180)
print(home)
bed = Bed("4", "席梦思床")
print(bed)

home.containItem(bed)
print(home)
```

## 1,1 保护对象的属性

````python
# 如果有(object)叫 新式类
#原来的那种没有的，叫经典类,所以平时用新式类

class Person(object):
    def __init__(self, name, age):
        self.name = name
        self.age = age
````

* **对于方法内的属性修改，一般是在类中定义一个方法来修改属性，与此同时，为了避免在实例对象中更改对象属性。将对象名前面加上'__',其属性也叫私有属性**
* **另外，获取属性一般也将其定义为方法，方法返回到对象的属性。**

```python
class Person(object):
    def __init__(self, name, age):
        self.__name = name
        self.__age = age  # 私有属性
    	self.higt = 180   # 公有属性
    def __str__(self):
        return '年龄为： ' + str(self.__age)
   
	def setNewAge(self, newAge):
        if newAge>0 and newAge<80:
        	self.__age = newAge
     
    def getNewAge(self):
        return self.__age

xiaoming = Person('小明', 18)
print(xiaoming)

xiaoming.setNewAge(19)
print(xiaoming)
```

## 1.2  __del__（）方法及多个变量保存同一对象的引用。

```python
创建对象后，python解释器默认调用__init__()方法
当删除一个对象时，python解释器也会默认调用一个方法，这个方法为__del__()方法

class Animal(object):
    
    # 初始化的事情
    def __init__(self, name):
        self.__name = name
        
        
    # 结束前的事情
    def __del__(self):
        print("___啊。。。 ")
        
dog = Animal("旺财")   

print("____111--------------")

result:____111--------------
___啊。。。 
#虽然没有调用_del_ 方法，那是谁调用的?
#python解释器，如果监测到一个对象没有任何用处了，那么就把这个对象杀掉了。 

dog = Animal("xiaobai")
dog1 = dog
dog2 = dog

# 引用计数
print("____111--------------")
del dog
del dog1
del dog2
print("___222-------------")
# 结果

result:____111--------------
___啊。。。 
___222-------------

#另一种情况

print("____111--------------")
del dog
del dog1

print("___222-------------")
del dog2

#结果
result:____111--------------
___222-------------
___啊。。。 


# 注意以上两者的区别，叫做引用计数，当所有对象引用执行完了，才会执行__del__函数。所以，对于第二种情况，当删除dog1 和dog只是删除了对象的其他两个引用，当删除dog2 则删除了所有引用，同时删除了对象，那么就会执行del()函数

```

## 1.3  继承

```python
#1 定义了一个动物类
# 1 定义了一个动物类
class Animal(object):

    # 初始化的事情
    def __init__(self, name='动物', color='白色'):
        self.__name = name #私有属性，不会被继承
        self.__color = color

    # 结束前的事情
    def __del__(self):
        print("___啊。。。 ")


# 2 代表狗类
class Dog(object):
    # 初始化的事情
    def __init__(self, name='狗', color='白色'):
        self.__name = name
        self.__color = color

    # 临死前做的事情：
    def __del__(self):
        print("----啊啊啊————————")

    def printInfo(self):
        print('名字是： %s' % self.__name)
        print('颜色是： %s' % self.__color)


wangcai = Dog( name='旺财')
wangcai.printInfo()

result:
名字是： 旺财
颜色是： 白色
----啊啊啊————————

# 上面代码中两个类方法有重复，所以继承就可以解决此问题
class Animal(object):# 默认是object,所有类继承object

    # 初始化的事情
    def __init__(self, name='动物', color='白色'):
        self.name = name
        self.color = color

    # 结束前的事情
    def __del__(self):
        print("___啊。。。 ")


# 2 代表狗类
class Dog(Animal):

    def printInfo(self):
        print('名字是： %s' % self.name)
        print('颜色是： %s' % self.color)


wangcai = Dog( name='旺财')
wangcai.printInfo()


```

* **继承(私有属性，私有方法)**

```python
# coding=utf-8


class Animal(object):

    def __init__(self):
        self.a = 9
        self.__b = 10

    def test1(self):
        self.a = 10
        self.__b = 11
        print(self.a)
        print(self.__b)


class Dog(Animal):

    def test2(self):
        print(self.__b)


dd = Dog()
dd.test1()#如果是通过继承来的方法访问父类的私有属性是可以的
dd.test2()# 如果是在之类中，自定义了一个方法，此方法不能访问父类中的私有属性。


result:

10
Traceback (most recent call last):
11
  File "D:/untitled/max.py", line 25, in <module>
    dd.test2()
  File "D:/untitled/max.py", line 20, in test2
    print(self.__b)
AttributeError: 'Dog' object has no attribute '_Dog__b'


#2 私有方法

# coding=utf-8


class Animal(object):

    def __init__(self):
        self.a = 9
        self.__b = 10

    def test1(self):
        self.a = 10
        self.__b = 11
        print(self.a)
        print(self.__b)

    # 如果在方法名前面加上2个下划线，那么这个方法就成了私有方法  ，所以这个方法只能在这个类内部调用，继承这个类的新类不能使用这个方法
    def __test3(self):
        self.a = 10
        self.__b = 11
        print(self.a)
        print(self.__b)

    # 但是有时候特殊人确实需要调用这个方法，那么我就在类内部写入一个新的方法，里面设置一定权限，然后去调用上面的方法
    def test4(self):
        # 判断用户的密码或者权限
        self.__test3()


class Dog(Animal):

    def test2(self):
        print(self.__b)


dd = Dog()
dd.test4()

result:
10
11



```

## 1.4 重写父类的方法

####  * 所谓重写，就是在之类中，有一个和父类相同名字的方法，在子类中的方法会覆盖掉父类中同名的方法

```python
# coding=utf-8


class Animal(object):

    def bark(self):
        print("啊啊啊啊。。。。")


class Cat(Animal):

    def bark(self):
        # 调用父类的这个方法
        Animal.bark(self)  # 调用父类的方法叫做重写，注意加上self
        # 调用上一级父亲的方法
        super().bark()    # 同样调用上一级父类的方法，不用加self
        print("喵喵。。。")


tom = Cat()
tom.bark()


result:
    啊啊啊啊。。。。
	啊啊啊啊。。。。
	喵喵。。。
```

## 1.5 多继承

* **多继承即继承多个类**

```python
# coding=utf-8


class A(object):

    def testA(self):
        print("------------a test")


class B(object):

    def testB(self):
        print("--------------b test")


class C(A, B):
    pass


c = C()
c.testA()
c.testB()

result:
    ------------a test
--------------b test



# 广度遍历
# 广度遍历
class Base(object):

    def test(self):
        print('---------base test')


class A(Base):

    def test2(self):
        print("------------a test")


class B(Base):

    def test2(self):
        print("--------------b test")


class C(A, B):
    pass


c = C()
c.test()

print(C.__mro__) # 可以查看C类的对象搜索方法时的先后顺序

result:
    ---------base test
(<class '__main__.C'>, <class '__main__.A'>, <class '__main__.B'>, <class '__main__.Base'>, <class 'object'>)
    
#广度遍历，先遍历兄弟父类，然后爷爷类
```

## 1.6 多态

* **”多态“是指调用的方法是同一个，但是执行的代码或者说 现象不一样****

* **当子类和父类都存在相同的`bark()`方法时，我们说，子类的`bark()覆盖了父类的`bark()`，在代码运行的时候，总是会调用子类的`bark()`。这样，我们就获得了继承的另一个好处：多态**



* 有了继承，才能有多态

```python
class Animal(object):

    def bark(self):
        print('啊啊啊。。。')


class Dog(Animal):

    def bark(self):
        print('汪汪汪。。。')


class Cat(Animal):

    def bark(self):
        print('喵喵喵。。。')


def animalBark(temp):
    temp.bark()


maomi = Cat()
wangcai = Dog()
animalBark(maomi)
animalBark(wangcai)

result:
    喵喵喵。。。
	汪汪汪。。。
# 同时调用bark()方法，但是不同对象其bark和父类的方法名一样，但作用不一样。所以输出的也不一样
```

## 1. 7 类属性和类方法

### 类属性

**在类和类中方法中定义的属性称为类属性。**

* 这个属性属于类属性，存储在类的内存空间中

* 在方法中的属性称为实例对象的属性，存储在实例的内存空间

  注意：**类对象和实例对象都可以访问类属性**，

**如果实例对象中没有和类属性同名的属性，就会去访问类属性。**

 **类对象也不能访问实例对象中的属性,即你没有对象，怎么做对象该做的事情。哈哈**

```python
 # coding=utf-8


class People(object):
    address = '山东'

    def __init__(self):
        self.name ='hello'
        self.age = '18'


people = People()
print(people.age)
print(people.address)
print(People.address)
print('*'*50)
print(People.age)


result:
    山东
	山东
		**************************************************
  File "D:/untitled/max.py", line 17, in <module>
    print(People.age)
AttributeError: type object 'People' has no attribute 'age'

```

## 类方法

在方法 前面加上'@classmethod'

#### 重要：

* **类对象，可以调用类属性，也可以调用类方法， 但类对象不能调用实例方法和实例属性**
* **实例对象可以获取实例和类的属性值，但实例对象只能修改实例属性，不能修改类属性，也可以调用实例方法和类方法。**

```python
class People(object):
    address = '山东'

    def __init__(self):
        self.name = 'hello'
        self.age = '18'

    @classmethod  #类方法可以修改类属性
    def setNewAddress(cls):
        cls.address = '内蒙古'


people = People()
People.setNewAddress()
print(People.address)
print(people.setNewAddress())

resultr:内蒙古
    	内蒙古
```

## 1.8 异常

当python监测到一个错误时，解释器无法执行代码，则会抛出一个异常。

```python
try:
    
    可能出错的代码块
    
except (IOError,NameError):  # ()里面为多个异常 
    如果捕获到异常，则执行。。
    
```

**注意：一般处理流程是发生错误了，然后将可能出现错误的代码放到try中。**

* 为了保留系统给的系统错误信息，则在except 后面加上as:

  ```python
  try:
      
      可能出错的代码块
      
  except (IOError,NameError) as variable:  # ()里面为多个异常 
      如果捕获到异常，则执行。。
      print(variable)
  ```

  

### try ...finally

**不管捕获到异常还是没捕获掉，都执行finally .作用是一旦发生错误，程序可能崩溃，所以执行finally。**

```python
try:
    num = 100
    print(num)
except (NameError) as errorMsg :
    print('产生了错误%s' %errorMsg)
else:
    print('没有捕获到异常')
finally:
    print('我一定会执行的')
```

## 1.9 抛出异常(人为引发异常)

**用raise语句来引发一个异常。异常/错误对象必须有一个名字，且它们应该是Error或者Exception类的子类。**

```python
# coding=utf-8


class ShortInputException(Exception):
    '''
    定义的异常类
    '''

    def __init__(self, length, atleast):
        Exception.__init__(self)
        self.length = length
        self.atleast = atleast


try:
    s = input('请输入 --->')

    if len(s) < 3:
        # raise引发一个你定义的异常
        raise ShortInputException(len(s), 3)


except EOFError:
    print('你输入了一个结束标志EOF')
except ShortInputException as x:
    print('ShortInputException:输入的长度是 %d,长度至少应是 %d' % (x.length, x.atleast))
else:
    print('没有异常发生')

    
result:
    
    请输入 --->22
ShortInputException:输入的长度是 2,长度至少应是 3
```

