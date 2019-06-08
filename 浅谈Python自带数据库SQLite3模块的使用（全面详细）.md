@[TOC](目录)

# 写在前面

&emsp;&emsp;SQLite3数据库是一款非常小巧轻量级的嵌入式开源数据库软件，也就是说没有独立的维护进程，所有的维护都来自于程序本身。由于其方便快捷，从python2.5开始SQLite3就成了Python语言的标准模块了；这也是Python中唯一一个数据库接口类模块，适合用户开发<font color=#ff00 size=3 face="黑体">小型数据库系统。</font>，此外建议小伙伴们在阅读之前先学习一些SQL数据库语言的基本语法，否则看这SQL语句会有一点蒙。接下来就体验一下它的神秘力量吧！

# 一：使用数据库的宏观过程

&emsp;&emsp;我猜很多小伙伴们开始学习数据库时应该和我一样把重点放在学习使用数据库的每一条SQL语句上，可是当我学习完近所有的语句后发现：我还是对建立使用数据库的过程一知半解，这样缺少从整体上对数据库的认识和了解。所以<font color=#ff00 size=3 face="黑体">我认为正确的方法应该是：先从整体上对数据库的使用过程有一个清晰宏观的掌握，之后再深入学习，这样食用味道会更佳哦！</font>

&emsp;&emsp;话不多说，上菜：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190608141603425.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)


# 二：数据库使用

## 1、导入数据库模块

&emsp;&emsp;此处没有什么可说的，由于python2.5以后的安装包已经自带SQLite3的软件包了，所以一行语句直接导入即可。

```python 
	import sqlite3
```

## 2、打开数据库

&emsp;&emsp;在python中，使用sqlite3创建数据库的连接，当我们指定的数据库文件不存在的时候连接对象会自动创建数据库文件；如果数据库文件已经存在，则连接对象不会再创建数据库文件，而是直接打开该数据库文件。<font color=#ff00 size=3 face="黑体">连接对象可以是硬盘上面的数据库文件，也可以是建立在内存（memory）中的，在内存中的数据库执行完任何操作后，都不需要提交事务的(commit)</font>

&emsp;&emsp;connect方法返回con对象，即是数据库链接对象，它提供了以下方法：

|方法|描述|
|-|-| 
|.cursor()|创建一个游标对象 |
|.commit()|处理事务提交| 
|.rollback()|处理事务回滚| 
|.close()|关闭一个数据库连接|

### 2.1、在硬盘上建立数据库

方法一：

```python 
	con=sqlite3.connect("E:\Test.db")
```

&emsp;&emsp;注意： `E:\Test.db` 与 `E:\\Test.db` 与 `E:\TEST.db` 均相同。由此可见<font color=#ff00 size=3 face="黑体">数据库的名称不区分大小写，且以第一次建立时的名字为准。</font> 但需要注意的是： `E:\test.db` 会报错，因为编译器会识别到 `\t` 为制表符，因此认为路径不对。

方法二：

```python 
	con=sqlite3.connect("Test.db")
```

&emsp;&emsp;不加全路径时，数据库文件会自动建立在工程项目文件夹下。

### 2.2、在内存上建立数据库


```python 
	con=sqlite3.connect("memory")
```

## 3、创建游标

&emsp;&emsp;游标对象有以下方法支持数据库操作： 

|方法|描述|
|-|-|
|.execute()|用来执行sql语句| 
|.executemany()|用来执行多条sql语句|
|.close()|用来关闭游标| 
|.fetchone()|用来从结果中取一条记录，并将游标指向下一条记录| 
|.fetchmany()|用来从结果中取多条记录。| 
|.fetchall()|用来从结果中取出所以记录。| 
|.scroll()|用于游标滚动。|

&emsp;&emsp;创建游标示例：
```python 
	cur=con.cursor()
```

## 4、执行SQL语句

### 4.1、创建表

&emsp;&emsp;<font color=#ff00 size=3 face="黑体">示例中所有的大写字符为SQL语法标准，小写字符为用户自定义的字符，但由于SQL语句不区分大小写，所以将SQL标准语句小写也可以。</font>

方法一：

```python 
	cur.execute("CREATE TABLE IF NOT EXISTS test(id INTEGER PRIMARY KEY,name TEXT,age INTEGER)")
```

方法二：

```python 
	cur.execute("CREATE TABLE test(id INTEGER PRIMARY KEY,name TEXT,age INTEGER)")
```

&emsp;&emsp;注意：<font color=#ff00 size=3 face="黑体">如果使用方法二（不加 `IF NOT EXISTS`），当项目中存在相同的表时会报错，所以为了省略检查表是否已建立的过程，建议使用方法一。</font>

### 4.2、新增数据

方法一

```python 
	data = "5,'leon',22"
	cur.execute('INSERT INTO test VALUES (%s)'%data)
```

方法二

```python
	cur.execute("INSERT INTO test values(?,?,?)",(6,"zgq",20))
```

方法三

```python
	cur.executemany('INSERT INTO test VALUES (?,?,?)',[(3,'name3',19),(4,'name4',26)])
```

### 4.2、更新数据

方法一：

```python
	cur.execute("UPDATE test SET name=? WHERE id=?",("nihao",1))
```

方法二：

```python
	cur.execute("UPDATE test SET name='haha' WHERE id=1")
```

### 4.3、删除数据

方法一：

```python
	n=cur.execute("DELETE FROM test WHERE id=?",(1,))
```

方法二：


```python
	n=cur.execute("DELETE FROM test WHERE id=2")
```

&emsp;&emsp;返回的n为游标对象

### 4.4、查询数据

```python
	cur.execute("SELECT * FROM test")
```

&emsp;&emsp;查询的结果存储在游标对象cur中，可以使用对象的方法进行访问。

### 4.5、删除表

```python
	cur.execute("DROP TABLE Test ")
```

## 5、查询并显示数据

### 5.1、全部显示

```python
	cur.execute("select * from Test")
	for item in cur:
    	print(item)
```

或

```python
	print(cur.fetchall())
```

### 5.2、显示一条

```python
	print(cur.fetchone())
```

### 5.2、显示多条

```python
	print(cur.fetchmany(3))
```

&emsp;&emsp;<font color=#ff00 size=3 face="黑体">注意：使用游标的方法返回的数据类型是列表。</font>

## 6、事务提交或回滚

### 6.1、提交

```python
	con.commit()
```

### 6.2、回滚

```python
	con.rollback()
```

## 7、关闭数据库连接和游标

```python
	cur.close()
	con.close()
```

&emsp;&emsp;注意：<font color=#ff00 size=3 face="黑体">一定要先关闭游标，再关闭数据库连接，否则会报错！</font>
