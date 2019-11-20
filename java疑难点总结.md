@[toc](本文目录)

# 前言

&emsp;&emsp;大家好，我是工程小猿！之前在学习Java语言的过程中总是遇到一些问题，比如在看基础知识时，发现它和C语言基本语法差别不大，除了没有C语言中[指针](https://baike.baidu.com/item/%E6%8C%87%E9%92%88/2878304?fr=aladdin)的概念和增加内存自动回收从而避免了[内存泄漏](https://baike.baidu.com/item/%E5%86%85%E5%AD%98%E6%B3%84%E6%BC%8F)外，其余基本语法相差无几。但是学习完全部Java语言后发现除了对类C的基础知识熟记外，对

 1. 封装
 2. 重载
 3. 构造方法
 4. 继承
 5. 接口
 6. 多态 

&emsp;&emsp;等Java独有的基础概念理解不够深刻，对每个概念在Java虚拟机中的运算过程一知半解，对这些概念的细节把握不清会直接导致在编码过程中出现bug。由于本人今年出参加了东北大学的计算机复试，所以结合东大复试考题系统详细得复习了Java语言。做了一些关于Java语言学习中的疑难点总结，分享出来希望能够帮助到有需要的人，同时也能使自己时刻复习与总结。

# Java基础疑难点

**1**：标识符：标识符只能以字母、“_”和“$”开头。可以使用汉字作为标识符(不推荐，尽  &emsp;&emsp;量不用)。 汉字标识符不能用作类名和接口名

**2**：变量名：Java中没有goto、const这些关键字，但不能用goto、const作为变量名。

**3**：float类型占用4字节，写可以修饰整数，分数，小数（小数时后面必须加f）

**4**：boolean类型有自己的运算，不能参与其他数据类型之间的运算。If(1):错误的

**5**：变量类型兼容性：

&emsp;**(1)**:double(8字节)> long(8字节) > float(4字节) > int(4字节) > char (2字节)>short(2字节)>byte(1字节) Boolean (1bit) “小”的数据类型可以直接赋值给“大”的数据类型，“大”的数据类型不能直接复制给“小”的数据类型(编译错误),char (2字节)可以赋值给long和int，但是不能赋值给short和byte(编译错误),boolean与其他数据类型之间没有兼容性，byte的范围为-128～127。

&emsp;**(2)**: 所有byte型、short型和char型的值将被提升到int型。

**6**：变量作用域：

```java
       {
            int x = 4;
            //这之间只有x可以访问
            int y = 1;
            //这里x和y可以访问
            {
            	int z = 2;
            	//x、y、z都可以访问
            	z = 5;
            }
            x = 4   
            /这里/只有x和y可以访问，不可以访问z
         }
```

**7**：逻辑运算符：
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019050308235335.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)

**8**：算术左移、算术右移：<<  >>	逻辑右移：>>>位移运算只能应用于整数类型与char类型，不能应用于浮点类型和boolean类型>>与>>>的区别是：>>在右移时最左侧填入原来的最高位，>>>在右移时最左侧填入0，对于int型整数移位a>>b，系统先将b对32取模，对于long型整数移位时a>>b ，则是先将移位位数b对64取模。

**9**：局部变量(临时变量)在使用之前必须被初始化，否则会出现编译错误


# Java面向对象疑难点

**1**：封装：
&emsp;&emsp;通过将类的实例变量声明为私有的（private），再提供一个或多个公有（public）方法实现对该实例变量的访问或修改，这种方式称为封装。

**2**：重载：
&emsp;&emsp;重载的多个方法必须要有不同的参数表，只能通过参数表分辨，不能通过返回值。

**3**：构造方法：
（1）构造方法在创建对象时被自动调用
（2）构造方法的功能通常是进行对象的初始化工作，在构造方法执行之后才完成对象的创建
（3）一个类一定有至少一个构造方法，如果程序没有明确定义一个构造方法，编译器会自动生成一个缺省的的构造方法
（4）构造方法的名字同类名完全一致
（5）构造方法没有返回值字段！
（6）构造方法一般都是public的,因为它们在产生对象时会被系统自动调用
（7）构造方法也可以重载
（8）如果类声明了带参数的构造方法，而没有显式定义无参的构造方法，则自动取消隐式的无参构造方法：eg:

```java
class Orange { Orange(int o) {…} }
Orange orange = new Orange();   ERROR!!
```

（9）如果父类中定义了含参的构造方法，则自动取消父类隐式的构造方法，并且子类必须定义含同样参数的构造方法，并在方法内写入super(参数1，参数2.......) 。
  (10) 子类初始化时无论调用无参或含参构造方法都必须调用父类的无参构造方法。

