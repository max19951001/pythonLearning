# 1. 字符串

**定义字符串：双引号或者单引号中的数据，即字符串。**

## 1.2 字符串输入和输出

**输出：**

``` python
name = "max"
print(name)
print("max")

print(name,end="")
print("max")
```

 **输入：**

```python
username = input("请输入用户名 :")
print("用户名为 ：%s"% username)
```

## 1.3  下标和切片

列表和元组支持下标，同样的字符串也支持下标索引，字符串可以看作是字符数组。

**下标：**

```python
name="max"
print(name[0])
print(name[1])
print(name[2])

result: 'm','a','x'

```

**切片：**对操作的对象截取其中一部分的操作。

​		语法：[起始：结束：步长] 

* 注意：切片为左闭右开区间。

```python
name="max"
print(name[0:2])
print(name[-1])
print(name[1:])
print(name[-1:-3:-1])
result:'ma','x','ax','xa'
```

## 1.4 字符串操作

myStr = ”hello world itcast and itcastcpp“

1. find() 

   寻找指定字符

   ````python
   myStr = 'hello world itcast and itcastcpp'
   result = myStr.find('it')
   result = myStr.find('itcast',14,30)
   
   result:12,23
   
   ````

   

2. index()

   > **index()和find()类似，不过find()找不到满足条件的直接返回-1，index()找不到满足条件直接报错**

   **注意：rfind()和rindex()分别从右边开始，find()和index()从左边开始**

   

3. count()

   返回str在start和end之间 在mystr里面出现的次数

   ```python
   语法：myStr.count(str,start = 0,end = len(mystr))
   
   myStr = 'hello world itcast and itcastcpp'
   myStr.count("itcast")
   
   result:2
   ```



4. replace()

   将myStr中的str1替换成str2,如果count指定，则替换不超过count次。

   ```python
   语法：myStr.replace(str1,str2,myStr.count(str1))
   
   myStr = 'hello world itcast and itcastcpp'
   result = myStr.replace("it","IT")
   ```

   

5. split()

   以str 为分割符切片myStr,如果maxsplit有指定值，则仅分割maxsplit个字符串

   ```python
   语法：myStr.split(" ",maxsplit)
   
   myStr="1,2,3"
   result = myStr.split(",")
   result = myStr.split(",",1)
   
   result:['1','2,'3'] ['1','2,3']
   
   ```



6. capitalize()

   把字符串的第一个字符大写

   ```python
   语法： myStr.capitalize()
   
   mystr = 'hello world'
   result = mystr.capitalize()
   
   result: 'Hello world'
   ```

   

7. title()

   把字符串的每个单词首字母大写

   ```python
   语法 ：myStr.title()
   
   mystr = "hell0 world"
   result = mystr.title()
   
   result:'Hello World'
   ```

   

8. lower()和upper()

   lower()把mystr中所有大写字符转为小写,upper()将所有小写转为大写

   ```python
   语法： myStr.lower()
   
   mystr = "HEKK word;"
   result = mystr.lower()
   result = mystr.upper()
   
   result:'hekk word;', 'HEKK WORD;'
   ```

   

9. startswith()和endswith()

   检查字符串是否以obj开头或结尾，是则返回True,否则返回False

   ```python
   语法： mystr.startswith(obj)或mystr.endswith(obj)
   
   mystr = 'hello world'
   result = mystr.startwith('he')
   result = mystr.endswith('l)
                           
   result:True,False          
   ```

   

10. ljust()和rjust()和center()

    返回一个原字符串左对齐，并使用空格填充至长度width的新字符串

    或返回一个原字符串右对齐，并使用空格填充至长度width的新字符串
    
    或返回一个原字符串居中，并使用空格填充至长度width的新字符串
    
    ```python
    语法：myStr.ljust(width)或myStr.rjust(width)
    
    mystr = "hello"
    result = mystr.ljust(10)
    result = mystr.rjust(10)
    result = mystr.center(11)
    
    result:'hello     ' ,'     hello'  ,'   hello   '
    
    ```
    
    

