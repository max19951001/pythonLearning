# 1.  字符串

**定义字符串：双引号或者单引号中的数据，即字符串。**

## 1.2 字符串输入和输出

**输出：**

``` python
name = "max"
print(name)
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
   result = myStr.find('itcast',14,20)
   
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

    ```
    语法：mystr.join(str)
    
    str = ' '
    li = ['my','name','is']
    result = str.join(li)
    
    result = 'my name is'
    ```

    