**4**;this关键字：
（1）在类的定义中，this代表当前正在处理的对象
（2）构造方法互相调用时，方法名称应该使用this来替代

**5**：内存管理：
（1）在创建对象时JVM为对象分配所需的内存，这些内存将一直被占用着，直到垃圾回收器将其回收。Java中不需要自己释放对象占据的内存，JVM会自动利用垃圾回收机制回收不再使用的对象占据的内存
（2）JVM采用mark-sweep-compress方法工作
（3）垃圾回收时系统自动进行的，通常不需要程序员干预
（4）垃圾回收可能在任何时间进行，进行垃圾回收的时机由JVM决定，程序员不能加以干涉
（5）不同版本的JVM有着不同的垃圾回收方式，不能对垃圾回收方式加以任何假定

**6**：数组：
Java中的数组是对象，数组类型属于引用类型

**7**：静态变量和方法
（1）不能在类的静态方法中直接访问类中的变量或方法，除非被访问的成员也是静态
（2）不论通过引用还是通过类名来访问，访问到的静态变量都是同一个

**8**：内部类：
（1）静态内部类：是类的成员，因此静态内部类可以直接访问包含它的类中的所有静态成员，包括private和protected成员；但是，在包含它的类不能直接访问静态内部类的成员。作为类的静态成员，不能在静态内部类中直接访问 包含它的类的非静态成员
（2）成员内部类：类似于定义一个类的普通成员
成员内部类可以访问外部类中的所有成员，不论静态成员还是非静态成员；而外部类不能直接访问成员内部类的成员。
在成员内部类的方法中this是内部类当前对象的引用，如果需要访问当前的外部类对象需要使用 外部类.this
（3）本地内部类：是定义在方法中的内部类，本地内部类只能在定义它的方法中使用，而且不能使用public,private等访问限定符限定本地内部类，本地内部类可以访问Enclosing Class中的所有成员，不论静态成员还是非静态成员；而Enclosing Class中不能直接访问本地内部类的成员。
（4）匿名内部类：没有名字的内部类

**9**：继承：
&emsp;（上溯造型）

    A x = new B(); // 子类当父类使用

&emsp;&emsp;引用x指向B的对象，但是x的类型是A
&emsp;&emsp;用对象x调用方法时，调用的是子类的方法，
&emsp;&emsp;用对象x调用属性时，调用的是父类的属性

**10**：super：
&emsp;&emsp;super关键字代表当前对象的父（超）类部分：使用super调用构造方法时，调用语句必须是构造方法的第一条语句。

**11**:final关键字：
&emsp;&emsp;  Final修饰的类可以被实例化，但不能被继承
&emsp;&emsp;  Final修饰的方法可以被重载，不能被重写（覆盖）
&emsp;&emsp;  Final修饰过的变量是不能修改的常量

**12**：==运算符判断两个变量是否引用同一对象，（类似于指针）；而equals（）判断两个对象是否值相等。

**13**：多态：父类的某个方法被其子类重写时，可以各自产生各自的功能行为。

**14**：抽象类与抽象方法：
（1）不能创建抽象类的对象
（2）如果一个类中有抽象方法，那么这个类必须被声明为抽象的(abstract)
（3）从抽象的超类继承的类，通常必须实现超类中所有的抽象方法，否则 继承类也必须声明为抽象的。

**15**：接口interface：只包含常量和抽象方法的抽象类；不可以有构造方法。
（1）接口中的所有方法都是public方法，不能使用其他的访问控制符
（2）接口中的所有方法都是抽象(Abstract)方法，不能使用final关键字说明
（3）即使不使用任何关键字说明，接口中的所有数据成员都是public static final

**16**：访问控制：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190503083412861.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)

**17**：异常(Exception)：
（1）基本的异常处理结构，try / catch关键字

```java
	try{
	//有可能产生异常的代码
	}catch (SomeException e){
	    //处理异常的代码
       }
       catch (AnotherException e){
	    //处理异常的代码
       }
```

&emsp;&emsp;在捕获同一继承体系中的多个异常类的时候，需要将捕获继承类的catch块置于捕获超类的catch块之前，否则会在编译时产生错误：
Eg:      //出错，超类(IOException)在前，继承类(FileNotFoundException )在后了

```java
    catch(IOException e){
    }
    catch(FileNotFoundException e){
    }
```

只有使用System.exit(0),才不执行Finally才不执行

（2）“throw”与“throws”区别: 
&emsp;&emsp;Throw：用在方法内，后面跟着的是异常对象，用在方法内。
&emsp;&emsp;Throws：用在方法上，后面跟着异常类名，用在方法上。 
&emsp;&emsp;如果方法内有Throw处理，那么方法上一定要用Throws声明。否则编译失败。  

