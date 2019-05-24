

# 1.  if  判断语句

## 1.1  if 语句：

> if 要判断的条件：
>
> ​		条件成立时，要做的事情

## 1.2 if -else 语句

> if 条件：
>
>   ​	满足条件做的事
>
> else：
>
> ​		 不满足条件时做的事

**注意**：else不能单独存在，必须和if对应。

## 1.3 elif 语句

> if 条件：
>
> ​	满足条件执行
>
> elif 条件：
>
> ​	执行
>
> else:
>
> ​	不满足条件执行

## 1.4  if 嵌套

> if 条件1：
>
> 执行满足条件内容
>
> ​		if 条件2：
>
> ​				执行

**注意：if 嵌套表示为：满足if 1之后才能执行 if 2** 	

# 2. while  循环语句

**例如：**

> i = 0
>
> while i<10:
>
> ​	print("gg")
>
> ​    i+=1

## 2.1 while 循环嵌套

> while 条件1：
>
> ​	执行。。
>
> ​		while 条件2：
>
> ​				执行。。。

# 3. for 循环

**结构： for 变量 in  xxx :**        

**xxx一般为包含多个元素的值，xxx为迭代对象。如字符串，列表**

> name="DongGe"
>
> for temp in name:
>
> ​	 print("%s"%temp)

# 4 break 和**continue**

break: 直接终止循环

continue:终止本次循环，紧接着进入下一循环

### 注意点：

* **break/continue 只能用在循环中，除此以外不能单独使用。for或者while循环**
* **break/continue在嵌套循环中，只能对最近的一层循环有用**

