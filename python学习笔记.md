@[TOC](Python学习笔记（持续更新）)

# 前言

&emsp;&emsp;来交作业啦！之前给自己定的目标（每周至少更新一篇学习总结），如今万里长征已经迈出了第一步！希望学习的同时通过博客自勉吧！言归正传，从本篇博客开始，我准备使用接下来的一个月左右的时间学习一下如今最火的编程语言—Python，所以这篇文章也会持续更新。

# 注意
&emsp;&emsp;本篇文章是在默认已经学过C语言和Java语言的前提下总结的，因只重点总结Python与C、Java不同或易错知识点。红线部分为重点或与C、Java不同之处。尚未学习过C、Java的小伙伴们可以先自学C语言和Java，在我看来对比C语言和Java来学习python，效果可能会更好！在此提供一篇本人之前学习Java的笔记：[点我点我](https://blog.csdn.net/GuoQiZhang/article/details/89784677)

# 该不该学习Python（个人感受，纯属胡言论语）

&emsp;&emsp;通过一周左右的学习，让我感受到了这门语言的一个最大特点：<font color=#0422ff size=5 face="黑体">流氓</font>，这是我目前能找到对它最好的修饰词了。但这绝对不是在贬低Python，反而是在赞扬它。作为一门前端语言，它集C、Java语言中的精华于一身。很好的发挥了前端语言<font color=#ff40 size=3 face="宋体">重视简洁高效，轻视执行速度</font>的特点，就像那句：人生苦短，我用Python！那么该不该学习Python呢？我的建议如下：

 1. 如果你只是<font color=#ff40 size=3 face="宋体">单纯的想搞事情</font>，想做出一个作品或者想完成某个项目，又或者对编程有兴趣想尝试，优先学习Python能够快速的达到你的目的。
 
 2. 如果你将来想<font color=#ff40 size=3 face="宋体">从事编程这类计算机的相关工作或者编程是你狂热的兴趣爱好</font>，学习C和C++将会使你的编程道路走的更深更远，算的上是IT必修课程之一，它能有效的帮助你了解和理解计算机软硬件的工作方式和软硬件是如何协同工作的，它们工作的思维方式是什么，让你更懂计算机的想法，也能帮助你更快的学习其他的编程语言，万变不离其宗，其中的道理自然可以互通，也为你的学习提供了实用高效的参照物。

# 第一章 Python基础知识

## 1.1 Python基本语法

### 1.1.1  Python 数据类型

<font color=#0422ff size=4 face="黑体">1、数值类型：</font>

（1）整型（int）

  &emsp;&emsp;&emsp; Python3版本中只有一种int，取消了Python2中的long类型。

（2）浮点型（float）

&emsp;&emsp;&emsp; 科学技术法表示：2.78E2, Python解释器结果：278.0

（3）复数（complex）   

&emsp;&emsp;&emsp;表示方法：`a+bj`或`a+bJ`或`complex(a,b)`， Python解释器结果：`（a+bj）`
<font color=#ff40 size=3 face="黑体">总结：Python数据类型是不允许改变的，如果改变，意味着将重新分配内存空间，也表明Python是强类型的动态脚本语言，关于语言类型的分类可以参考：</font>[传送门](https://blog.csdn.net/xhg_wandering_soul/article/details/80796192)

<font color=#0422ff size=4 face="黑体">2、字符串</font>

&emsp;&emsp;Python将单字符和字符串合并，单引号与双引号均可使用，且效果一致。当想在字符串中嵌套字符串时内外引号需要不同（’I am”bom”!’和”I am’bom’!”）

<font color=#0422ff size=4 face="黑体">3、布尔类型</font>

&emsp;&emsp;只有True和False两种类型，与或非运算同C、Java。在Python中数字0、0.0、空字符串、空元组、空序列、空字典等一切空值均为False，其它值认为True，这和C语言一致，和Java不同。在Java中布尔类型为单独数据类型，不能与其他类型混合使用，例如


```python

      if(1) // error
```

<font color=#0422ff size=4 face="黑体">4、空值</font>

&emsp;&emsp;使用None表示，不支持任何运算，未指定返回值的函数自动返回None。和C语言、Java一致。

### 1.1.2  Python 序列数据结构

<font color=#0422ff size=4 face="黑体">1、列表（List） ——元素可变</font>

**（1）创建**：

```python

     方法(1)：  list1=['中国','美国',2019,2.87]
     方法(2)：  a=list('中国')
     #list()内部最多输入一个字符串，且真实的存储是a=[‘中’,’国’]。
```

**（2）访问（索引）**：


&emsp;&emsp;类似数组采用截取（切片）的方式，eg：`list1[0]，list[1:5]`

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

&emsp;&emsp;C中间插入：`list1.insert(a,b)`：a为插入的位置；b为插入的值

**（4）合并**：`a=[1,2,3]  b=[4,5,6]`  `a+b` 或`a.extend(b)` 完成合并，`a+b`不改变a,b的值，`a.extend(b)`修改a的值。

**（5）删除**：
&emsp;&emsp;A按位置删除元素：`del list1[2] 、list1.pop(2)`  pop()函数无参数时删除尾部元素。

&emsp;&emsp;B按元素值删除：`list1.remove(“a”)`

**（6）判断**：`a in list1` ：返回True说明a在list1中，False说明a不在list1中。

**（7）排序**：`list1.sort()`  默认升序

**（8）长度**：`len(list1) 、  list1.count(a)`：查询a元素在列表中出现的次数，

**（9）位置**：`list1.index(a)`：查询a在列表中首次出现的位置。

**（10）列表生成式**：`range(a,b)`：输出从a到b-1的所有值，使用`list(range(a,b))`,生成列表。

&emsp;&emsp; A  for循环：`[x*x for x in range(1,11)]` 

&emsp;&emsp;  B  if判断：`[x*x for x in range(1,11) if x%2==0]` 
    
<font color=#0422ff size=4 face="黑体">   2、元组(tuple)——元素不可变</font>

**(1)特点**：与列表相似，不同是使用小括号，且元素不能修改。

**(2)创建**：

```python

    方法1： tuple1=(1,2,3,"中国")   
    方法2： tuple1="中国","英国",100,200 #（可以省略括号）
```

 &emsp;&emsp;  &emsp;当只有单元素时，为了与单变量区别，在元素后面要加逗号。

**(3)连接/截取（切片）**：与列表相同

**(4)删除**：不能删除元素，只能删除整个元组：`del tuple1`

**(5)字符串、列表、元组转换**：`str()、list()、tuple()`


 <font color=#0422ff size=4 face="黑体">   3、字典（dict） ——键唯一且无序</font>
    
**(1）创建**：由键值对（key => value）组成，用花括号{}表示。eg: dict1={key1:1,key2: 2} 

 &emsp;&emsp; <font color=#ff40 size=3 face="黑体">注：key必须唯一不唯一时后者的value覆盖前者的value，value不必。Key不可修改，所以只能用数字、字符串、元组表示；而value可以修改，可以使用任何数据类型。创建空字典：dict1={}</font>

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

 <font color=#0422ff size=4 face="黑体">   4、集合（set）———无序不重复</font>

**（1）创建**：使用大括号{} 或set()函数。注：创建一个空集合时必须使用set()函数。

```python

    方法1：set1={1,2,3,4,5} 
    方法2：set1=set()
```
**（2）判断**：in使用方法与字典一致

**（3）集合运算**： 

&emsp;&emsp; 	A：差：’-’

&emsp;&emsp;  B：并：’|’

&emsp;&emsp;    C：交：’&’

&emsp;&emsp;   D：异或：’^’

### 1.1.3  Python 控制语句

<font color=#ff40 size=3 face="黑体">（1）、Python使用’#’做注释符,和C、Java的’/’用法相同，但python没有多行注释符，只能用多行#代替</font>

<font color=#ff40 size=3 face="黑体">（2）、Python不用大括号、begin等符号区分代码块，而是使用缩进来区分，换行使用’\’。</font>

<font color=#0422ff size=4 face="黑体">   1、选择结构 </font>

   &emsp;&emsp; if....else 和if....elif.....else：使用方法与C、Java相似，区别：多了elif关键字；选择条件不用小括号，且在条件后面加冒号。Eg：
   

```python

    if True: 
   		........
    else:
   		........
```
<font color=#0422ff size=4 face="黑体"> 2、循环结构  </font>

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

### 1.1.4  Python 函数与模块

<font color=#0422ff size=4 face="黑体">   1、函数的定义 </font>

```python

    def  函数名（函数参数）:
           函数体
	    return 表达式或者值
```

例如

```python

    def hello(arg)
            print("hello,word!")
            return 0

```

&emsp;&emsp;函数参数不用指定参数类型，因为python中的变量是动态脚本语言。函数定义的采用缩进方式划分。return返回值可选，且可以在任意地方出现，执行return后函数结束。

<font color=#0422ff size=4 face="黑体">   2、函数的使用 </font>

&emsp;&emsp;和C语言一致，先定义再使用。例如：

```python
 
    hello(1)

```

<font color=#0422ff size=4 face="黑体">   3、闭包(函数嵌套) </font>

&emsp;&emsp;在函数内部再定义一个嵌套函数，可以将内部的嵌套函数作为外层函数的返回结果。

**（1）定义**：

```python

    def  get():
        def  add(x,y):
            return x+y
        return add            #此处需要返回函数对象，所以不需要加括号

```

<font color=#ff40 size=3 face="黑体">注意： 外层调用内层函数时需要返回函数对象，所以不需要加括号</font>

**（2）调用**：

```python

    test=get()           #test此时为函数
    print(test(2,3))
 
    #结果：5
```

<font color=#0422ff size=4 face="黑体">   4、函数递归调用 </font>

&emsp;&emsp;<font color=#ff40 size=3 face="黑体">和C语言一致，eg:</font>

```python

     def  f(x):
         if  x==1:
              return 1
         else:
              return f(x-1)+x*x

     printf(f(4))
   
     #结果：30

```

<font color=#0422ff size=4 face="黑体">   5、模块（Java中的包） </font>

&emsp;&emsp;模块就是一个保存python代码的文件，在python中使用import来引入模块。<font color=#ff40 size=3 face="黑体">和Java的包一致，可以认为python的模块就是Java的包，就像C语言的函数和Java的方法一样</font>

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

&emsp;&emsp; <font color=#ff40 size=3 face="黑体">注意：上面两种方法覆盖范围均为整个模块，但使用方法不同；使用 ` import  [模块名]` 导入的模块调用方法为： `math.[函数名]` 使用 `from [模块名] import*` 导入的模块调用方法可以直接使用函数名。</font>

&emsp;&emsp;**方法二**：调用某个模块下的某一个或几个函数时，使用 “ from [模块名] import [函数名1]，[函数名2].......” 


```python

      from math import sqrt,cos,sin

      print(sqrt(50))
      print(cos(10))
      print(sin(10))

```

&emsp;&emsp; <font color=#ff40 size=3 face="黑体">此外，如果使用 `from [模块名] import*` 或 `from [模块名] import  [函数名]` 方法导入模块时，在函数内部重新定义相同的[函数名]，则自动屏蔽导入的函数，而使用自身定义的函数。另外python使用 `from [模块名] import [函数名] ` 来代替了Java的 ` import [模块名].[函数名]` 的导入方式</font>

**（2）定义自己的模块**：


&emsp;&emsp;  python中每一个 .py 文件都可以作为一个模块使用，文件名就是模块名；直接使用上述方法导入即可，甚是”流氓“。

## 1.2 Python面向对象

### 说明

&emsp;&emsp;<font color=#ff40 size=3 face="黑体">面向对象的程序设计部分，程序逻辑与思想与Java极其相似，均使用类与对象的思想。包括继承、封装、多态等。</font>

### 1.2.1 定义和使用类

<font color=#0422ff size=4 face="黑体">   1、类的定义 </font>

  ```python
 
    class  类名:
        属性（成员变量）
        成员函数（成员方法）

 ```

<font color=#ff40 size=3 face="黑体">  Python </font>中类的定义是:

  ```python
 
    class  Person:                                     
        num=1
        def SayHello(self):                   
            print("hello world!")

 ```

 <font color=#ff40 size=3 face="黑体">  Java </font>中类的定义是:

  ```java
 
    class  Person{
         int num=1;
         SayHello(){
            System.out.print("hello world!");
        }        
    }                                     

 ```

&emsp;&emsp;<font color=#ff40 size=3 face="黑体">  类的方法与普通的函数只有一个特别的区别——它必须有一个额外的第一个参数名称，但是在调用这个方法的时候你不必为这个参数赋值，Python会提供这个值。这个特别的变量指对象本身，按照惯例它的名称是self，也可以用任何变量名称代替，python调用方法时会自动跳过第一个变量，从第二个赋值，但最好使用self。</font>

&emsp;&emsp;<font color=#ff40 size=3 face="黑体"> 简单说，python中的self和Java的this一样，代表类的实例，而非类。更多关于self的详细的说明请参考</font>[https://blog.csdn.net/daocaoren1543169565/article/details/80626035](https://blog.csdn.net/daocaoren1543169565/article/details/80626035)

<font color=#0422ff size=4 face="黑体">   2、类的使用 </font>


&emsp;&emsp;类的使用和Java也类似，都是以创建对象的思想来使用，类是对象的模板。调用（创建对象）方法为：

<font color=#ff40 size=3 face="黑体">  Python </font>实例化对象：

  ```python
 
     # 对象名=类名()
     person1=Person()
     person1.SayHello()
     
     #结果：hello world!

 ```

而<font color=#ff40 size=3 face="黑体">  Java </font>实例化对象：

  ```java
 
     Person person1=new Person();
     person1.SayHello();

     //结果：hello world!
 ```



### 1.2.2 构造函数

&emsp;&emsp;python和Java一样都具有构造函数，都是用来在对象实例化时对参数进行初始化操作。如果用户未涉及构造函数，则会提供一个默认的构造函数。在Python中使用<font color=#ff40 size=3 face="黑体">  固定的形式表示构造方法 </font>，如下：

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

&emsp;&emsp;<font color=#ff40 size=3 face="黑体"> 注意：一个class只能有一个用于构造对象的`__init__`函数，但python中的变量是无类型的,因此传给`__init__`的参数可以是任何类型。所以可以代替Java中重载和多态的思想</font>


### 1.2.3 析构函数
   
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

### 1.2.4 实例属性与类属性（成员变量）
   
&emsp;&emsp;属性又可以叫成员变量，其分为实例属性与类属性。简单说，实例属性就是在初始化时 `__init__()` 函数中定义的，定义与引用时都要在前加上对象名。而类属性就是在成员函数（方法）外定义的，使用时可以用对象名来引用或使用类名访问。<font color=#ff40 size=3 face="黑体"> 注意：如果实例对象中的类变量（程序中的num）没有重新赋值，则所有实例中的类变量共享同一值,但如果实例对象中的类变量被使用 `对象.类变量` 方式重新赋值，则各对象中的类变量（num）将新分配内存来存储，所以值将不同。</font>演示如下：


  ```python

    class Student:
        num=1;
        def __init__(self,str,n):
            self.name=str
            self.age=n
        def SayHello(self):
            print("Hello!")
        def PrintName(self):
            print("姓名：",self.name",年龄：",self.age)
        def PrintNum(self):
            print(Person.num)

    #主程序
    s1=Student("王大丫",42)
    s2=Student("王二丫",32)
    s1.PrintName()
    s2.PrintNum()
    Student.num=2
    print(s1.num)
    print(s2.num)
    s1.num=3        #对象中的类变量被重新赋值
    s2.num=4        #对象中的类变量被重新赋值
    print(s1.num)
    print(s2.num)

    #运行结果
    姓名：王大丫 年龄：42
    姓名：王二丫 年龄：32 
    2
    2
    3
    4
 ```



# 未完待续。。。。。。

