1  函数

## 1.1 函数介绍

> 你可以定义一个由自己想要功能的函数，以下是简单的规则：
>
> - 函数代码块以 **def** 关键词开头，后接函数标识符名称和圆括号**()**。
> - 任何传入参数和自变量必须放在圆括号中间。圆括号之间可以用于定义参数。
> - 函数的第一行语句可以选择性地使用文档字符串—用于存放函数说明。
> - 函数内容以冒号起始，并且缩进。
> - **return [表达式]** 结束函数，选择性地返回一个值给调用方。不带表达式的return相当于返回 None

```python
def 函数名(参数):
	代码
	return [expression]		
```

#### 注意 ：函数分为库函数和自定义函数

* 函数在定义的时候进行文档说明

## 1.2 函数的参数

*  定义函数如果有参数,则调用的时候必须传入相应的值

```python
def add2Num(num1,num2):# num1,num2为形参，定义函数时小括号里面的参数为形参，实际作用接受传递过来的数据
	sum = num1+num2
    print(sum)
  

result = add2Num(5,6) # 5，6为实参
```

* 调用函数时参数的顺序

```python
def add2Num(num1,num2):
	sum = num1+num2
    print(sum)
    
add2num(num2=5,num1=6)
#若在调用时，写的参数和定义的时候接受的形参的顺序不一致，那么可以在传递的时候，指定是给哪个形参的。
```

## 1.3  函数的返回值

*  有时函数的作用需要进行返回值。则需要在函数最后写上return()

 ```python
def add2Num(num1,num2):
	sum = num1+num2
    return(sum)

result = add2Num(2,3)
# 将返回值用变量接受
 ```

## 1.4 四种类型函数

1. 无参数无返回值  

   >一般只是打印数据

```python
def displayMenu():
    # 菜单显示
    print("-"*30)
    print("名片管理系统 v1.1")
    print("1 添加名片")
    print("2 删除名片")
    print("3 修改名片")
    print("4 查询名片")
    print("5 遍历所有名片")
    print("6 退出系统")
    print("-"*30)

```

2. 无参数有返回值

   ```python
   def getChioce():
       # 选择
       selectedKey = input("请输入序号：")
       return int(selectedKey)
   ```

   

3. 有参数无返回值

   ```python
   def printAllinfo(nameListTemp):
       #接受传入的数据
       print("="*50)
       for temp in nameListTemp:
           print(temp)
       print("="*50) 
       
   ```

   

4.  有参数有返回值

   ```python
   def sumNums(num):
       i = 1
   	sum = 0
       while i <= num:
           sum += i
           i +=1
       return sum
   	
   ```

   

   

### 最终结果

```python
# 菜单显示
def displayMenu():   
    print("-"*30)
    print("名片管理系统 v1.1")
    print("1 添加名片")
    print("2 删除名片")
    print("3 修改名片")
    print("4 查询名片")
    print("5 遍历所有名片")
    print("6 退出系统")
    print("-"*30)
    
    
# 选择
def getChioce():
    selectedKey = input("请输入序号：")
    return int(selectedKey)   

#接受传入的数据
def printAllinfo(nameListTemp)：   
    print("="*50)
    for temp in nameListTemp:
        print(temp)
    print("="*50) 

# 主程序
nameList = []
i = 0
while i<10:
    # 打印提示
    displayMenu()
    #等待用户选择
    key = getChioce()
    
    if key == 1:
        print("您选择了添加名片功能")
        newName = input("请输入您的姓名 ：")
        nameList.append(newName)
    elif key == 5:
        printAllinfo(nameList)
    elif key == 3:
        pass
    else:
        print("输入有误， 请重新输入")
    i += 1
```



## 1.5 函数嵌套：

```python
def testB():
    print("------testB start")

def testA():
    print("-----testA start")
    testB()

testA()
```

## 1.6 定义函数和调用函数的顺序

* **定义函数放在调用函数的上面，也就是说函数定义写在最上面，主过程写在后面**



## 1.7 局部变量和全局变量

*  **局部变量**

  >在函数里面定义的变量，就叫做局部变量，它只在定义它的函数中有效，出了这个函数，它就没有了
  >
  >**形参也是局部变量**

*  **全局变量**

  >在函数的外边定义的变量就叫做 全局变量
  >
  >注意：**如果在函数中直接修改全局变量，将会产生异常**(**针对不可变类型数据**)
  >
  >
  >
  >如果真的需要修改，那么可以在函数中进行声明 
  >
  >**global  全局变量**

## 1.7 函数的应用(学生管理系统)

