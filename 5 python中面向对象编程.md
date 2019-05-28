* **面向过程：根据业务逻辑从上到下写代码**

* **面向对象：对数据与函数绑定到一起，进行封装，这样能够更快速的开发过程。**

  

### 重要： 面向对象编程的2个非常重要的概念：类和对象。

*  类就是创建对象的模板。
* 类是抽象的

## 1.1 类的构成

类由3个部分构成：(1)类的名称：类名；(2)类的属性：一组数据

(3)类的方法：允许对进行操作 的方法(行为)



### 举例：

人的类：类名：人(Person);  属性：身高(height)、年龄(age) ; 方法：跑(run)、打架(fight)

### 注意：类的方法 等于函数

## 1.2 定义类

```python
class 类名：# 类就等于属性+方法
	方法

# 定义了一个狗类    
class Dog:  # 类名使用大驼峰
    
    def bark(self): #在类的方法中，方法参数中写入self
        print("汪汪汪")
    
    
    def run(self):
        print("狗在疯狂的叫")
    
```



## 1.3 创建对象

```python
# 定义了一个狗类    
class Dog:  # 类名使用大驼峰
    
    def bark(self): #在类的方法中，方法参数中写入self
        print("汪汪汪")
    
    
    def run(self):
        print("狗在疯狂的叫")

# 创建一个小狗
xiaoGou = Gog()
# 调用对象的方法
xiaoGou.bark()
xiaoGou.run()


# 添加属性
xiaoGou.weight = 5
xiaoGou.color = '黄色'

# 获取小狗的属性
print(xiaoGou.weight)
print(xiaoGou.color)
```



## 1.4 self

* self理解为自己，在python中指的是类的对象

* 某个对象调用其对象时，python解释器会把这个对象作为第一个参数传递给self,所以开发者只需传递后面的参数即可。

  

## 1.5  str方法

str 方法用于打印具体的内容。

**python中当使用print输出对象的时候，只要自己定义了str（self)方法，那么就会打印从在这个方法中return的数据。**

```python
# python中当使用print输出对象的时候，只要自己定义了__str__（self)方法，那么就会打印从在这个方法中return的数据。

# 1第一种情况
# 定义类Car,加上str方法
class Car:
    
    def __init__(self,newWheelNum,newColor):
        self.wheelNum = newWheelNum
        self.color = newColor
    
    def __str__(self):
        msg = '嘿，我的颜色是'+self.color+'我有'+str(self.wheelNum)+'个轮胎'
        return msg # return 返回的是字符串
    def move(self):
        print("车再跑")

        
# 实例对象BMW
BMW = Car(4,"黑色")
print(BMW)


result :嘿，我的颜色是黑色我有4个轮胎
    

# 2 第二种情况
# 定义类Car,不加str方法

class Car:
    
    def __init__(self,newWheelNum,newColor):
        self.wheelNum = newWheelNum
        self.color = newColor
    def move(self):
        print("车再跑")

        
# 实例对象BMW
BMW = Car(4,"黑色")
print(BMW)

result :<__main__.Car object at 0x000002ACA42CD630>   
```



## 1.6 烤地瓜 面向对象方法应用