11. lstrip()和rstrip()和strip()

     lstrip(),rstrip(),strip()删除mystr中左边,右边以及中间的空格

    ```python
    语法：myStr.lstrip()或myStr.rstrip()或myStr.strip()
    
    mystr = '   hello   '
    result = mystr.lstrip()
    result = mystr.rstrip()
    result = mystr.strip()
    
    result:'hello   ','   hello','hello'
    ```

    

12. partition()和rpariition()

    把mystr以str分割成三部分，str前，str和str后,rpartition()从右开始切

    ````python
    语法：mystr.partition(obj)和mystr.rpartition()
    
    myStr = 'hello world itcast and itcastcpp'
    result=myStr.partition("itcast")
    result=myStr.rpartition("itcast")
    
    result: ('hello world  ','itcast','  and itcastcpp')
            ('hello world itcast and  ','itcast','cpp')
    ````

    

13. splitlines()

    按照行分隔符，返回一个包含各行作为元素的列表

    ```python
    语法：mystr.splitlines()
    
    mystr = 'hello\nworld'
    result = mystr.splitlines()
    
    result:['hello','world']
    ```

    

14. isalpha()和isdigit()和isalnum()

    isalpha()如果字符串里面都是字母，返回True，否则返回False

    isdigit()如果字符串里面都是数字，返回True,否则返回False

    isalnum()如果字符串里面都是字母或者数字，返回True,否则返回False

    ```python
    语法：mystr.isalpha()或mystr.isdigit()或mystr.isalnum()
    ```

    

15. isspace()

    判断字符串是否**只是**空格，是返回True,否则返回False

    

16. join()

    mystr中每个字符后面插入str,构造出一个新的字符串

    ```python
    语法：mystr.join(str)
    
    str = ' '
    li = ['my','name','is']
    result = str.join(li)
    
    result = 'my name is'
    ```

    

# 2. 列表

## 2.1   列表基本介绍

* 定义列表：list=["sjsj",1,"sjsj"]

* 空列表：nulllist=list()

* 访问列表内容：print(list[0])

## 2.2   列表循环遍历

1. **for 循环**

````python
nameList = ['xiaowang','xiaozhang','xiaohua']

for name in nameList:
	print(name)

result: xiaowang
		xiaozhang
		xiaohua
````



2. **while 循环**

```python
nameList = ['xiaowang','xiaozhang','xiaohua']

length = len(nameList)
i=0
while i<length:
	print(nameList[i])

result: xiaowang
		xiaozhang
		xiaohua    
```

## 2.3 列表“增”操作 *********

**增加元素(append,extend,insert)**

* **append**(仅仅在列表后面加上新的元素)

  ```python
  names = ['zhangsan','lisi']
  for temp in names:
      print(temp)
  print('-'*30)
  name = "baoqiang"
  names.append(name)
  for temp in names:
  	print(temp)
  ```

* **insert(index,object)** （在指定位置插入元素）

  ```python
  names = ['zhangsan','lisi']
  for temp in names:
  	print(temp)
  name = 'baoqiang'
  names.insert(1,name)
  for temp in names:
  	print(temp)
  ```

* **extend** (通过extend可以将另一个集合中的元素逐一添加到列表中)

  ```python
  a = [1,2]
  b = ['a','b','c']
  a.extend(b)
  print(a)
  a.append(b)
  print(a)
  
  
  result:[1,2,'a','b','c']
         [1,2,'1','b','c',['a','b','c']]
  ```

## 2.4 列表“改”操作

**注意：**修改元素的时候，通过下标来确定要修改的是哪个

 ```python
names = ['aaa','b','cc']
names[1] = 'bbbb'
print(names)

result: ['aaa','bbbb','cc']
 ```

## 2.5 列表“查”操作*******

**查找元素(in，not in,index,count)**

* in,not in （存在则返回True,否则返回False,或不存在返回True,否则返回False）

  ```python
  fileNames = ['zhangsan','lisi']
  findname = 'lisi'
  if findname in fileNames:
  	print("存在")
  else:
  	print("不存在")
      
  result: 存在
  ```