```python
# 1  先把整体的框架考虑清楚，搭框架，不要开始就考虑写函数

# 菜单显示
def showInfo():
    print('*' * 30)
    print("     学生管理系统   v 1.0")
    print("1：添加学生的信息")
    print("2：删除学生的信息")
    print("3：修改学生的信息")
    print("4：查询学生的信息")
    print("5：遍历学生的信息")
    print("6：退出系统")
    print('*' * 30)
    
# 1 添加用户信息    
def addNewStudents(studentTemp):
    name = input("请输入姓名：")
    stuId = input("请输入学号：")
    age = input("请输入年龄：")
    stuInfo = {}
    stuInfo['name'] = name
    stuInfo['id'] = stuId
    stuInfo['age'] = age
    studentTemp.append(stuInfo)
    
# 2 删除用户信息
def delStuInfo(studentTemp):
    delNum = int(input("请输入要删除的序号"))
    del studentTemp[delNum]
    
# 3  修改学生信息
def modifyStuInfo(studentTemp):
     ModifyNum = int(input("请输入要修改的序号"))
     strNum = int(input("请输入需要修改学生姓名或学生id或者学生年龄? 请输入1或者2或3"))
     if strNum == 1:
    	 strStu = input("请输入修改学生姓名：")
         (studentTemp[ModifyNum])['name'] =strStu
     elif strNum == 2:
         strStu = int(input("请输入修改学生id："))
        (studentTemp[ModifyNum])['id'] =strStu
     elif strNum == 3:
         strStu = int(input("请输入修改学生年龄："))
        (studentTemp[ModifyNum])['age'] =strStu
     else:
        print(输入有误，请重新输入：)
        
# 4  查询学生的信息
def queryStuInfo(studentTemp):
     queryNum = int(input("请输入要修改的序号"))
     queryDict = studentTemp[queryNum]
     print("姓名         id           年龄")
     print("%s           %s             %s"%\		      (queryDict['name'],queryDict['id'],queryDict['age']))
    
# 5 遍历用户信息   
def  traverseStu():
    print('*' * 30)
    print("接下来进行遍历所有学生信息:")
    print("姓名         id           年龄")
    for temp in students:
        print('%s        %s          %s' % (temp['name'], temp['id'], temp['age']))
# 定义一个列表，元素为字典用来存储多个学生信息
students = []
while True:
    # 1.0 先把功能列表进行显示给用户
    showInfo()
    # 1.1  提示用户选择功能
    # 1.2  获取用户的选择的功能
    key = int(input("请选择功能序号："))
    # 1.3 根据用户的选择，执行相应的功能。
    if key == 1:
        addNewStudents(students)
    elif key == 2:
        delStuInfo(students)
    elif key == 3:
    	modifyStuInfo(students）
    elif key == 4:
        queryStuInfo(students)
    elif key == 5:
        traverseStu()
    elif key == 6:
        result = input("确认退出系统吗？yes还是no")
        if result == yes:
        	break
    else:
        print("输入有误，请重新输入")
```

## 1.8 可变类型和不可变类型***

* **可变类型**

  * 列表  list
  * 字典  dict

* **不可变类型**

  * 数值类型 int,long,bool,float
  * 字符串 str
  *  元组 tuple

  

## 1.9  函数传递参数时的引用

* **如果在传递参数为可变类型时，那么在函数中就可以修改其值。如list,dict**

* **如果在传递参数为不可变类型时，那么在函数中就不能修改其值。如数值类型，字符串，元组**

### 注意：

**如果全局变量是可变类型，即列表或者字典，则可以在函数中直接进行修改，若全局变量是不可变类型，即数值类型，字符串以及元组，则不能直接修改**

* 为了和局部变量防止名字相同的问题，所以在全局变量前加上一个**g_变量名**

## 1. 10 函数返回多个值

1. 如果一个函数中有多个return，那么程序只执行任何一个return

   >程序执行到return ,那么就会立即结束当前的函数

2. 如果一个函数需要返回多个值，那么可以在最后return所有值。
3. 一般一个函数需要返回多个值，将返回值存在一个元组或者列表或者字典，然后return

```python
def test2():
    name='sjsj'
    myId = '22'
    age = '33'
    return,name,myId,age

result = test2()
print(result)

result:('sjsj','22','33')
    
    
def test3():
    name='sjsj'
    myId = '22'
    age = '33'
    listTest = [name,myId,age]
    return listTest

result = test3()
print(result)

result:['sjsj','22','33']
```

## 1.11  缺省参数

```python
def test(a,b="中国"):
    print(a)
    print(b)
    
test(10)#  b为缺省参数，则可不用写，一般缺省参数写在后面
result:10,中国
    
test(10,"其他国家")  
result:10,其他国家
```

* **不定长参数**  **再输入多个参数时用**

  **在形参最后一个加上***

  ```python
  def test(a,*b):
      print(a)
      print(b)
  test(1,2,3,4,4)
  
  result:
      1
      (2,3,4,4) #输出为元组
  
  ```

  

* **有时在最后不定长参数，且传入名字**

  ```python
  def test2(a,*b,**c):  # *b,**c为可传递参数，可不传递
      print(a)
      print(b)
      print(c)
  test2(1,22,33,5,m=23,n=56)
  
  result:1
         (22,33,5)
          {"m":23,"n":56}  
  ```

  

## 1.12 递归

*  **函数自己调用自己** (注意截至)

  ```python
  def test1(num):
      if num > 1:
          result=num+test1(num-1)
      else:
          result = 1
      return result
  result = test1(3)
  print(result)
  
  
  result:6
  ```

  



### 特殊案例：a+=a和a=a+a的区别

**这段代码说明的是，+=属于原地操作，不会修改列表首地址，类似于列表append()方法，而... = ...+...这样的写法是创新一个新对象，会修改列表首地址。**

```python
testList = [10, 4]
print(testList)
print(id(testList))
testList += testList
print(testList)
print(id(testList))

print('----' * 50)
testList2 = [10, 4]
print(testList2)
print(id(testList2))
testList2 = testList2 + testList2 #这块坐标相当于新定义一个变量 testList2，将等式右边赋值给左边。
print(testList2)
print(id(testList2))




result:[10, 4]
2730542916168
[10, 4, 10, 4]
2730542916168
--------------------------------------------------
[10, 4]
2730542916232
[10, 4, 10, 4]
2730543416136

#这段代码说明的是，+=属于原地操作，不会修改列表首地址，类似于列表append()方法，而... = ...+...这样的写法是创新一个新对象，会修改列表首地址。

```