**18**：main中参数问题：
&emsp;&emsp;参数String[ ] args(String args[])的作用就是可以在main方法运行前将参数传入main方法中。从控制台，输入编译执行命令时传参数：java xxx hello world 则arg[0]为hello；arg[1]为world。去掉[ ] 可以编译和运行，但接收不到参数。

**19**：System.out.println函数自动执行换行  System.out.print("\n");等同于System.out.println("");

**20**：一个类中 静态代码块、构造代码块、构造方法的执行流程：
&emsp;(1)静态代码块 > 构造代码块 > 构造方法
&emsp;(2)静态的内容是随着类的加载而加载，静态代码块的内容会优先执行
&emsp;(3)子类初始化之前先会对父类进行初始化



# 打印简单图形
### 1：倒三角
```java
public class Test_2017_3 {
	public static void main(String[] args)
	{	
		int h=7;   //行数
		int l=13;  //列数
		for(int i=0;i<h;i++){
			for(int n=0;n<i;n++)
				System.out.print(" ");
			for(int j=i;j<l;j++){
				System.out.print("*");
			}
			l--;
			System.out.print("\n");
		}
	}
}

输出：
*************
 ***********
  *********
   *******
    *****
     ***
      *
```
 ### 2：空心菱形
```java
 public class Test {
	public static void main(String arg[]){
		int count=0;
		for(int i=0;i<9;i++){
			//添加每行数字前的空格
			if(i<=4){
				count++;
				for(int j=0;j<4-i;j++)
					System.out.print(" ");
			}else{
				count--;
				for(int j=0;j<i-4;j++)
					System.out.print(" ");
			}
			//写数
			if(i==0||i==8){
				System.out.println(count);
			}else{
				//前5行
				if(i<=4){
					System.out.print(count);
					for(int j=0;j<2*i-1;j++)
						System.out.print(" ");
					System.out.println(count);
				}
				//后5行
				else{
					System.out.print(count);
					for(int j=0;j<15-2*i;j++)
						System.out.print(" ");
					System.out.println(count);	
				}
			}
		}
	}
}

输出：
    1
   2 2
  3   3
 4     4
5       5
 4     4
  3   3
   2 2
    1
```
### 3：实心菱形
```java
public class Test_2014_3 {
	public static void main(String[] args){
		int h=7;   //行数
		for(int i=0;i<h;i++){
			if(i<4){
				for(int c=0;c<3-i;c++)
			       System.out.print(" ");
				for(int j=0;j<2*i+1;j++)
					System.out.print("*");
				System.out.print("\n");
			}else{
				for(int a=0;a<i-3;a++)
				   System.out.print(" ");
				for(int j=0;j<(13-2*i);j++)
					System.out.print("*");
				    System.out.print("\n");
			}
		}
		
	}
}

输出：
   *
  ***
 *****
*******
 *****
  ***
   *

```
### 4：实心正三角形
```java
package code_for_exam;
import java.io.IOException;
import java.util.Scanner;

public class first {
	public static void main(String[] args) { 
			int i = 0;
			try {
				i = GetInput();
			} catch (MyException e) { 
				e.printStackTrace();
			}
			Triangle tr =new Triangle();
			tr.PrintTriangle(i);
	}
	// 得到控制台输入
	public static int GetInput() throws MyException{
		System.out.println("请输入三角形高度：");
		int i = 0;
		Scanner sc = new Scanner(System.in); 
		i = sc.nextInt(); 
		if(i == 0) {
			throw new MyException("输入错误！");
		}
		return i;
	}
}
//定义三角形输出类
class Triangle {
	public void PrintTriangle(int l) {
		//输出每行
		for(int i=0;i<l;i++) {
			//最后一行
			if(i==l-1) {
				for(int j=0;j<2*l-1;j++) {
					System.out.print("*");
				}
			}else {
				//第一行
				if(i==0){
					for(int j=i; j<l-1;j++) {
						System.out.print(" ");
					}
					System.out.println("*");	
				}else {	//中间行
					for(int j=i; j<l-1;j++) {
						System.out.print(" ");
					}
					System.out.print("*");
					
					for(int k=0;k<2*i-1;k++) {
						System.out.print(i);
					}
					System.out.println("*");	
				}	
			}
		}
		
	}
}	
// 自定义异常类
class MyException extends Exception{
	public MyException(String msg) {
		super(msg);
	}
}
输出：
请输入三角形高度：
7
      *
     *1*
    *222*
   *33333*
  *4444444*
 *555555555*
*************
```



# word版下载

&emsp;&emsp;此总结属于个人对Java学习的见解，如有错误，欢迎通过评论批评指正！另附此篇文章的word版本的下载地址：https://download.csdn.net/download/guoqizhang/11092765