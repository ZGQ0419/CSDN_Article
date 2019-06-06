[@TOC]

&emsp;&emsp;在学习Python的过程中，总是会涉及到模块调用与函数使用。因为每一个函数涉及到参数数量变化问题，类似与Java语言的函数重载。例如：在使用randrange()函数时，查阅函数使用方法为：

```python
	randrange([start],stop[,step])
```

&emsp;&emsp;由示例可得，该函数最多可以传入三个函数，分别为 `start` , `stop` , `step` 。 但为什么会有 `[]` 这个符号呢？经过了解发现，这是用来标识参数可选的符号。也就是说：

<font color=#ff00 size=3 face="宋体">1、不带 `[]` 的参数是必须传入的，优先级最高；
2、而带有 `[]` 符号的参数可以选择不传入，优先级第二；
3、使用类似 `[,]` 的参数优先级最低。</font>

也就是说如果函数示例传入一个参数，则表示stop参数。

```python
	randrange(10)
```

传入两个参数时，则表示start和stop参数。

```python
	randrange(1，10)
```

传入三个参数时，则表示start、stop、step参数。

```python
	randrange(1，10，2)
```