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

