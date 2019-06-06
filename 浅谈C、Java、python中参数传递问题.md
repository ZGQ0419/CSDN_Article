[@TOC]

# 写在前面

&emsp;&emsp;在近期学习python时，突然想到一个问题：python函数在传参时是值传递还是引用传递？先科普一下什么是值传递，什么是引用传递，已了解的请直接跳过。

<font color=#ff00 size=3 face="宋体">**1、值传递（passl-by-value）：**</font>被调函数的形式参数作为被调函数的局部变量处理，即在堆栈中开辟了内存空间以存放由主调函数放进来的实参的值，从而成为了实参的一个副本。值传递的特点是被调函数对形式参数的任何操作都是作为局部变量进行，不会影响主调函数的实参变量的值。<font color=#ff00 size=3 face="宋体">简言之就是：主函数中把实参的值传递给形参，形参开辟新内存来存储值，而不影响实参的值。</font>

<font color=#ff00 size=3 face="宋体">**2、引用传递(pass-by-reference)：**</font>被调函数的形式参数虽然也作为局部变量在堆栈中开辟了内存空间，但是这时存放的是由主调函数放进来的实参变量的<font color=#ff00 size= face="宋体">**地址**</font>。被调函数对形参的任何操作都被处理成间接寻址，即通过堆栈中存放的地址访问主调函数中的实参变量。正因为如此，被调函数对形参做的任何操作都影响了主调函数中的实参变量。<font color=#ff00 size=3 face="宋体">简言之就是：主函数中把实参的地址传递给形参，形参与实参共用同一物理地址，而影响实参的值。</font>

&emsp;&emsp;为了更好记忆，使用C语言、Java和python三者对比的方法进行讨论。

# C语言参数传递

&emsp;&emsp;C语言应该是最好理解的，因为它直接将值与地址（指针）分开，因此直接传变量的值和传变量地址分别对应着值传递与引用传递。如下表所示：

|传递方式|描述|
|:-:|:-:|
|传变量|该方法是传递变量的值，形参与实参指向不同地址，属于值传递类型。|
|传指针|该方法是传递变量的地址，使形参与实参共用同一地址，因此是引用传递类型。|

<font color=#0422ff size=4 face="黑体">1、值传递</font>

&emsp;&emsp;<font color=#ff00 size=3 face="宋体">C语言传递变量是值传递，实参将值传递给形参时，形参单独开辟新内存来创建实参的副本，从而不影响实参的值。</font>示例如下：

```C
	#include<stdio.h>
	int test(int b);	

	int main(){
		int a=1;
		printf("before：a的地址为：%d\n",&a);
		printf("before：a的值为：%d\n",a);
		test(a);
		printf("after：a的地址为：%d\n",&a);
		printf("after：a的值为：%d\n",a);
		return 1;
    }
    int test(int b){
		printf("b的地址为：%d\n",&b);
    	printf("b的值为：%d\n",b);
		b=2;
		printf("b的地址为：%d\n",&b);
		printf("b的值为：%d\n",b);
		return b;
    }

	//结果
	before：a的地址为：1703724
	before：a的值为：1
	b的地址为：1703644
	b的值为：1
	b的地址为：1703644
	b的值为：2
	after：a的地址为：1703724
	after：a的值为：1
```

&emsp;&emsp;由程序执行结果可得：实参a的地址与形参b的地址不同，改变形参b的值不改变实参a的值，两者互不影响。

<font color=#0422ff size=4 face="黑体">2、引用传递</font>

&emsp;&emsp;<font color=#ff00 size=3 face="宋体">C语言传递指针是引用传递，形参与实参共用同一地址，因此实参与形参彼此相互影响。</font>示例如下：
```C
	#include<stdio.h>

	int test(int b[]);
	int main(){
	int a[2]={0,1};
	printf("a的地址为：%d\n",a);
	printf("before:a[0]的值为：%d\n",a[0]);
	test(a);
	printf("after:a[0]的值为：%d\n",a[0]);
	return 1;
	}

	int test(int b[]){
	printf("b的地址为：%d\n",b);
	printf("b[0]的值为：%d\n",b[0]);
	b[0]=2;
	printf("b[0]的值为：%d\n",b[0]);
	return 1;
	}

	//结果
	a的地址为：1703720
	before:a[0]的值为：0
	b的地址为：1703720
	b[0]的值为：0
	b[0]的值为：2
	after:a[0]的值为：2
```

&emsp;&emsp;由程序执行结果可得：传递数组时，实际是传递指针的操作。形参b与实参a共用 `1703720` 这个地址，因此相互影响。此外还有结构体传参的方式，结构体传递也分值传递与引用传递，详细可以参考这篇文章：[https://blog.csdn.net/lin37985/article/details/38582027](https://blog.csdn.net/lin37985/article/details/38582027)

# Java参数传递

&emsp;&emsp;Java中参数传递与其他语言不同，它只有<font color=#ff00 size=3 face="黑体">值传递，没有引用传递。</font>但这不影响它进行类似引用传递的操作。当Java传递的参数是对象时便可以达到类似引用传递的效果。如下表所示：

|参数类型|描述|
|:-:|:-|
|基本类型|传递的是基本类型的字面量值的拷贝。简单的int,long,float数据类型都属于基本类型|
|引用类型|传递的是该参量所引用的对象在堆中地址值的拷贝。类的对象，字符串等数据为引用类型|


<font color=#0422ff size=4 face="黑体">值传递</font>：

<font color=#ff00 size=4 face="宋体">1、基本类型</font>

```java
	package test;

	public class Test {
		public static void main(String[] args) {
			// TODO 自动生成的方法存根
			int a=1;
			System.out.println("before a的值:"+a);
			new Test().test(a);
			System.out.println("after a的值:"+a);
		}
		public void test(int b) {
			System.out.println("before b的值:"+b);
			b=2;
			System.out.println("after b的值:"+b);
		}
	}
	//结果
	before a的值:1
	before b的值:1
	after b的值:2
	after a的值:1
```

&emsp;&emsp;由程序运行结果可得，在基本类型中，进行的是值传递，形参b并不改变实参a的值。

<font color=#ff00 size=4 face="宋体">2、引用类型</font>


```java
	package test;

	public class Test {
		public static void main(String[] args) {
			// TODO 自动生成的方法存根
			Func func=new Func();
			System.out.println(func.num);
			new Test().test(func);
			System.out.println(func.num);
		}
		public void test(Func b) {
			b.num=1;
		}
	}
	class Func {
		int num=0;
	}
	//结果
	0
	1
```

&emsp;&emsp;由程序运行结果可得，当方法中传入的是类的对象时，则进行的是类似指针操作，通过对象可以直接修改