* index和count （与字符串中的用法相同）

  ```python
  nums= ['a','b','c','d']
  result = nums.index('a',0,3)# 注意是左闭右开区间，返回结果为索引值。
  print(result)
  result = a.count('a')
  print(result)
  
  result:0,1
  ```

## 2.6  列表"删"操作***

**删除元素 (del,pop,remove)** 

* del  （通过下标删除）

  ```python
  fileNames = ['lihuan','dazhao','laojiang']
  del fileNames[1]
  print(fileNames)
  del fileNames # 删除整个列表
  result:['lihuan','laojiang']
  ```

  

* pop  (从后面一个开始删除)

  ```python
  fileNames = ['lihuan','dazhao','laojiang']
  fileNames.pop()
  print(fileNames)
  
  result:['lihuan','dazhao']
  ```

* remove (针对元素删除)

  ```python
  fileNames = ['lihuan','dazhao','laojiang']
  fileNames.remove('lihuan')
  print(fileNames)
  
  result:['dazhao','laojiang']
  ```

  

## 2.7  列表嵌套综合应用

1 现在有三个办公室，现在有8各老师等待工位的分配，请随机进行分配。

```python
import random
# 1 定义列表，用来存储8位老师的名字
teachers = ['xiaoming','xiaohua','xiaoli','xiaozhang','xiaosong',\
           'xiaozhao','xiaoliu','xiaowu','xiaona']
# 2 定义列表，存储3个空的办公室
offices = [[],[],[]]
#3 循环进行分配
for name in teachers:
    index = random.randint(0,2)
     while len(offices[index])<4:
    	offices[index].append(name)
   
# 4输出最终结果
i = 1
for room in offices:
    print("办公室%d"%i)
    for teacherName in room:
        print(teacherName)
    i+= 1
    
```



# 3.  元组

**与列表定义的差别在于用“（）"将元素括起来**

* 元组不能更改列表的内容,所以一般存储不能修改内容的数据

```python
tuple1 = (”127",'sjs')
tuple1[0] = '102'

result:异常，不能更改元组的值。
```

* #### 注意事项

  * 元组中只包含一个元素时，需要在元素后面加上逗号

  ```python
  tup1 = (50,)
  ```

  * 元组中元素不可删除，但可以删除整个元组

    ```python
    tup1 = (50,)
    del tup1
    ```

    

    

# 4 .  字典

子典是另一种可变容器模型，且可存储任意类型对象。

字典的每个键值 **key=>value** 对用冒号 **:** 分割，每个**键值**对之间用逗号 **,** 分割，整个字典包括在花括号 **{}** 中 ,格式如下所示：

```python
d = {key1 : value1, key2 : value2 }
```

字典的键值一般不会修改。

* **空字典：d = {}**

* 字典的值访问是通过 键来访问

  ```python
  dict = {'name':"max","age":19,"sex","male"}
  print(dict["name"])# 访问对应的值
  dict["name"] = "rose"# 修改键对应的值
  dict["weight"]=180 # 增加键值
  
  dict["hello"] # 访问没有键的元素就会报错
  dict.get("hello") # 没有取出值，但不会报错
  dict.get("hello",172) # 没有hello键值，则会自动赋值为172
  ```

  

* **删除字典元素**

  **del**命令

  ```python
  dict = {'name':"max","age":19,"sex","male"}
  del dict['name'] #删除键是'name'的条目
  del dict #删除字典
  
  dict.clear() # 清空词典所有条目
  ```

  

* ### 注意事项

  * 不允许同一键出现两次。创建时如果同一个键被赋值两次，前一个值会被覆盖

  * 键必须不可变，所以可以用数字，字符串或元组充当，所以用列表就不行

    ```python
    dict = {['name']:'max','age':19}
    
    result：异常
    Traceback (most recent call last):
    TypeError: list objects are unhashable
    ```

    

* ### 字典常见操作

  * len() 测试字典中键值对的个数

  * keys() 返回键的列表

  * values( ) 返回values值

  * items() 返回一个包含所有(键，值)元组的列表

    ```python
    dict = {"name":"max","age":24}
    temp = dict.items()
    for key,value in temp:
        print(key,value)
    ```

