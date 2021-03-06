@[TOC](目录)

# 前言

&emsp;&emsp;经过一个月左右的时间，终于学完了python的基础部分的知识。现将总结笔记整理成博客分享出来，希望能够帮助到有需要的人。废话不多说，上菜！

# 注意

&emsp;&emsp;本篇文章是在默认已经学过C语言和Java语言的前提下总结的，因只重点总结Python与C、Java不同或易错知识点。红线部分为重点或与C、Java不同之处。尚未学习过C、Java的小伙伴们可以先自学C语言和Java，在我看来对比C语言和Java来学习python，效果可能会更好！在此提供一篇本人之前学习Java的笔记：[点我点我](https://blog.csdn.net/GuoQiZhang/article/details/89784677)

# 该不该学习Python（个人感受，纯属胡言论语）

&emsp;&emsp;通过一周左右的学习，让我感受到了这门语言的一个最大特点：<font color=#0422ff size=5 face="黑体">流氓</font>，这是我目前能找到对它最好的修饰词了。但这绝对不是在贬低Python，反而是在赞扬它。作为一门前端语言，它集C、Java语言中的精华于一身。很好的发挥了前端语言<font color=#ff00 size=3 face="宋体">重视简洁高效，轻视执行速度</font>的特点，就像那句：人生苦短，我用Python！那么该不该学习Python呢？我的建议如下：
 1. 如果你只是<font color=#ff00 size=3 face="宋体">单纯的想搞事情</font>，想做出一个作品或者想完成某个项目，又或者对编程有兴趣想尝试，优先学习Python能够快速的达到你的目的。
 2. 如果你将来想<font color=#ff00 size=3 face="宋体">从事编程这类计算机的相关工作或者编程是你狂热的兴趣爱好</font>，学习C和C++将会使你的编程道路走的更深更远，算的上是IT必修课程之一，它能有效的帮助你了解和理解计算机软硬件的工作方式和软硬件是如何协同工作的，它们工作的思维方式是什么，让你更懂计算机的想法，也能帮助你更快的学习其他的编程语言，万变不离其宗，其中的道理自然可以互通，也为你的学习提供了实用高效的参照物。
 
# 基础知识：Python 的数据存储机制

&emsp;&emsp;每个编程语言都有其各自的存储机制，依个人愚见，学习任意一门语言，一定要了解其数据存储机制，学习Python也不例外。在学习Python时你会发现，它和C语言、Java在基础知识方面最大的不同就是python在使用变量时不用先声明再使用，而是想用某个变量时直接拿来用，这就决定了它的数据存储方式有些不同。对于python，一切变量都是对象，变量的存储采用C语言中**指针**的思路来进行设计，即变量存储的只是变量值的内存地址，而不是变量值本身。关于python数据储存的详细过程推荐这篇文章  [https://blog.csdn.net/u014665013/article/details/85787884](https://blog.csdn.net/u014665013/article/details/85787884)

# 第一章 Python基本语法

## 1.1 Python 数据类型

### <font color=#0422ff size=4 face="宋体">1.1.1 数值类型</font>

（1）整型（int）

  &emsp;&emsp;&emsp; Python3版本中只有一种int，取消了Python2中的long类型。

（2）浮点型（float）

&emsp;&emsp;&emsp; 科学技术法表示：2.78E2, Python解释器结果：278.0

（3）复数（complex）   

&emsp;&emsp;&emsp;表示方法：`a+bj`或`a+bJ`或`complex(a,b)`， Python解释器结果：`（a+bj）`
<font color=#ff00 size=3 face="黑体">总结：Python数据类型是不允许改变的，如果改变，意味着将重新分配内存空间，也表明Python是强类型的动态脚本语言，关于语言类型的分类可以参考：</font> [https://blog.csdn.net/xhg_wandering_soul/article/details/80796192](https://blog.csdn.net/xhg_wandering_soul/article/details/80796192)

### <font color=#0422ff size=4 face="宋体">1.1.2 字符串</font>

&emsp;&emsp;Python将单字符和字符串合并，单引号与双引号均可使用，且效果一致。当想在字符串中嵌套字符串时内外引号需要不同（’I am”bom”!’和”I am’bom’!”）

### <font color=#0422ff size=4 face="宋体">1.1.3、布尔类型</font>

&emsp;&emsp;只有True和False两种类型，与或非运算同C、Java。在Python中数字0、0.0、空字符串、空元组、空序列、空字典等一切空值均为False，其它值认为True，这和C语言一致，和Java不同。在Java中布尔类型为单独数据类型，不能与其他类型混合使用，例如

```python
      if(1) // error
```

### <font color=#0422ff size=4 face="宋体">1.1.4、空值</font>

&emsp;&emsp;使用None表示，不支持任何运算，未指定返回值的函数自动返回None。和C语言、Java一致。

<font color=#ff000 size=4 face="黑体">* Python独有特点：</font>
1. python中没有`++`或`--`的运算符
2. `/`是真正意义上的除法；`//`是C语言中的地板除法（floor）例子：

```python
	a=10
	b=3
	print(a/b)
	print(a//b)
	#结果
	3.3333333333333335
	3
```

 3. `**`表示幂运算，例：

```python
	a=10
	b=2
	print(a**b)
	#结果
	100
```
 4. `3 < 4 < 5` 等同于`3<4 and 4<5`

 5. 运算符优先级：从上到下，从左到右逐次降低：
 
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190828220220850.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)

 6. Python使用`断言（assert）`来检查错误点：如果其后面的表达式为假时则抛出异常。例如：
```python
	assert 3>4
	#结果：
	AssertionError    Traceback (most recent call last)
	<ipython-input-8-ccf53c07db24> in <module>()
	----> 1 assert 3>4
	
	assert 3<4
	#结果（无）
```
## 1.2  Python 序列数据结构

### <font color=#0422ff size=4 face="宋体">1.2.1、列表（List） ——元素可变（打了激素的数组）</font>

**（1）创建**：

```python
     方法(1)：  list1=['中国','美国',2019,2.87]
     方法(2)：  a=list('中国')
     #list()内部最多输入一个字符串，且真实的存储是a=[‘中’,’国’]。
```

**（2）访问（索引）**：


&emsp;&emsp;类似数组采用截取（切片）的方式，eg：`list1[0]，list[1:5]`  左闭右开。

&emsp;&emsp;A:跳跃取值：`List1[a:b:c]`  其中a为切片起点，b为切片终止点，c为跳转间距。

&emsp;&emsp;B:逆序：`List1[::-1]`。

**（3）添加**：直接使用`list1[a]=b，list[a:b]=[c:d]`等。

&emsp;&emsp;A列表嵌套：

```python
    list1=['中国', '美国', 2019 , 2.87] 
    list1[0]=[1,2,3]
    结果：list1=[[1,2,3] , '美国' , 2019 , 2.87]。
```

&emsp;&emsp;B尾部添加：`list1.append(4)`：括号内只能加一个。
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;  `list1.extend(a)`：a为列表。

&emsp;&emsp;C中间插入：`list1.insert(a,b)`：a为插入的位置；b为插入的值

**（4）合并**：`a=[1,2,3]  b=[4,5,6]`  `a+b` 或`a.extend(b)` 完成合并，`a+b`不改变a,b的值，`a.extend(b)`修改a的值。

**（5）删除**：
&emsp;&emsp;A按位置删除元素：`del list1[2] 、list1.pop(2)`  pop()函数无参数时删除尾部元素。

&emsp;&emsp;B按元素值删除：`list1.remove(“a”)`

**（6）判断**：`a in list1` ：返回True说明a在list1中，False说明a不在list1中。

**（7）排序**：`list1.sort()`  默认升序
&emsp;&emsp;&emsp;&emsp;&emsp;`list1.reverse()`：将列表整体反转。

**（8）长度**：`len(list1) 、  list1.count(a)`：查询a元素在列表中出现的次数，

**（9）位置**：`list1.index(a)`：查询a在列表中首次出现的位置。
&emsp;&emsp;&emsp;&emsp;&emsp;`list1.index(a,b,c)`：表示查询值a在列表中从位置b到位置c之间首次出现的位置。区间依然是`[b,c)`。

**（10）分片**：`list1[a:b]`：取list1中[a,b)中的元素。

**（11）列表生成式**：`range(a,b)`：输出从a到b-1的所有值，使用`list(range(a,b))`,生成列表。

&emsp;&emsp; A  for循环：`[x*x for x in range(1,11)]` 

&emsp;&emsp;  B  if判断：`[x*x for x in range(1,11) if x%2==0]` 

**（12）列表的比较**：两个列表比较时默认比较第一个元素值的大小

**（13）计数**：`list1.count(a)`：表示a在列表中出现的次数

```python
	list1 = [123,456]
	list2 = [234,123]
	print(list1>list2)

	#结果
	False
```
    
### <font color=#0422ff size=4 face="宋体">   1.2.2、元组(tuple)——元素不可变（带上了枷锁的列表）</font>

**(1)特点**：与列表相似，不同是使用**小括号**，且元素不能修改。

**(2)创建**：

```python
    方法1： tuple1 = (1,2,3,"中国") 或 tuple1 = (1,)  
    方法2： tuple1 = "中国","英国",100,200     #（可以省略括号，逗号才是关键）
```

 &emsp;&emsp;  &emsp;当只有单元素时，为了与单变量区别，在元素后面要加逗号。

**(3)连接/截取（切片）**：与列表近似

```python
	tuple1=(1,2,3)
	tuple2 = (4,5,6)
	tuple1 =tuple1 + tuple2
	#结果
	(1, 2, 3, 4, 5, 6)
```

**(4)删除**：不能删除元素，只能删除整个元组：`del tuple1`

**(5)字符串、列表、元组转换**：`str()、list()、tuple()`

**(6)查看元组类型的函数**： `dir(tuple)` 例如：

```python
dir(tuple)
#结果
['__add__',
 '__class__',
 '__contains__',
 '__delattr__',
 '__dir__',
 '__doc__',
 '__eq__',
 '__format__',
 '__ge__',
 '__getattribute__',
 '__getitem__',
 '__getnewargs__',
 '__gt__',
 '__hash__',
 '__init__',
 '__init_subclass__',
 '__iter__',
 '__le__',
 '__len__',
 '__lt__',
 '__mul__',
 '__ne__',
 '__new__',
 '__reduce__',
 '__reduce_ex__',
 '__repr__',
 '__rmul__',
 '__setattr__',
 '__sizeof__',
 '__str__',
 '__subclasshook__',
 'count',
 'index']
```


**(7)字符串常用方法**：

|方法|解释|
|-|:-|
|capitalize()|把字符串的第一个字符改为大写|
|casefold()|把整个字符串的所有字符改为小写|
|center(width)|将字符串居中，并使用空格填充至长度 width 的新字符串|
|count(sub[, start[, end]])|返回 sub 在字符串里边出现的次数，start 和 end 参数表示范围，可选。|
|encode(encoding='utf-8', errors='strict')|以 encoding 指定的编码格式对字符串进行编码。|
|endswith(sub[, start[, end]])|检查字符串是否以 sub 子字符串结束，如果是返回 True，否则返回 False。start 和 end 参数表示范围，可选。|
|expandtabs([tabsize=8])|把字符串中的 tab 符号（\t）转换为空格，如不指定参数，默认的空格数是 tabsize=8。|
|find(sub[, start[, end]])|检测 sub 是否包含在字符串中，如果有则返回索引值，否则返回 -1，start 和 end 参数表示范围，可选。|
|index(sub[, start[, end]])|跟 find 方法一样，不过如果 sub 不在 string 中会产生一个异常。|
|isalnum()|如果字符串至少有一个字符并且所有字符都是字母或数字则返回 True，否则返回 False。|
|isalpha()|如果字符串至少有一个字符并且所有字符都是字母则返回 True，否则返回 False。|
|isdecimal()|如果字符串只包含十进制数字则返回 True，否则返回 False。|
|isdigit()|如果字符串只包含数字则返回 True，否则返回 False。|
|islower()|如果字符串中至少包含一个区分大小写的字符，并且这些字符都是小写，则返回 True，否则返回 False。|
|isnumeric()|如果字符串中只包含数字字符，则返回 True，否则返回 False。|
|isspace()|如果字符串中只包含空格，则返回 True，否则返回 False。|
|istitle()|如果字符串是标题化（所有的单词都是以大写开始，其余字母均小写），则返回 True，否则返回 False。|
|isupper()|如果字符串中至少包含一个区分大小写的字符，并且这些字符都是大写，则返回 True，否则返回 False。|
|join(sub)|以字符串作为分隔符，插入到 sub 中所有的字符之间。|
|ljust(width)|返回一个左对齐的字符串，并使用空格填充至长度为 width 的新字符串。|
|lower()|转换字符串中所有大写字符为小写。|
|lstrip()|去掉字符串左边的所有空格|
|partition(sub)|找到子字符串 sub，把字符串分成一个 3 元组 (pre_sub, sub, fol_sub)，如果字符串中不包含 sub 则返回 ('原字符串', '', '')|
|replace(old, new[, count])|把字符串中的 old 子字符串替换成 new 子字符串，如果 count 指定，则替换不超过 count 次。|
|rfind(sub[, start[, end]])|类似于 find() 方法，不过是从右边开始查找。|
|rindex(sub[, start[, end]])|类似于 index() 方法，不过是从右边开始。|
|rjust(width)|返回一个右对齐的字符串，并使用空格填充至长度为 width 的新字符串。|
|rpartition(sub)|类似于 partition() 方法，不过是从右边开始查找。|
|rstrip()|删除字符串末尾的空格。|
|split(sep=None, maxsplit=-1)|不带参数默认是以空格为分隔符切片字符串，如果 maxsplit 参数有设置，则仅分隔 maxsplit 个子字符串，返回切片后的子字符串拼接的列表。|
|splitlines(([keepends]))|在输出结果里是否去掉换行符，默认为 False，不包含换行符；如果为 True，则保留换行符。|
|startswith(prefix[, start[, end]])|检查字符串是否以 prefix 开头，是则返回 True，否则返回 False。start 和 end 参数可以指定范围检查，可选。|
|strip([chars])|删除字符串前边和后边所有的空格，chars 参数可以定制删除的字符，可选。|
|swapcase()|翻转字符串中的大小写。|
|title()|返回标题化（所有的单词都是以大写开始，其余字母均小写）的字符串。|
|translate(table)|根据 table 的规则（可以由 str.maketrans('a', 'b') 定制）转换字符串中的字符。|
|upper()|转换字符串中的所有小写字符为大写。|
|zfill(width)|返回长度为 width 的字符串，原字符串右对齐，前边用 0 填充。|
### <font color=#0422ff size=4 face="宋体">   1.2.3、字典（dict）——键唯一且无序</font>
    
**(1）创建**：由键值对（key => value）组成，用花括号{}表示。eg: dict1={key1:1,key2: 2} 

 &emsp;&emsp; <font color=#ff00 size=3 face="黑体">注：key必须唯一不唯一时后者的value覆盖前者的value，value不必。Key不可修改，所以只能用数字、字符串、元组表示；而value可以修改，可以使用任何数据类型。创建空字典：dict1={}</font>

**(2)访问（查询）**：

   &emsp;&emsp;     A：`dict1[key]`，查询指定的value，键不存在时报错。

   &emsp;&emsp;     B：`dict1.values()` 返回所有value

   &emsp;&emsp;     C：`dict1.items()` 把每对键值组成一个元组，放在一个列表中显示

**(3)修改字典**：添加和修改value时均可使用dict1[key]=’value’

**(4)删除**：  

&emsp;&emsp;&emsp;&emsp; `del  dict1[key]` ：删除指定键值

&emsp;&emsp;&emsp;&emsp; `dict1.clear()` ：清空字典

&emsp;&emsp;&emsp;&emsp; `del dict1`  ：删除字典

**(5)判断**：使用in返回值判断字典是否存在键   eg: `“key1” in dict1` 

```python 
	dict1 = {1:'one',2:'two',3:'three'}
	print(dict1[2])
	list(dict1.items())
	#结果
	'two'
	[(1, 'one'), (2, 'two'), (3, 'three')]
```

### <font color=#0422ff size=4 face="宋体">   1.2.4、集合（set）———无序不重复</font>

**（1）创建**：使用大括号{} 或set()函数。注：创建一个空集合时必须使用set()函数。

```python
    方法1：set1={1,2,3,4,5} 
    方法2：set1=set(空/元组/列表)
```
**（2）查询访问**：in使用方法与字典一致

**（3）集合运算**： 

&emsp;&emsp; 	A：差：’-’

&emsp;&emsp;  B：并：’|’

&emsp;&emsp;    C：交：’&’

&emsp;&emsp;   D：异或：’^’

**（4）添加**：
&emsp;&emsp; 使用 `add` 或`remove`增加或删除某个元素

```python 
	set1={1,2,3,4,5}
	2 in set1
	set1.add(8)
	print(set1)
	set1.add((10,22))
	print(set1)
	set1.remove(2)
	print(set1)
	#结果
	True
	{1, 2, 3, 4, 5, 8}
	{1, 2, 3, 4, 5, 8, (10, 22)}
	{1, 3, 4, 5, 8, (10, 22)}
```
## 1.3  Python 控制语句

<font color=#ff00 size=3 face="黑体">（1）、Python使用’#’做注释符,和C、Java的’/’用法相同，但python没有多行注释符，只能用多行#代替</font>

<font color=#ff00 size=3 face="黑体">（2）、Python不用大括号、begin等符号区分代码块，而是使用缩进来区分，换行使用’\’。</font>

### <font color=#0422ff size=4 face="宋体">   1.3.1、选择结构 </font>

   &emsp;&emsp; if....else 和if....elif.....else：使用方法与C、Java相似，区别：多了elif关键字；选择条件不用小括号，且在条件后面加冒号。Eg：
   

```python
    if True: 
   		........
    else:
   		........
```
### <font color=#0422ff size=4 face="宋体"> 1.3.2、循环结构  </font>

 &emsp;&emsp;  Python只提供for 和while两种循环，不使用do......while。

 &emsp;&emsp; A：while：使用方法：
 

```python
        while 判断条件:
              循环体
```

 &emsp;&emsp; B：for： 使用方法：

```python
        for 循环索引值 in 序列
             循环体
```

&emsp;&emsp; C：continue与break：使用方法和C、Java相同

### <font color=#0422ff size=4 face="宋体">   1.3.3、断言 </font>
 &emsp;&emsp; 在开发一个程序时候，与其让它运行时崩溃，不如在它出现错误条件时就抛出异常（返回错误）。这时候断言`assert` 就显得非常有用。assert的语法格式：、

```python
  	a_str = "hello world!"
	assert type(a_str) == str
	assert type(a_str) == int
	assert 1
	assert 0
	#结果
	1：
	（无）
	2：
	AssertionError    Traceback (most recent call last)
	<ipython-input-9-40bbc368ad99> in <module>()
	----> 1 assert type(a_str) == int
	AssertionError:
	3：
	（无）
	4：
	AssertionError     Traceback (most recent call last)
	<ipython-input-10-34d6bc1d929c> in <module>()
	----> 1 assert 0
	AssertionError: 
```

由例子可知：断言表示的含义是：如果断言后面的条件为1或真，则不报错，否则报错。
## 1.4  Python 函数与模块

### <font color=#0422ff size=4 face="宋体">   1.4.1、函数的定义 </font>

```python
    def  函数名（函数参数）:
           函数体
	    return 表达式或者值
```

例如

```python
    def hello()
            print("hello,word!")
            return 0
```

&emsp;&emsp;函数参数不用指定参数类型，因为python中的变量是动态脚本语言。函数定义的采用缩进方式划分。return返回值可选，且可以在任意地方出现，执行return后函数结束。

### <font color=#0422ff size=4 face="宋体">   1.4.2、函数的形参和实参</font>
&emsp;&emsp;首先先说一下**函数文档**：python中在函数第一行使用引号`''` 来定义函数文档，和注释不同的是可以调用函数内置属性`.__doc__`来查看文档。例如：

```python
	def func():
		'这是函数文档！'
	func.__doc__

	#结果
	'这是函数文档！'
```
&emsp;&emsp;接着说一下**关键字参数**，它是指在传参数时可以把形参的名字和值直接联系起来，而解决了传参时顺序不一致而产生错误的问题；例如：

```python
	def func(name,words):
		print(name + '说：' + words)
	func('鲁迅','工程小猿写的博客很不错！')
	func(words = '工程小猿写的博客很不错！',name = '鲁迅')
	#结果
	鲁迅说：工程小猿写的博客很不错！
	鲁迅说：工程小猿写的博客很不错！
```
&emsp;&emsp;接着说一下**收集参数**，当传入的参数过多或者不定时可以使用收集参数。关键字为：`*params` 类似于C语言传入带指针的数组进行操作：

```python
	def func(*params):
		print('收集参数的长度：', len(params))
		print('第二个参数是：' , params[1])
	func(1,2,3,4)
	#结果	
	收集参数的长度： 4
	第二个参数是： 2
```
```python
	def func(*p,name):
		print('收集参数的长度：', len(p))
		print('第二个参数是：' , p[1])
		print('name：' , name)
	func(1,2,3,name = 4)
	#结果	
	收集参数的长度： 3
	第二个参数是： 2
	name： 4
```

### <font color=#0422ff size=4 face="宋体">   1.4.3、返回值 </font>
&emsp;&emsp;因为python属于动态数据类型的语言，所以在函数定义时是不需要指明返回值的，并且可以省略返回值，返回多个值（返回多个值时使用元组或列表）：

```python
    def func():
    	return 1,2,3
    func()
    #结果
    1,2,3
```
### <font color=#0422ff size=4 face="宋体">   1.4.4、全局变量与局部变量 </font>
&emsp;&emsp;和C语言、Java一样，全局变量全局可见，而局部变量只在函数内部有效。由于python变量不用事先定义，所以<font color=#ff00 size=3 face="黑体">在函数内部正常是只能使用全局变量而不能改变全局变量的值。</font>因为在函数内部如果使用所谓的全局变量，其实是在函数内新定义了一个和全局变量一样的局部变量，所以全局变量未能得到修改，想在函数内对全局变量进行修改时必须使用`global`关键字：

```python 
	#错误示范
	big = 0      #这是全局变量
	def func():
    	big=1   #这个是另外一个局部变量
	func()
	print(big)
	#结果
	0
```
```python 
	#正确示范
	big = 0      #这是全局变量
	def func():
    	global big
    	big = 1   #对全局变量进行修改,不能使用：global big = 1 这种形式
	func()
	print(big)
	#结果
	1
```
&emsp;&emsp;还有一种思路：可以使用列表的方法来修改参数值：

```python 
	#使用列表
	big = [0]
	def func():
		big[0] = 1
	func()
	print(big[0])
	#结果
	1
```
### <font color=#0422ff size=4 face="宋体">   1.4.5、闭包(函数嵌套) </font>

&emsp;&emsp;在函数内部再定义一个嵌套函数，可以将内部的嵌套函数作为外层函数的返回结果。

**（1）定义**：

```python
    def  get():
        def  add(x,y):
            return x+y
        return add            #此处需要返回函数对象，所以不需要加括号
```

<font color=#ff00 size=3 face="黑体">注意： 外层调用内层函数时需要返回函数对象，所以不需要加括号</font>

**（2）调用**：

```python
    test=get()           #test此时为函数
    print(test(2,3))
    #结果：5
```
或
```python
    print(get()(2,3))
    #结果：5
```
### <font color=#0422ff size=4 face="宋体">   1.4.6、lambda、filter()、map()表达式 </font>
&emsp;&emsp;lambda表达式和函数作用相似，其使用方法为：`lambda  参数x ： 返回值` 例如：

```python
	g=lambda x : x**2
	print(type(g))
	print(g(2)) 
	#结果
	<class 'function'>
	4
```
&emsp;&emsp;filter()是一种过滤器函数，过滤掉值为 0 或 false 的值。传入两个参数，第一个可以为None或函数，为None时：只挑选出后面列表中的真值，如果传入的是函数，则将后面的数值带入到函数中计算后返回真值：
```python 
	list(filter(None,[1,0,True,False]))
	list(filter(lambda x : x%2,range(10)))
	#结果
	[1, True]
	[1, 3, 5, 7, 9]
```
&emsp;&emsp;map(func, *iterables)函数是映射函数，传入两个参数，第一个参数为函数，第二个为一个迭代器（类似数组），其作用将迭代器中的数值依次带入函数中计算后，返回结果：

```python 
	list(map(lambda x : x**2,range(10)))
	#结果
	[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```
### <font color=#0422ff size=4 face="宋体">   1.4.7、函数递归调用 </font>
&emsp;&emsp;<font color=#ff00 size=3 face="黑体">和C语言一致，eg:</font>

```python
     def  f(x):
         if  x==1:
              return 1
         else:
              return f(x-1)+x*x

     printf(f(4))
     #结果：30
```

### <font color=#0422ff size=4 face="宋体">   1.4.8、模块（Java中的包） </font>

&emsp;&emsp;模块就是一个保存python代码的文件，在python中使用import来引入模块。<font color=#ff00 size=3 face="黑体">和Java的包一致，可以认为python的模块就是Java的包，就像C语言的函数和Java的方法一样</font>

**（1）导入模块**：

&emsp;&emsp; 类似Java使用方法有很多；如下

&emsp;&emsp;**方法一**：调用某个模块时，使用 “import  [模块名]” 或  ”from  [模块名] import *“ eg:

```python
      import  math
      print(math.sqrt(50))

        或

      from math import* 
      print(sqrt(50))  
```

&emsp;&emsp; <font color=#ff00 size=3 face="黑体">注意：上面两种方法覆盖范围均为整个模块，但使用方法不同；使用 ` import  [模块名]` 导入的模块调用方法为： `math.[函数名]` 使用 `from [模块名] import*` 导入的模块调用方法可以直接使用函数名。</font>

&emsp;&emsp;**方法二**：调用某个模块下的某一个或几个函数时，使用 “ from [模块名] import [函数名1]，[函数名2].......” 


```python
      from math import sqrt,cos,sin

      print(sqrt(50))
      print(cos(10))
      print(sin(10))
```

&emsp;&emsp; <font color=#ff00 size=3 face="黑体">此外，如果使用 `from [模块名] import*` 或 `from [模块名] import  [函数名]` 方法导入模块时，在函数内部重新定义相同的[函数名]，则自动屏蔽导入的函数，而使用自身定义的函数。另外python使用 `from [模块名] import [函数名] ` 来代替了Java的 ` import [模块名].[函数名]` 的导入方式</font>

**（2）定义自己的模块**：


&emsp;&emsp;  python中每一个 .py 文件都可以作为一个模块使用，文件名就是模块名；直接使用上述方法导入即可，甚是”流氓“。

## 1.5 格式化输入输出与异常处理
### <font color=#0422ff size=4 face="宋体">   1.5.1、字符串函数format </font>

```python
	print("{0} love {1}.{2}".format("I","hello","world"))
	print("{a} love {b}.{c}".format(a="I",c="hello",b="world"))
	print("{a} love {b}.{2}".format(a="I",b="hello","world"))
	print("{a:.1f} {b}".format(a = 29.78,b = "GB"))
	#结果
	1：
	I love hello.world
	2：
	I love world.hello
	3：
	错误
	4:
	29.8GB (四舍五入)
```
### <font color=#0422ff size=4 face="宋体">   1.5.2、格式化字符含义 </font>
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190902150523311.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)
例子：
```python
	print('%c %c %c' %(97,98,99))
	print('%s' %'hello world')
	print('%d + %d = %d' %(4,5,4+5))
	print('%f' %2.678)
	print('%5.2f' %2.678)
	print('%5d' %2.678)
	print('%05d' %7)
	#结果
	1：
	a,b,c
	2:
	hello world
	3:
	4 + 5 = 9
	4:
	2.678000
	5:
	 2.68
	6:
	     2
	7:
	00007 
```
### <font color=#0422ff size=4 face="宋体">   1.5.3、异常处理</font>
![ ](https://img-blog.csdnimg.cn/20190903164014142.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20190903164625948.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)
&emsp;&emsp;还可以使用
```python 
	try:
		检测范围
	except Except [as reason]:
		异常处理代码
	finally:    #finally有无均可
		一定执行的语句
```
或  使用 `raise Except` 来直接引出一个异常。
例子：
```python 
	try:
		int(a)
		sum=1+'1'
		f=open('我为什么这么帅.txt')
		print(f.read())
		f.close()
	except OSError as reason:
		print('文件出错啦'+str(reason))
	except TypeError as reason:
		print('文件类型出错啦'+str(reason))
	except: #当不知道异常类型时可以不写，但不推荐这种做法
		print('不知道啥原因就出错啦')
	finally:
		print('我是一定执行的代码部分')
```
和
```python 
	raise TypeError
```
&emsp;&emsp; <font color=#ff00 size=4 face="宋体">**注意：上述except中检测出第一个异常后下面的except便不在检查，所以为了尽可能查到具体原因，python规定不带异常类型的 except必须放到最后面**</font>

### <font color=#0422ff size=4 face="宋体">   1.5.4、with语句</font>
&emsp;&emsp; with 语句适用于对资源进行访问的场合，确保不管使用过程中是否发生异常都会执行必要的“清理”操作，释放资源，比如**文件使用后自动关闭**、**线程中锁的自动获取和释放**等。
原理：

>  with 语句实质是上下文管理。 1、上下文管理协议。包含方法__enter__() 和
> __exit__()，支持该协议对象要实现这两个方法。 2、上下文管理器，定义执行with语句时要建立的运行时上下文，负责执行with语句块上下文中的进入与退出操作。
> 3、进入上下文的时候执行__enter__方法，如果设置as var语句，var变量接受__enter__()方法返回值。
> 4、如果运行时发生了异常，就退出上下文管理器。调用管理器__exit__方法。

```python
	with open('d:\\xxx.txt') as fp:
	     print fp.read()
```
```python
	class Mycontex(object):
    def __init__(self,name):
        self.name=name
    def __enter__(self):
        print("进入enter")
        return self
    def do_self(self):
        print(self.name)
    def __exit__(self,exc_type,exc_value,traceback):
        print("退出exit")
        print(exc_type,exc_value)
if __name__ == '__main__':
    with Mycontex('test') as mc:
        mc.do_self()
    #输出
    进入enter
    test
    退出exit
    None None
```
# 第二章 Python面向对象

## 说明

&emsp;&emsp;<font color=#ff00 size=3 face="黑体">面向对象的程序设计部分，程序逻辑与思想与Java极其相似，均使用类与对象的思想。包括继承、封装、多态等。</font>

## 2.1 定义和使用类

### <font color=#0422ff size=4 face="宋体">   2.1.1、类的定义 </font>

```python
    class  类名:
        属性（成员变量）
        成员函数（成员方法）

 ```

<font color=#ff00 size=3 face="黑体">  Python </font>中类的定义是:

```python
    class  Person:                                     
        num=1
        def SayHello(self):                   
            print("hello world!")
 ```

 <font color=#ff00 size=3 face="黑体">  Java </font>中类的定义是:

```java 
    class  Person{
         int num=1;
         SayHello(){
            System.out.print("hello world!");
        }        
    }                                     
 ```

&emsp;&emsp;<font color=#ff00 size=3 face="黑体">  类的方法与普通的函数只有一个特别的区别——它必须有一个额外的第一个参数名称，但是在调用这个方法的时候你不必为这个参数赋值，Python会提供这个值。这个特别的变量指对象本身，按照惯例它的名称是self，也可以用任何变量名称代替，python调用方法时会自动跳过第一个变量，从第二个赋值，但最好使用self。</font>

&emsp;&emsp;<font color=#ff00 size=3 face="黑体"> 简单说，python中的self和Java的this一样，代表类的实例，而非类。更多关于self的详细的说明请参考</font>[https://blog.csdn.net/daocaoren1543169565/article/details/80626035](https://blog.csdn.net/daocaoren1543169565/article/details/80626035)

### <font color=#0422ff size=4 face="宋体">   2.1.2、类的使用 </font>


&emsp;&emsp;类的使用和Java也类似，都是以创建对象的思想来使用，类是对象的模板。调用（创建对象）方法为：

<font color=#ff00 size=3 face="黑体">  Python </font>实例化对象：

```python 
         # 对象名=类名()
         person1=Person()
    
         person1.SayHello()
     
         #结果：hello world!
 ```

而<font color=#ff00 size=3 face="黑体">  Java </font>实例化对象：

```java
     Person person1=new Person();
     person1.SayHello();

    //结果：hello world!
 ```



## 2.2 构造函数

&emsp;&emsp;python和Java一样都具有构造函数，都是用来在对象实例化时对参数进行初始化操作。如果用户未涉及构造函数，则会提供一个默认的构造函数。在Python中使用<font color=#ff00 size=3 face="黑体">  固定的形式表示构造方法 </font>，如下：

```python  
    def __init__(self,....):
            #变量初始化
            print("helloworld")
            ...........
 ```
而在Java中使用和类名一致的函数名来定义构造函数。例如：

```java  
    class Person{
        Person(){
            变量初始化
        }
    }
 ```
&emsp;&emsp;<font color=#ff00 size=3 face="黑体"> 注意：一个class只能有一个用于构造对象的`__init__`函数，但python中的变量是无类型的,因此传给`__init__`的参数可以是任何类型。所以可以代替Java中重载和多态的思想</font>


## 2.3 析构函数
   
&emsp;&emsp;析构函数(destructor) 与构造函数相反，当对象结束其生命周期，如对象所在的函数已调用完毕时，系统自动执行析构函数。析构函数往往用来做“清理善后” 的工作，所以析构函数全部是在python中符合一定标准时自动执行的。
&emsp;&emsp;Java自动进行内存回收。python也默认提供函数进行回收内存。此外python还提供一个内存回收函数（`__del__()`）。当使用del 删除对象时，系统自动调用 `__del__()` 析构函数进行内存释放，另外当对象在某个作用域中调用完毕，在跳出其作用域的同时析构函数也会被调用一次，这样可以用来释放内存空间。析构函数的演示调用如下：
```python
    class Test:
        def __init__(self):
            print("helloworld")
        def __del__(self):
             print("该对象已删除！")

    x=Test()
    del x
    #运行后
    helloworld
    该对象已删除！
 ```
关于数值（算数）运算的析构函数如下图：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190904212058797.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)
## 2.4 实例属性与类属性（成员变量）
   
&emsp;&emsp;属性又可以叫成员变量，其分为实例属性与类属性。简单说，实例属性就是在初始化时 `__init__()` 函数中定义的，定义与引用时都要在前加上对象名。而类属性就是在成员函数（方法）外定义的，使用时可以用对象名来引用或使用类名访问，例如：

```python
    class Student:
            num = 1
            def __init__(self,str, n):
                     self.name = str
                     self.age = n
            def SayHello(self):
                     print("Hello!")
            def PrintName(self):
                     print("姓名：", self.name ,"年龄：", self.age)
            def PrintNum(self):
                     print(Student.num)

    # 主程序
    s1 = Student("王大丫", 42)
    s2 = Student("王二丫", 32)
    s1.PrintName()
    s2.PrintName()
    s1.PrintNum()
    #运行结果
    姓名： 王大丫 年龄： 42
    姓名： 王二丫 年龄： 32
    1
    1
 ```

&emsp;&emsp;<font color=#ff00 size=3 face="黑体"> 1：类变量的值在所有实例中共享，但如果类变量（程序中的num）在某实例对象中通过 `对象.类变量` 方式类似被“重新赋值”时，那么系统将重新为该实例对象分配另外的空间来存储新值，而类变量和其他实例调用类变量的值均不变。</font> 可以通过下面代码来验证：

```python
    class Student:
    num = 1
    def __init__(self):
        pass

    # 主程序
    s1 = Student()
    s2 = Student()
    print(s1.num)   
    print(s2.num)
    s2.num = 2                  # 通过调用对象实例来“修改”类变量num的值
    print(s2.num)
    print(Student.num)
    print(s1.num)
    print(id(Student.num))
    print(id(s1.num))
    print(id(s2.num))
    #运行结果
    1
    1
    2
    1
    1
    490559760
    490559760
    490559776                  #  s2的num值修改后发现系统重新给其分配了新地址
 ```

&emsp;&emsp;<font color=#ff00 size=3 face="黑体"> 2：如果类变量与实例变量同名，则优先调用实例变量</font> 验证如下：

```python
    class Student:
        num = 1
        def __init__(self, str, n):
            self.name = str
            self.age = n
            self.num = 90

    # 主程序
    s1 = Student("王大丫", 42)
    s2 = Student("王二丫", 32)
    print(s1.num)
    print(Student.num)                   #发现在类变量num值仍为1的前提下，优先使用实例变量
    print(s2.num)
    #运行结果
    90
    1
    90
 ```

## 2.5 私有成员与共有成员

&emsp;&emsp;Python无严格的私有变量保护机制，正常情况下，属性名定义时在前面加入`__`即表示私有变量（Java使用关键字 private 修饰私有变量），否则为共有变量。私有变量在类的外部不允许直接访问，想访问只有两招：其一是像Java一样通过调用共有成员方法来访问与修改。代码如下
 
```python
     class Student:
          num = 1
          def __init__(self, a, b):
                  self.age = a
                  self.__score = b
           def getScore(self):
                  return self.__score

     # 主程序
     s1 = Student(18,100)
     print(s1.getScore())
     #输出结果
     100
```

&emsp;&emsp;方法二则是使用python特殊方式进行私有变量访问，即通过：`对象名._类名+私有成员`的方式进行访问。示例如下：
 
 ```python
    class Student:
         num = 1
        def __init__(self, a, b):
            self.age = a
            self.__score = b

    # 主程序
    s1 = Student(18,100)
    print(s1._Student__score)                #通过特殊方法调用私有成员
    #运行结果
    100
 ```

## 2.6 公有方法、私有方法、静态方法

<font color=#0422ff size=4 face="黑体">   1、公有方法 </font>

&emsp;&emsp;公有方法与私有方法都属于对象，日常使用的最常见的绝大部分方法都是公有方法，通过 `def  方法名（self,......）` 定义。

&emsp;&emsp;公有方法的调用有两种方法，其一为使用对象名调用： `对象名.方法名（........）` ；其二为使用类名调用，但必须显式把对象名传给“self” 参数来指明访问的对象： `类名.函数名（对象1, ......）`。示例如下：

```python
    class Student:
    num = 1
    def Printf(self, tag):
            if tag == 1:
                print("我是通过对象名调用输出的")
            else:
                print("我是通过类名调用输出的")

    # 主程序
    s1 = Student()
    s1.Printf(1)                     #我是通过对象名调用输出的
    Student.Printf(s1, 0)            #我是通过类名调用输出的   
    #结果
    我是通过对象名调用输出的
    我是通过类名调用输出的
```

<font color=#0422ff size=4 face="黑体">   2、私有方法 </font>

&emsp;&emsp;私有方法只允许本类进行访问，外部类与子类均不能访问。因此不允许对象直接使用 `对象名.方法名（）` 直接调用，只能在内部使用 `self.方法名（）`方式使用。示例：

```python 
    class Student:
    num = 1
    def __Printf(self):
                print("我是在私有方法中输出的")
    def Wprintf(self):
        self.__Printf()              #使用self方法调用私有方法
    # 主程序
    s1 = Student()
    s1.Wprintf()
    #结果
    我是在私有方法中输出的
```

<font color=#0422ff size=4 face="黑体">   3、静态方法 </font>

&emsp;&emsp;静态方法的意义和Java类似，都是用来处理类中的逻辑判断或者运算，只能访问类成员，不能访问对象（实例）成员。所以在定义静态方法时不需要传入 “self” 参数，而且需要在定义前加 `@ staticmethod` 声明静态方法，两种调用方法均可以。示例如下：

```python
    class Student:
    num = 1
    def __init__(self):
        self.age = 20
        self.score = 100
    @ staticmethod                     #静态方法声明
    def Wprintf(tag):                  #此处不需要传入self参数
        # print(Student.score)     此处如果这样写会报错，因为变量score为实例成员，无法访问
        if tag == 1:
            print(Student.num)
            print("通过对象调用")
        else:
            print(Student.num)
            print("通过类名称调用" )

    # 主程序
    s1 = Student()
    s1.Wprintf(1)              #通过对象调用
    Student.Wprintf(0)         #通过类名调用
    #结果
    1
    通过对象调用
    1
    通过类名称调用
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190904195534605.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)
## 2.7 类的继承

&emsp;&emsp;类的继承这部分思想与Java相同，只是表达方式不大相同而已。既然存在继承，就会有父类（基类）和子类（派生类）。<font color=#ff00 size=3 face="黑体"> 子类可以继承父类的公有成员，但不能继承私有成员。</font>类继承的语法为：

```python
    class 子类名称(父类名称):
        子类成员......
```
 
&emsp;&emsp;在继承父类时，有几个特点需要注意：

**（1）**python在子类调用方法时，总是先在本类中查找方法，找不到时再去父类中找。 如示例1；

**（2）**在继承时，如果子类重写了父类的方法，那么父类的方法将不被调用，如果子类需要调用父类的方法，有两种方法。

&emsp;&emsp;**A:** 在子类方法中使用 `super()` 来调用。

&emsp;&emsp;**B:** 在主程序中使用 `父类名称.父类方法（子类对象名）` 的方式调用。如示例2；


示例1：

```python
    class Person():       
        def __init__(self):
            print("父类初始化方法")  
        def Printf(self):
            print("父类Printf方法!")
        def Wiite(self):
            print("父类Wiite方法！")
    class Student(Person):
        def __init__(self):
            print("子类初始化方法")
        def Printf(self):
            print("子类Printf方法!")

    # 主程序
    s1 = Student()
    s1.Printf()         #优先调用子类方法
    s1.Wiite()          #在子类中找不到该方法时采用父类方法  
    #结果
    子类初始化方法
    子类Printf方法!
    父类Wiite方法！
```

示例2：

```python  
    #在子类方法中调用父类方法
    class Person():
        def __init__(self):
            print("父类初始化方法")      
        def Printf(self):
            print("父类Printf方法!")
    class Student(Person):
        def __init__(self):
            super().__init__()
            print("子类初始化方法")
        def Printf(self):
            super().Printf()
            print("子类Printf方法!")
    # 主程序
    s1 = Student()
    s1.Printf()
    #结果
    父类初始化方法
    子类初始化方法
    父类Printf方法!
    子类Printf方法!

    或者

    #在主程序中调用父类方法
    class Person():
         def __init__(self):
               print("父类初始化方法")
         def Printf(self):
               print("父类Printf方法!")
    class Student(Person):
         def __init__(self):
               print("子类初始化方法")
         def Printf(self):
               print("子类Printf方法!")

    # 主程序
    s1 = Student()
    Person.__init__(s1)
    Person.Printf(s1) 
    #结果
    子类初始化方法
    父类初始化方法
    父类Printf方法!
```

## 2.8 多态

&emsp;&emsp;<font color=#ff00 size=3 face="黑体"> python中多态的含义和Java中多态类似，均依赖于继承，包括重载、重写（覆盖）、子父类数据类型的包括关系等。</font>例如：父类是人，子类有学生、教师、工人等等，学生对象的数据类型除了是学生外，同时也是父类人，学生也具有人的方法与属性。可以说学生有多种状态，就是所谓的多态。多态遵循软件设计中的“开闭原则”，即对扩展开放，对修改封闭。

# 第三章 Python图形界面设计

## 说明

&emsp;&emsp;本章主要总结Python语言在window平台下通过导入Tkinter库进行窗口设计的一些常见函数的使用方法，不会包括全部的函数使用。与Python语法学习无关，所以如果时间紧迫，可以跳过阅读。

&emsp;&emsp;Python提供多个图形开发界面的库，常用的Python GUI库如下：

**（1）Tkinter**：Tkinter模块是Python标准的工具接口，兼容Unix、Window、Mac平台，已经内置到Python安装包中，所以导入时只需要使用import导入即可；IDLE也是用Tkinter编写的，<font color=#ff00 size=3 face="黑体">适合应对简单的图形界面，做一些小工具。</font>

**（2）wxPython**：wxPython是Python语言的一套优秀的GUI图形库，允许Python程序员很方便的创建完整的、功能健全的GUI用户界面。 wxPython是作为优秀的跨平台GUI库wxWidgets的Python封装和Python模块的方式提供给用户的。

**（3）Jython**：Jython是一种完整的语言，而不是一个Java翻译器或仅仅是一个Python编译器，它是一个Python语言在Java中的完全实现。Jython也有很多从CPython中继承的模块库。最有趣的事情是Jython不像CPython或其他任何高级语言，它提供了对其实现语言的一切存取。所以Jython不仅给你提供了Python的库，同时也提供了所有的Java类。这使其有一个巨大的资源库<font color=#ff00 size=3 face="黑体">如果想全面的了解和学习使用Tk模块进行界面编程部分设计，此处推荐一位大神的博客：</font>    [https://blog.csdn.net/yingshukun/article/details/53985080](https://blog.csdn.net/yingshukun/article/details/53985080)。

## 3.1 创建window窗口

```python
    import tkinter

    win=tkinter.Tk()
    #设置标题
    win.title("i乐帮")
    #设置界面宽与高
    win.geometry("800x400")
    #设置最小与最大窗口
    # win.minsize("200x100")
    # #win.maxsize("1000x800")
    #进入消息循环，也就是显示窗口
    win.mainloop()
```

## 3.2 几何布局管理器

&emsp;&emsp;何为几何布局管理器？简单来说就是对各种组件（如Button、Text、Label等）在页面上显示的位置，宽高等属性进行控制管理。Tkinter提供了3种风格不同的管理器：<font color=#ff00 size=4 face="黑体">pack、grid、place。</font> 

<font color=#0422ff size=4 face="黑体">   1、pack布局管理器 </font>

&emsp;&emsp;pack采用<font color=#ff00 size=3 face="黑体">块</font>的方式组织组件；pack布局根据<font color=#ff00 size=3 face="黑体">子组件创建生成的顺序</font>将其放在快速生成的界面中，例如在如下两个示例中，button与label显示的位置不同：

```python
    from tkinter import *

    #创建根窗口
    root = Tk()
    #创建button
    button=Button(root,text="我是button")
    button.pack(side=LEFT)                        #使用pack布局
    #创建标签
    label=Label(root,text="我是标签")
    label.pack(side=LEFT)
    #循环显示
    root.mainloop()
```

```python
    from tkinter import *

    #创建根窗口
    root = Tk()
    #创建标签
    label=Label(root,text="我是标签")
    label.pack(side=LEFT)
    #创建button
    button=Button(root,text="我是button")
    button.pack(side=LEFT)
    #循环显示
    root.mainloop()
```

&emsp;&emsp;在pack()方法内提供若干参数设置选项，具体设置请自行查找。

<font color=#0422ff size=4 face="黑体">   2、grid布局管理器 </font>

&emsp;&emsp;grid采用<font color=#ff00 size=3 face="黑体">表格</font>的方式组织组件；grid位置布局根据<font color=#ff00 size=3 face="黑体">子组件的行/列单元格确定。</font>子组件可以跨多行/列，在每一列中，列宽由这一列中最宽的单元各确定；grid管理器被广泛应用。类似于Android开发中的<font color=#ff00 size=3 face="黑体">相对布局</font>，示例如下：

```python 
    from tkinter import*
    root=Tk()
    Button(root,text="1").grid(row=0,column=0)
    Button(root,text="2").grid(row=0,column=1)
    Button(root,text="3").grid(row=0,column=2)
    Button(root,text="4").grid(row=1,column=0)
    Button(root,text="5").grid(row=1,column=1)
    Button(root,text="6").grid(row=1,column=2)
    Button(root,text="7").grid(row=2,column=0)
    Button(root,text="8").grid(row=2,column=1)
    Button(root,text="9").grid(row=2,column=2)
    Button(root,text="0").grid(row=3,column=0,columnspan=2,sticky=E+W)
    Button(root,text=".").grid(row=3,column=2,sticky=E+W)
    root.mainloop()
```

<font color=#0422ff size=4 face="黑体">   3、palce布局管理器 </font>

&emsp;&emsp;place几何布局管理器允许指定组件的大小和位置。place的优点是可以控制精确控制组件的位置，不足之处是改变窗口的大小时，子组件不能在其父组件随之灵活改变大小。示例如下：

```python
    from tkinter import*
    root=Tk()
    root.title("place界面布局管理器")
    root['width']=300;root['height']=300
    Label(root,text="用户名",width=6).place(x=1,y=1)
    Entry(root,width=20).place(x=45,y=1)
    Label(root,text="密  码",width=6).place(x=1,y=20)
    Entry(root,width=20,show="*").place(x=45,y=20)
    Button(root,text="登录",width=8).place(x=40,y=40)
    Button(root,text="取消",width=8).place(x=110,y=40)
    root.mainloop()
```

## 3.3 Tkinter组件

&emsp;&emsp;有些界面设计经验的编程人员大致都很了解界面控件有哪些了，Tkinter提供的控件也大致相同，简单的控件如下：

| 控件  | 描述    | 
| :-:  | :-|
| Button | 按钮控件，在程序中显示按钮    |  
| Canvas  | 画布控件，显示图形元素，例如线条或文本|  
| Checkbutton | 多选框控件，用作提供多项选择框 |  
|Entry|输入控件，用于输入文本信息|
|Frame|框架控件，在屏幕上显示一个矩形区域，用来作为容器|
|Label|标签控件，用来显示文本或位图|
|Listbox|列表框控件，用来显示一个字符串列表给用户|
|Menubutton|菜单按钮控件，用于显示菜单项|
|Menu|菜单控件，显示菜单栏，下拉菜单和弹出菜单|
|Message|消息控件，用来显示多行文本，于Label类似|
|Radiobutton|单选按钮控件，显示菜单栏，下拉菜单与弹出菜单|
|Scale|范围控件，显示一个单选的按钮状态|
|Scrollbar|滚动条控件，在内容超过可视化区域时使用，例如列表框|
|Text|文本控件，用于显示多行文本|
|Toplevel|容器控件，用来提供一个单独的对话框，和Frame比较类似|
|Spinbox|输入控件，与 Entry类似，但是可以指定输入范围值|
|PanedWindow|PanedWindow是一个简单的容器控件，常用于复杂的窗口布局|
|LabelFrame|LabelFrame是一个简单容器控件，常用于复杂窗口布局|
|tkMessageBox|用于显示应用程序的消息框|

&emsp;&emsp;以上所有组件都包括一些共同的属性，如字体大小、颜色等，如下表所示

| 属性 | 描述 |
| :-:|-|
|dimension| 控件大小|
|color|控件颜色|
|font|控件字体|
|anchor|锚点（内容停靠位置），对应东、西、南、北四个点|
|relief|控件样式|
|bitmap|位图，内置位图包括 error、gray75、gray50、gray25、gray12、ginfo、questhead、hourglass、question和warning，自定义位图为.xbm格式的文件|
|cursor|光标|
|text|显示文本内容|
|state|设置组件状态为正常（NORMAL）、激活（ACTIVE）、禁用（DISABLED）|

&emsp;&emsp;设置组件的属性代码方式有三种，如示例所示：

```python
    from tkinter import*
    root=Tk()
    root.title("组件属性设置方式")
    root['width']=300;root['height']=300
    #方式一
    button1=Button(root,text="方式一")
    button1.grid()
    #方式二
    button2=Button(root)
    button2.config(text="方式二")
    button2.grid()
    #方式三
    button3=Button(root)
    button3["text"]="方式三"
    button3.grid()
    root.mainloop()
```

&emsp;&emsp;每一种控件的具体的使用方法和python语法无关，这里就不详细的介绍了，该部分可以在网上查找相关的资料自行学习。

## 3.4 Tkinter字体

<font color=#0422ff size=4 face="黑体">   1、通过元组表示字体 </font>

&emsp;&emsp;使用 `("字体名","字体大小","其他样式修饰")` 元组来修饰,放在 `font` 属性里；示例如下：

```python
    from tkinter import*
    root=Tk()
    root.title("通过元组表示字体！")
    root.geometry("800x400")
    # Label显示
    label=Label(root, text="标签", font=("Arial","27","italic"))
    label.pack()
    root.mainloop()
```

<font color=#0422ff size=4 face="黑体">   2、通过Font对象表示字体 </font>

&emsp;&emsp;直接上示例：

```python
    from tkinter import*
    import tkinter.font
    root=Tk()
    root.title("通过Font对象表示字体！")
    root.geometry("800x400")
    # Label显示
    ft=tkinter.font.Font(family="Arial",size=19)
    label=Label(root, text="标签", font=ft)
    label.pack()
    root.mainloop()
```

## 3.5 Python事件处理

<font color=#0422ff size=4 face="黑体">1、事件类型</font>

&emsp;&emsp;事件通用定义格式： `<modifier-detial>`。其中 `modifier` 定义的是按键类型，其包括键盘、鼠标、窗体等设备， `detial` 用于明确定义哪一个键或按钮的行为。示例如下：


```python
	<Button-1>  				#按下鼠标左键
	<KeyPress-A>  			  #按下键盘上的A键
	<Control-Shift-KeyPress-A>  #同时按下Control、Shift、KeyPress-A三个键
```

&emsp;&emsp;键盘事件如下：

|名称|描述|
|:-:|-|
|KeyPress|按下键盘时触发，可以在detial中指明是哪个键|
|KeyRelease|释放键盘上的某键时触发，可以在detial中指明是哪个键|


&emsp;&emsp;鼠标事件如下：

|名称|描述|
|:-:|-|
|ButtonPress或button|按下鼠标某键时触发，可以在detial中指明是哪个键|
|ButtonRelease|释放鼠标某键时触发，可以在detial中指明是哪个键|
|Motion|点中组件的同时托拽组件移动时触发|
|Enter|当鼠标指针移进组件时触发|
|Leave|当鼠标指针移出组件时触发|
|MouseWheel|当鼠标滚轮滚动时触发|




&emsp;&emsp;窗体事件如下：

|名称|描述|
|:-:|-|
|Visibility|当组件变为可视时触发|
|Unmap|当组件由显示状态变为隐藏状态时触发|
|Map|当组件由隐藏状态变为显示状态时触发|
|Expose|当组件从原本被其他组件遮盖的状态中暴露出来时触发|
|FocusIn|当组件获得焦点时触发|
|FocusOut|当组件失去焦点时触发|
|Configure|当改变组件大小时触发，例如拖拽窗体边缘|
|Property|当窗体的属性被删除或改变时触发，属于TK的核心事件|
|Destroy|当组件被销毁时触发|
|Activate|与组件选项中的state项有关，表示组件由不可用转为可用，例如按钮由disabled（灰色）转为enabled|
|Deactivate|与组件选项中的state项有关，表示组件由可用转为不可用，例如按钮由enabled转为disabled（灰色）|


<font color=#0422ff size=4 face="黑体">2、事件绑定 </font>

&emsp;&emsp;事件绑定有三种方法，分为创建组件对象时指定、实力绑定、标识绑定。

1、创建组件对象时指定：

```python
	def callback():
		showinfo("人生苦短，我用Python!")
	button=Button(root,text="设置command",command=callback)
	button.pack()
```

2、实例绑定：
&emsp;&emsp;使用bind()函数来指定组件绑定事件。

```python
	组件对象.bind("<事件类型>",事件处理函数)
```

例如：

```python
	button.bind("<Button-1>",callback)
```

3、标识绑定：

```python
	组件对象.tag_bind("r1","<Button-1>",callback)
```

<font color=#0422ff size=4 face="黑体">3、事件处理函数 </font>

1、定义事件处理函数

事件处理函数通过传递event参数进行信息交互，Event对象的参数如下：

|参数|说明|
|:-:|-|
|.x/.y|鼠标相对于组件左上角的坐标|
|.x_root/.y_root|鼠标相对于屏幕左上角的坐标|
|.keycode|键码，但他不能反应事件前缀Alt,Control,Shift,Lock,并且它不区分大小写按键，即输入a与A是相同的键码。|
|.char|字符|
|.type|事件类型|
|.widget|触发的组件|

# 第四章 Python文件的使用

&emsp;&emsp;Python中对文件的操作通常按照以三个步骤进行，和C语言、Java使用方法类似：
**（1）**使用open()函数打开（或建立）文件，返回一个file对象
**（2）**使用file对象的读写方法对文件进行读写操作。其中将数据从外存传输到内存的过程称为读操作，将数据从内存传输到外存的过程称为写操作。
**（3）**使用file对象的close()方法关闭文件

## 4.1 打开/建立文件


&emsp;&emsp;打开文件的方法主要使用 `open（）` 函数: `file对象=open("文件路径"，"mode模式"，buffering)`；调用方法有两种；如下所示：


```python
	#该方法需要手动关闭文件：使用.close()方法
	filepoint=open("D:\python\text.txt","r",0(False)/1(True))
	或
	#该方法在文件使用后会自动关闭文件
	with open("D:\python\text.txt","r",0(False)/1(True)) as filepoint:
```

&emsp;&emsp;其中mode的值为：

|值|描述|
|:-:|-|
|"r"|读模式，如果文件不存在，则发生异常。默认值为"r"|
|"w"|写模式，如果文件不存在，则先创建再打开；如果文件存在，则清空文件再打开|
|"a"|追加模式，如果文件不存在，则先创建文件再打开；如果文件存在，打开文件后将新内容追加到原内容之后|
|"b"|二进制模式，可添加到其他模式中使用，例如"rb":读取二进制文件|
|"+"|读/写模式，可添加到其他模式使用，例如"r+"：打开文件并读写。|
![](https://img-blog.csdnimg.cn/20190903145438223.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)
&emsp;&emsp;buffering参数为1时表示I/O有缓冲，为0时表示I/O无缓冲，<font color=#ff00 size=3 face="">python3中文本文件不能设置buffering = 0，而二进制文件可以。</font>当参数大于1时，表示缓冲区大小，以字节为单位，负数表示默认缓冲区大小。<font color=#ff00 size=3 face="">注意：缓冲区指的是程序一次性从外存（ROM）读取到内存（RAM）中的数据量，与程序性能和处理数据速度有关，与总共读取的数据量无关。</font> 示例如下：

```python
	# file对象=open("文件路径"，"mode模式"，"buffering")
	filepointer = open("F:\Test.txt", "r", 1)
	print(filepointer)
	textcontent=filepointer.read()
	print(textcontent)

	#结果：
	<_io.TextIOWrapper name='F:\\Test.txt' mode='r' encoding='cp936'>
	hello,word!
```

## 4.2 读文本文件

&emsp;&emsp;读取文本文件的方法主要有以下三种：

|方法|描述|
|:-:|-|
|read()|将整个文件的内容读取为一个字符串，同时可以选择设置参数，如read(3):表示一次读取三个字符，注意：此处不是缓冲字符了，而是从缓冲字符中一次性读取多少字节的数据|
|readline()|从文件中获取一个字符串，一行一行的读。<font color=#ff00 size=3 face="">读完后指定自动传递到下一行。每一行最后的回车键会算单独一行</font>|
|readlines()|返回一个字符串列表，其中每一项是文件中每一行的字符串。|

![](https://img-blog.csdnimg.cn/20190903150516896.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)

&emsp;&emsp;read()的使用方法在上一个示例中使用到了，而readline()示例如下：

```python
	filepointer = open("F:\Test.txt", "r", 1)
	while True:
    	textcontent=filepointer.readline()
    	print(textcontent)
    	if textcontent=="":
    	    break;
	filepointer.close()

	#结果
	第一行

	第二行

	第三行
```

&emsp;&emsp;readlines()的使用示例如下：

```python
	filepointer = open("F:\Test.txt", "r", 1)
	textcontent=filepointer.readlines()
	filepointer.close()
	print(textcontent)
	for line in textcontent:
    	print(line)

	#结果
	['第一行\n', '第二行\n', '第三行']
	第一行
	
	第二行

	第三行
```

## 4.3 写文本文件

&emsp;&emsp;因为open()方法默认打开方式是"r"读方式，所以如果进行写操作时必须注明"w"标志。同样写操作时是不能读的。同样写方法主要有两种： `write()` , `writelines()`。使用方法如下：

|方法|描述|
|:-:|-|
|write()|字符串写入操作，示例：write("写入操作")，<font color=#ff00 size=3 face="">注意：使用"w"方式打开时将清空原有内容。</font>|
|writelines(sequence)|向文件中写入一个序列字符串列表，如果需要换行，需要自己加入每行的换行符;sequence为序列对象名|

&emsp;&emsp; `write()` 方法的使用示例如下：

```python 
	# file对象=open("文件路径"，"mode模式"，"buffering")
	filepoint = open("F:\Test.txt", "w")
	filepoint.write("以w方式写入！\n")
	filepoint.close()
	filepoint1 = open("F:\Test.txt", "a")
	filepoint1.write("以a方式写入！\n")
	filepoint1.close()
```

&emsp;&emsp; `writelines()` 方法的使用示例如下：

```python
	filepoint = open("F:\Test.txt", "w")
	list1=["1","2","3","4"]
	filepoint.writelines(list1)
	filepoint.close()
```

## 4.4 关闭文件

&emsp;&emsp;关闭文件主要有两种方法，其一是使用 `.close()` 方法关闭文件，其二是使用 `with` 关键字对文件进行自动关闭。

&emsp;&emsp;**1、**使用`.close()` 方法关闭文件时还有两种思路：示例如下

```python
	#思路一
	filepoint = open("F:\Test.txt","r")
	textcont=filepoint.read()
	filepoint.close()
	print(textcont)
	
	#思路二
	filepoint = open("F:\Test.txt","r")
	try:
    	textcont=filepoint.read()
	finally:
    	filepoint.close()
	print(textcont)
```

&emsp;&emsp;**2、**使用 `with` 关键字关闭文件的示例如下：

```python
	with open("F:\Test.txt","r") as filepoint :
    	textcont=filepoint.read()
	print(textcont)
```
## 4.5 二进制文件的读/写
	
&emsp;&emsp;当我在小白入门时期，完全搞不懂什么是文本文件，什么是二进制文件。所以为了更好的学习python，还是先科普一下为好。直接上百度百科：[https://zhidao.baidu.com/question/1372778.html](https://zhidao.baidu.com/question/1372778.html) ；简单说就是文本文件就是经过ASCII编码后显示给我们看的中英文文件，而二进制文件就是单纯的使用0和1这个计算机唯一能识别数据流，例如音视频文件等。

&emsp;&emsp;python没有二进制类型，但可以使用string类型来存储二进制数据类型，因为string是以字节为单位的。主要有<font color=#ff00 size= face="">将数据转换为字节流</font>和<font color=#ff00 size= face="">将字节流转换为数据</font>两个互逆过程

<font color=#0422ff size=4 face="黑体">1、将数据转换为字节流</font>

&emsp;&emsp;使用 `struct` 结构体中的 `pack("格式化字符串",数据)` 函数来进行转换。pack()中的参数：格式化字符串用来表示数据的数据类型（int，bool等）。示例如下：

```python
    import struct

	a=90
	bytes=struct.pack("i",a)
	print(bytes)
	
	#结果
	b'Z\x00\x00\x00'
```

<font color=#0422ff size=4 face="黑体">2、将字节流转换为数据</font>

&emsp;&emsp;使用 `struct` 结构体中的 `unpack()` 函数来还原成数据。具体示例可以查阅文献得到。


# 推荐阅读

**1、Java学习中的疑难点总结**： [https://blog.csdn.net/GuoQiZhang/article/details/89784677](https://blog.csdn.net/GuoQiZhang/article/details/89784677)

**2、计网，数据库学习思维导图**： [https://blog.csdn.net/GuoQiZhang/article/details/89812526](https://blog.csdn.net/GuoQiZhang/article/details/89812526)

**3、Win10系统下载安装Markdown破解与右侧无法预览的解决办法**： [https://blog.csdn.net/GuoQiZhang/article/details/90315238](https://blog.csdn.net/GuoQiZhang/article/details/90315238)