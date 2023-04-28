#   JAVA学习笔记

##  JAVA概述

###  JVM和垃圾回收机制

 - JVM

   java语言的特点：==跨平台性==

   ​	java程序可以在win、linux、mac上都可以运行的原因是因为java程序运行在jvm上，而不同os上面都会安装jvm

   > 但是针对于不同os的jvm是不同的
   >
   > JVM跑在os上面

- 垃圾回收

  c语言中需要程序员手动进行free无用的内存，但是java语言，会自动进行内存的回收

  > 但是即使java语言会自动回收内存但还是可能会出现内存泄漏和内存溢出

​		**并且可能会出现有的内存无法回收的情况**



### JDK、JRE、JVM的关系

 - JDK ==编写java程序==

​		Java Development kit   即java开发工具包

​		JDK是提供给java开发人员使用，包括了java开发工具和JRE    

 - JRE ==运行java程序==

​		Java Runtime Enviroment  即java运行环境

​		包括JVM和java程序所需要的类库

 - JVM  ==java虚拟机==

>JDK 包含 JRE
>
>JRE 包含 JVM



### 环境配置

​		运行一个java程序都需要调用JDK中bin目录下的java.exe 、 javac.exe 、javadoc.exe文件，而在cmd中我们知道必须要在对应目录下才能执行该目录下的exe文件

> 也就是说在c盘的根目录下运行java.exe会显示：
>
> java.exe 不是内部或外部指令，也不是可运行程序或批处理文件

​	   

  -  目的：==为了能够在所有地方都能运行这三个exe文件==

  - Path环境变量：==windows执行命令时需要搜索的路径==

>
>
>所以只需要将JDK的bin目录添加到path环境变量中即可，不同路径用分号隔开
>
>先找当前目录，再找path路径

- JAVA_HOME

  但是对于java开发人员来说，一般不会在path中添加bin目录，而是新建一个环境变量名JAVA_HOME值为bin的父目录，在path中引用JAVA_HOME

  >  在path环境变量中添加：%JAVA_HOME%bin
  >
  > 且一般选择将JAVA_HOME置顶

    - 原因：在服务器开发的时候会识别JAVA_HOME变量

- JDK的选择

  在计算机上课可以安装多个版本的JDK，但只能使用一个JDK，具体使用哪个版本的JDK，就看环境变量中所选的是哪个JDK的bin目录



### JAVA程序的运行过程

​	==源文件== == > ==字节码文件== == >==结果==

​	过程：==.java==通过**javac.exe**进行编译为==.class==通过**javac.exe** 来解释运行产生结果



### JAVA的注释

​	单行注释和多行注释内容不参与编译

- **单行注释**

  和c相同通过//进行单行注释

- **多行注释**

​		和c相同用/* */进行多行注释

- **文档注释**（==java所特有的==）

  格式为：

  ```java
  /**
     @author 指定java程序的作者
     @version 指定源程序版本
   */
  ```

  - 作用：javadoc.exe可以提取文档注释的内容

​		

###  API文档

  - **API文档与API**：

    - **API**(Application Programming Interface) , 应用程序编程接口，是java JDK中附带的类库

    - **API文档**则是API的使用说明

​			[官方API文档下载](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

---



##  JAVA基本语法

###  关键字和保留字

		- **关键字**：被java赋予特殊含义的单词（class、public等等）
		- **保留字**：现有java未使用，但以后可能会使用（goto、const）

>
>
>在定义变量的时候需要避开、

- **标识符**：自己可以起名的地方（类名、变量名、函数名、接口名等）
  - **命名规则**：
    - 由26个英文字母大小写，0-9，_ 或$组成
    - 不能以数字开头
    - 不能使用关键字和保留字，但可以包含
    - java严格区分大小写，且长度无限制
    - 标识符不能包含空格
  - **命名规范**：
    - **包名**：多单词组合的时，==所有字母都小写==
    - **类名、接口名**：多单词组合时，==各单词首字母大写==
    - **变量名、方法名**：多单词组合时，==第一个单词首字母小写，其余单词首字母大写==
    - **常量名**：==所有字母都大写==，多单词时，==每个单词间用下划线连接==

>
>
>1.  命名规则不匹配会导致编译错误
>
>2.  命名规范不匹配不会报错，但作为一个java工程师必须得遵守行业规范
>
>3. 在起名时最好见名知意，否则最好写好注释
>
>4.  java是采用Unicode字符，所以可以使用中文命名，但不建议

### 变量

- **概念：**

  - 内存中的一个存储区域
  - 该区域的数据可以在同一类型范围内不断变化（可以重新赋值）
  - 是程序中最基本的存储单元，包含==类型、变量名、值==

- **分类：**

  ![image-20230103161311639](./JAVA学习笔记.assets/image-20230103161311639.png)![image-20230103165536655](image\image-20230103165536655.png)

  - **整数类型**：

    - bit是计算机**最小**存储单位，byte是计算机**基本**存储单元

    - 通常都声明为**int**，当不足以表示的时候才会声明为**long**

  - **浮点类型**:

    ![image-20230103170023225](image\image-20230103170023225.png)

  - **字符类型**：

    - 用' '来定义char型变量，但内部只能定义一个字符，当要定义多个字符的时候可以使用**String**

    - **转义字符**:有时候会用来定义转义字符\n,\t

    - 使用Unicode：eg：char c ='\u0043'

      在现在的编码中一般都采用Unicode映射方式来防止不同语言之间产生乱码，UTF-8是现在广泛使用的Unicode具体实现方式

  - **布尔类型**：

    - 取值true，false
    - 通常在条件判断，循环结构中使用

>​	
>
>**int**和**float**都是4字节但是表示的范围不一样的原因：int存储的全是数值，而float一部分存储的是数值一部分存储的是幂方		



- **注意：**

  - 变量需要先声明后使用，先赋值后使用

  - 变量的生存周期就是其作用域，出了作用域就会被垃圾回收

  - 不能进行定义同名变量

### 类型转化

- **自动类型转化**：

  - 不同类型进行运算的时候会自动向上类型转化

    eg：int + byte 结果为byte自动提升为int

    ==特别的：== byte、char、short做运算时其结果是int类型

- **强制类型转化**：自动类型转化的逆运算

  - 可能导致精度损失

### String

- String类型的使用：

  - string属于引用类型不属于基本数据类型
  - 声明String类型的时候用" ", eg: String s = "haha"
  - String类型可以和八种基本数据类型做运算，==但只能是连接运算==

  > 当”**+**“左右有String类型时候才是连接运算，其余情况都是加法运算

​		

### 进制的表示

![image-20230103174800939](image\image-20230103174800939.png)

### 运算符

- 算数运算符

  ![image-20230104153212546](image\image-20230104153212546.png)

  - += 、 -=等不会改变本身的数据类型

    eg：

    ​		short s1=10;

    ​		s1 = s1+2;	编译失败，将int变量赋值给了short

    ​		s1 += 2;		编译成功，s1仍然是short型

- 赋值运算符: =

  - 当 = 两边的数据类型不一致时，可以使用自动类型转换或者强制类型转换来进行处理 
  - 支持连续赋值

- 比较运算符 

  ![image-20230104154441975](image\image-20230104154441975.png)

- 逻辑运算符：只适用于boolean类型的变量之间

  ![image-20230104154746919](image\image-20230104154746919.png)

- 位运算符

- 三元运算符

  （条件）？表达式1：表达式2

  当条件为true则执行表达式1

  当条件为false则执行表达式2

### Scanner类获取参数

- 步骤：

  - 导包：import java util.Scanner;   (idea等工具会自动导包)

  - Scanner的实例化

    eg：

    ​	Scanner input = new Scanner(System.in);

    - System.in : 表示从键盘进行输入

  - 调用Scanner类的相关方法来获取变量

### 流程控制

- 流程控制中的if-else 、 switch-case 、do-while、 while 、for 和C相同则不再赘述

### Array

​		java中的数组和C语言中的数组语言定义、使用和遍历是相同的，但是由于java分配内存都需要使用new关键字，所以在数组的声明上会有区别

- **一位数组**

  - **静态初始化**

    - 在初始化的时候显示给出每个数组元素，则数组长度即为元素个数

      int [] array = new int [] {1,2,3};

  - **动态初始化**

    - 在初始化的时候只给出数组的长度而不给出每个数组元素

      int [] array = new int [5]   //动态初始化了一个长度为5的数组

  - **注意**

    - 数组的定义要么动态要么静态，不能既动态又静态，即要么new之后给数据元素不给长度，长度即元素个数；要么给数组长度不给具体数组元素;更不能都不是

      - 错误示例：

        int [] array = new int [3] {1,2,3};

        int [] array = new int []; 

    - 左边的” [] "是说明定义的是一个数组结构不能在里面放值

      - 错误示例：

        int [3] array = new int [3];

  - **数组初始值**

    - 当没有显示给出数组元素值的时候的数组默认值
      - 整形：0
      - 浮点：0.0
      - 字符：0 但是显示出来类似空格效果
      - 布尔：false
      - 引用：null

- **二维数组**

  - **静态初始化**

      - 在初始化的时候显示给出每个数组元素，则数组长度即为元素个数

        int [][] [] []array = new int [] [] {{1,2,3},{1,2}};


  - **动态初始化**

    - 在初始化的时候只给出数组的长度而不给出每个数组元素

      int [] []array = new int [5] [4]   //动态初始化了一个长度为5的数组

  - **二维数组长度**

    - 以int [][] [] []array = new int [] [] {{1,2,3},{1,2}}; 为例子

      array.length: 2					//原因二维数组的内存结构

      array[0].length:3				//下标0的数组元素对应的一维数组长度

  - **二维数组的遍历**

    - 与C不同，java二维数组的遍历以下示代码为例

      >
      >
      >for(int i=0;i<array.length;i++){
      >			for(int j =0;j<array[i].length;j++){
      >				System.out.print(array[i][j]);
      >			}
      >			System.out.println();
      >		}

## 查找算法

### 线性查找

​		即是通过一个for循环挨个查找看是否equals就可

### 二分查找

​		又称“折半查找”

- 前提：所要查找的数组必须是有序的（以升序为例）
- 通过通过一个循环，建立两个索引，一个head，一个end，每次比较中值和目标值，如果目标值大于中值，则将head修改为中值索引再进行查找，直到找到或找完所有数据都不匹配为止

​		

## 排序算法

### 概念

- 衡量指标
  - 时间复杂度：分析关键字的比较次数和记录的移动次数
  - 空间复杂度：分析算法需要多少辅助内存
  - 稳定性：当两数相等时，原数据中先出现的应当排在结果的前置位，满足则称该算法是稳定的，反之不稳定（或称不安全）
- 简单分类
  - 内部排序：
    - 整个排序过程只需要占用内存不需要借助外存
  - 外部排序：
    - 当数据量非常大的时候，在借用内存的同时还需要借用外存，最常见的是多路归并排序

### 交换排序

#### 冒泡排序

​		每次比较相邻两个元素，每次确定一个元素的具体位置，先最大，再次大运行下去，具体实现即两层for循环

#### 快速排序

> ```java
> public static void qSort(int a[],int begin,int end){
>     if(begin > end){
>         return;
>     }
>     int flag=a[begin];
>     int i=begin;
>     int j=end;
>     while(i<j){
>         while(flag<=a[j] && i<j){
>             j--;
>         }
>         while(flag>=a[i] && i<j){
>             i++;
>         }
>         if(i<j){
>             int temp=a[j];
>             a[j]=a[i];
>             a[i]=temp;
>         }
>     }
>     a[begin]=a[i];
>     a[i]=flag;
>     qSort(a,begin,i-1);
>     qSort(a,i+1,end);
> 
> }
> ```

==注意==：

​		在头尾指针进行移动的时候，一定是尾指针先进行移动

​		**原因**：

​		因为先移动的指针一定会等待后移动的指针，那么指针相交的		位置一定是先移动的指针（首指针）先停止的位置，这里先移		动的指针是首指针，它的停止条件是指针指向的元素>基准元		素，那么最终停止的位置（指针相交位置）的元素也是大于基		准元素的情况，即

![image-20230211195236030](image\image-20230211195236030.png)



## 面向对象

### 概述

java面向对象的三大主线

- 类和类的成员：属性，方法，构造器，代码块，内部类
- 面向对象的三大特性：封装性，继承性，多态性
- 其他的关键字：this，super，static，final，abstract，interface，package，import

区分面向对象和面向过程：

​	以“把大象装进冰箱为例”

- 面向过程的最小单元是函数，考虑事情怎么做

  - 开门
  - 放大象
  - 关门

- 面向对象的最小单元是类和对象，考虑事情谁来做

  - 人{

    ​		打开（冰箱）{

    ​			冰箱.open()

    ​		...

    ​		}

    ​		抬起（大象）{

    ​		...

    ​		}

    ​		关门（冰箱）{

    ​		...

    ​		}

    }

  - 冰箱{

    ​			open(){

    ​			...

    ​			}

    }

  - 大象{

    ​			进入（冰箱）{

    ​			...

    ​			}

    }



### 类和对象

- 类：对一类事物的描述，是抽象的，概念上的定义，称(class)
- 对象：是类具体存在的个体，又称实例(instance)



#### 类的设计

- 设计类：也就是设计类的成员，主要就是属性和行为
  - 属性：类中的成员变量
  - 行为：类中的成员方法

#### 类和对象的使用

- 创建类，设计类的成员
- 创建类的对象
- 通过对象调用类的属性，方法等

#### 类和多个对象之间的关系

- 每个对象都在堆中进行创建，每个对象都有自己的属性（非static），默认为null
- 对象可以之间为其他对象赋值，但两个对象都指向堆空间的同一块地址，当一个对象发生改变时，另一个对象随之改变

#### 对象的内存解析

- 堆：存放对象实例
- 栈：存放局部变量
- 方法区：存放类信息，常量，静态变量

#### 类中属性的使用

- 属性（成员变量） vs 局部变量
  - 相同点：
    - 定义的格式相同
    - 先声明后使用
    - 都有各自的作用域
  - 不同点：
    - 在类中成名的位置不同
      - 属性声明在类的{}内部
      - 局部变量声明在方法内，方法形参，代码块内，构造器形参，构造器内部
    - 权限修饰符不同
      - 属性：在声明属性时可用public , private , protected , 缺省来修饰
      - 局部变量：不可以使用权限修饰符
    - 默认初始化值不同
      - 属性：根据其类型有各自的初始化值
      - 局部变量：没有初始化值，所以在调用之前必须显示初始化
    - 在内存中加载的位置不同：
      - 属性：加载在堆空间中(非static)，static属性放在方法区
      - 局部变量：加载在栈空间中



### 类中方法的声明和使用

- 方法的声明： 权限修饰符  返回类型  方法名  （形参）{

​									方法体

​								}

> static , final , abstract , 修饰的方法后续再展开
>
> 以上的部分是每个方法所必须的

- 权限修饰符：public , private , protected , 缺省
- 返回值类型：
  - 有返回值：
    - 如果方法有返回值，则需要再方法声明的时候指定返回值的类型，并通过return来进行返回所指定的变量或者常量
  - 无返回值：
    - 在方法声明时用void声明，在方法中通常不需要用return，若用return则用“return；” 后不接表达式来告诉方法结束
- 方法名：
  - 属于标识符，应当“见文知意”
- 形参列表：
  - 形参可声明0个，1个或者多个，每个形参用逗号隔开
- 方法的使用：
  - 可以调用当前类的属性或方法
  - 方法中不可以定义一个新的方法



### 对象数组

形如： Student [] =new student[20]  //定义了20个学生对象的对象数组

>
>
>```java
>public class Student {
>    int id;
>    int grade;
>    double score;
>}
>
>  Student [] stu=new Student[20];//声明对象数组
>        for(int i=0;i<stu.length;i++){
>            stu[i]=new Student(); //初始化每一个对象
>            stu[i].id=(int) Math.random();
>            stu[i].grade=(int) Math.random();
>            stu[i].score=Math.random();
>        }
>```



### 方法的使用

#### 方法的重载

- 定义：方法名是一样的，通过不同的形参列表来区分不同的方法

- 总结：两同一不同

  - 类名和方法名相同

  - 参数列表不同：类型，个数

    >
    >
    >与形参名字无关，int，string和string，int也不同

>
>
>```java
>public class test1 {
>    public  static  void main(String [] argc){
>        int [] a1=new int[]{1,2,3};
>        char[] a2=new char[]{'a','b','c'};
>        boolean [] a3=new boolean[]{false,true};
>        System.out.println(a1);//打印出数组地址，调用public void println(Object x)
>        System.out.println(a2);//打印出abc，调用public void println(char[] x)
>        System.out.println(a3);//打印出数组地址，调用public void println(Object x)
>    }
>}//对println的重载
>```



#### 可变个数的形参列表

- 出现于方法形参的类型确定，但是个数不定的情况，常常使用于数据库修改的sql语句

  - 形如（参数类型...参数名）

    >
    >
    >```java
    >public class ArgsTest {
    >    public static void main(String[] args) {
    >        ArgsTest test=new ArgsTest();
    >        test.print();
    >        test.print(1);
    >        test.print(1,2);
    >    }
    >    public void print(int ... num){
    >        System.out.println(2002);
    >    }
    >}//均会输出2002
    >```

- 说明：

  - 可变个数可以是0,1。。。

  - 当有确定匹配的时候会先调用（方法重载）

  - 与类型相同的数组参数不能构成重载，会产生报错

  - 对于可变个数形参就可以将其视为对应的数组即可，也就是说第一个实参值为num[0]

  - 形参列表只能出现在参数的后面

  - 至多只能出现一个可变的形参列表

    >
    >
    >```java
    >public void print(int i,int ... num){
    >    System.out.println(123);
    >}
    >public void print(int ... num,int i){
    >    //这样就会报错
    >}
    >```

   >
   >
   >```java
   >public class ArgsTest {
   >    public static void main(String[] args) {
   >        ArgsTest test=new ArgsTest();
   >        test.print();
   >        test.print(1);//就会输出1234，而非2002
   >        test.print(1,2);
   >    }
   >    
   >    public void print(int i){
   >        System.out.println(1234);
   >    }
   >//    public void print(int [] a){
   >//        
   >//    }//第三条报错
   >    public void print(int ... num){
   >        System.out.println(2002);
   >    }
   >}
   >```

#### 参数值的传递

- 值的传递

  ```java
  int m=10;
  int n=m;
  //m的修改不会引起n的变化，两者都在栈中各自生成
  ```

- 引用数据类型

  - 数组的引用

  ```java
  int [] arr1=new int[]{1,2,3,4};
  int [] arr2=arr1;
  arr1[0]=1000;
  //当修改arr1时arr2也会跟着被修改，两者都指向堆中的同一块内存区域，所以一个改另一个也会跟着变化
  ```

  - 对象的引用

    ```JAVA
    class haha{
        public  int i;
    }
    haha h1=new haha();
    h1.i=10;
    haha h2=h1;
    h1.i=100;//h2.i也同样为100，其原理和数组的引用类似
    ```

- 形参和实参的传递
  - 值传递：调用方法时传递的是基本数据类型，给的是值（形参不影响实参）
  - 引用传递：调用方法传递的是对象，数组等，给的是地址（形参影响实参）

- java参数传递的机制：值传递



#### 递归方法

- 方法又调用自己的现象称为递归

- 分类

  - 直接递归：直接在自己的方法中调用自己，如快排的实现
  - 间接递归：A调用B，B调用A

  ```java
  /*
      实现递归计算0到某个数的和
   */
  public class NumSum {
      public static void main(String[] args) {
          NumSum n=new NumSum();
          System.out.println(n.getSum(100));
      }
      public int getSum(int num){
          if(num==0){
            return 0;
          }
          return getSum(num-1)+num;
      }
  }
  ```

- 斐波那契数列 

  ```java
  public int Fbnc(int num){
      if(num==1){
          return 1;
      } else if (num==2) {
          return 1;
      }else{
          return Fbnc(num-1)+Fbnc(num-2);
      }
  }
  ```

- 缺点
  - 递归调用会占用大量的系统堆栈，内存的消耗较多，当调用层次过多时，速度会比循环更慢
  - 在要求“高性能”的情况下需要尽量避免递归调用

### import和package的使用

- package：

  - 作用：工程项目中可能有上千个类，管理这些类就会十分繁琐，引入package的概念之后就可以将不同功能的类进行划分，用不同的package包裹

  - 语法格式

    ```java
    package 顶层包名.子包名
    ```

  - 注意：

    - 一个源文件只能有一个package声明语句，放于开头
    - 包名属于一个标识符，满足标识符的命名规则（全小写），见名知意
    - package声明语句中的“.”表明一层目录结构
    - 同一个包下可以声明多个类和接口，但不能定义同名的类和接口。在不同的包下是可以定义同名类和接口的

- import：

  - 为了使用其他包中的类，需要显示使用import语句引入指定包下所需要的类

  - 语法格式：

    ```java
    import 包名.类名
    ```

  - 注意：

    - 当需要导入多个类时，用";"隔开即可

      ```JAVA
      import java.util.Scanner;
      import java.util.HashMap;
      ```

    - 当需要导入该包下所有类时，用".*"即可

      ```java
      import java.util.*
      ```

    - lang包和当前包定义的类都不需要用import导入

    - 当两个包下有同名类的时候在使用的时候需要使用全类名的方式调用

      ```java
      java.sql.Date date=new java.sql.Date();
      ```

### 面向对象的特性

#### 封装性

- 引入封装性的原因：

  - 例如使用洗衣机，吹风机等，我们只需要打开开关，按相应按键就可以不需要关注电机怎么运转，线路怎么搭建，也就是说我们只需要关注对应的接口输入输出即可，不需要关注具体的内部实现。

  - 有的事物不允许外界对内部进行操作和修改，只能通过制定的方式访问修改

  - 用来实现高内聚，低耦合

    - 高内聚：类的内部数据操作自己完成，不允许外部干涉

    - 低耦合：仅暴露少量方法给外部，方便外部调用

      >
      >
      >即通过权限修饰符来把该隐藏的隐藏，该暴露的暴露出来


##### 权限修饰符

- 用private, public, protected, 缺省来修饰类已经类的内部成员

  - 使用范围

    ![image-20230316154844305](image\image-20230316154844305.png)

- 注意：
  - 外部类只能用public 和缺省进行修饰，内部类就不会有限制了
  - 类的内部成员可以用四种权限修饰符修饰

##### 构造器

- 作用：

  - 搭配new关键字，创造类的对象

    ```java
    Test test=new Test()
    ```

  - 在创建对象的时候，可以给对象的相关信息赋值（带参构造器）

    ```java
    //对于Test类
    public Test(){
    	xxx
    }//与类同名且没有返回值
    public Test(int a){
    	xxx
    }
    ```

    >
    >
    >创建类之后如果没有显示的构造器，那么编译器会生成一个默认的空参构造器，当有显示构造器之后，编译器便不会提供默认的空参构造器，也就是C++中的构造函数

##### JavaBean

- 满足以下特征的java类
  - 类是公共的
  - 有一个无参的公共的构造器
  - 有属性且有对应的set，get方法
- 功能：
  - 常用于将数据库每一个元组来生成一个对象的情况

#### 继承性

##### this关键字

- 引入原因

  - 在set方法中有可能传入的形参和属性同名，**这时为了区分属性和形参**，用this修饰的变量就是属性，反之为形参

    ```java
    public class Test{
    	private String name;
    	
    	public void setName(String name){
    		this.name=name//前者为属性，后者为形参
    	}
    }
    ```

- this可以调用的结构

  - 类的成员变量

  - 类的方法（非static方法）

    - 在该方法中调用其他方法

      ```java
      public class Test{
      
      	public void eat(){
      		xxx;
      		this.sleep()//其实和直接使用sleep()是一样的，所以一般情况省略，当方法的形参和属性同名的时候才必须显示用this调用
      	}
      	public void sleep(){
      		xxx;
      	}
      }
      ```

  - 类的构造器 ：调用该类中的其他构造器，**且必须声明在构造器的首行**

    - 当有多个构造器，其其中有大量耦合的时候，常常使用（也可以将耦合的部分抽出写成一个private方法，在不同的构造器这个方法）

      ```java
      public class Test{
      	private String name;
      	private int age;
      	...
      	
      	public Test(){
      		xxx;//很多行代码
      	}
      	public Test(String name){
      		this();//复用空参构造器的很多行代码
      		xxx;
      	}
      	public Test(String name,int age){
      		this(name);//复用(String name)构造器的很多行代码，当然肯定也会递归调用空参构造器
      		xxx;
      	}
      }
      ```

      

 ##### 继承性

- 如果两个类有属性，方法的高度重合，为了减少代码的冗余提出继承，可使其中一个类作为父类，另一个类作为子类去继承“extends”，则子类享有父类的所有属性和方法

  ```java
  class person {
      private String name;
      private int age;
      private int number;
      
      public String getName(){
          return name;
      }
      xxx;
  }
  class student{
      private String name;
      private int age;
      private int number;
  
      public String getName(){
          return name;
      }  
      xxx;
  }
  ```

  则可改写为：

  ```java
  class person {
      private String name;
      private int age;
      private int number;
  
      public String getName(){
          return name;
      }
  }
  class student extends person{
      xxx;//其余重合部分之间继承
  }
  
  ```



- 继承性的好处
  - 减少了代码的冗余，提高了代码的复用性
  - 有利于功能的拓展，当需要加入新功能时不需要将所有类属性都修改一遍而是改改父类即可
  - 描述了一种“is-a”关系，比如上文”student is a person“，为多态提供了前提

- 语法格式

  ```java
  class 子类 extends 父类
  ```

- 默认父类：Object

  - 当java中声明的类没有显示声明父类时，会默认继承java.lang.Object类

- 说明
  - java是提供多层继承：A继承B，B继承C
  - java是只支持单继承
    - 一个父类可以有多个子类
    - 一个子类至多有一个父类

- 示例![image-20230317110400708](image\image-20230317110400708.png)

  ```java
  public class Circle {
      private double radius;
  
      public Circle(){
          radius=1;
      }
  
      public  void setRadius(double radius){
          this.radius=radius;
      }
      public double getRadius(){
          return radius;
      }
      public double findArea(){
          return Math.PI*radius*radius;
      }
  }
  
  public class Cylinder extends Circle{
      private double length;
  
      public Cylinder(){
          length=1;
      }
  
      public void setLength(double length){
          this.length=length;
      }
      public double getLength(){
          return length;
      }
      public double findVolume(){
          System.out.println(findArea());
          return findArea()*length;
      }
  }
  
  ```

##### 方法的重写

-  针对于子类从父类中继承的方法不太适合于子类直接使用，对其进行重写来满足子类的需要

  - 以银行卡和透支卡为例

    ```java
    public class Card {
        private double ballance;//银行卡的余额
    
        public void withdraw(double atm){
            //用于判断余额是否足够支付
        }
    }
    public class CheekCard extends Card{
        private double protectBy;//透支额度
    
        public void withdraw(double atm){
            //因为透支卡没有余额属性，所以继承而来的withdraw方法便不再适用于子类
            //将其改写为判断透支额度是否足够支付
        }
    }
    
    ```

- 方法重写的要求：

  - 父类被重写的方法和子类重写的方法必须是方法名+形参列表都相同
  - 子类重写方法的权限修饰符不小于父类方法的权限修饰符
    - 子类不能重写父类中的private方法
  - 返回值问题
    - 父类方法的返回值类型是void或者基本数据类型时，子类重写的方法必须和其保持一致
    - 父类方法的返回值类型是引用类型时，子类重写方法的返回值和其相同或者是其子类

  - 子类重写方法抛出的异常可以和父类抛出异常相同，或者是父类抛出异常的子类

- 区分重载和重写
  - 重载：“两同一不同”，在同一个类中，通过不同的形参列表区分不同的方法
  - 重写：“在继承之中”，在子父类之间，子类对父类的方法进行修改

##### super关键字

- 当子类中需要使用父类中被重写的原方法，或者是当子类和父类有相同名字的属性，且子类想要调用父类的同名属性时，可使用super关键字

  >
  >
  >只有方法才能进行覆盖，属性是不能进行覆盖的，比如说父类和子类都有同名属性id，则构造子类对象时他有两个id属性，一个是继承的父类的id，一个是自己的id

- **区分“this.方法”和”super.方法“**

  - 常常在类中调用方法时会直接调用而不是通过对象调用，当调用的方法是this时会先在当前类中进行查找如果没有再去其父类，父类的父类中进行查找知道找到该方法，或者找到Object类还未找到则报错
  - super方法是直接去父类中找该方法，和this不同之处就是this先会在当前类中找

- **super调用构造器**

  - 子类在继承的时候是不会继承父类的构造器的，只能通过super来显示调用父类的构造器

    ```java
    super();//且置于首行
    ```

    >
    >
    >由于之前说可以用this()来调用该类的其他构造器也需要置于首行，所以this()和super()是不能同时出现的，至多存在一个，子类都会默认调用父类的空参构造器，即super()

##### 子类对象实例化

- 当创建子类对象的时候，子类对象会获取父类对象的所有属性和方法，在权限允许的条件下可以直接调用，会逐步向上获取直到Object类，并且是先加载父类在加载子类(先有父亲才有儿子)

#### 多态性

- 可以理解为一个事物的多种形态，即声明的时候是父类的类型，new的却是一个子类的对象

  - 父类的引用指向子类的对象（子类的对象赋值给父类的引用）

- 多态性的应用

  - 虚拟方法调用
    - 在编译时认为是调用的父类被重写的方法
    - 在执行时实际运行的是子类重写后的方法

- 前提：

  - 有继承关系
  - 子类对父类的方法进行重写 

- 注意

  - 多态性只能对方法满足，而不能对属性满足，如p.id调用的是父类id属性而不是子类Student的属性，虽然属性一般也都是private 

  ```java
  public class Person{
      public int id;
  	xxx;
     
       public void eat(){
          xxx;
      }
  }
  public class Student extends Person{
  	xxx;
       public void eat(){
          xxx;
      }
  }
  public static void main(String[] args) {
  	Person p=new Student(); 
      p.eat();//调用的是子类Student中重写的eat()方法
  }
  ```

- 多态性的优缺点

  - 优点：
    - 极大的减少了代码的冗余！以下式代码为例，在Test类中我们是不知道具体会传入什么类型参数，可能是Animal，Dog，Cat等等，如果没有多态性，则需要将所有可能的类型全封装成一个方法，也就是说会有大量的方法重载，但由于有了多态性，我们只需要写一个参数为父类的方法，在具体调用的时候传入子类对象即可解决
    -  便于扩展，即在不修改其他子类的前提下，即使增加了新的子类也只需在新的子类中添加方法即可
  - 缺点：
    - 创建对象的时候是会加载子类特有的方法和属性，但是由于声明的是父类的引用所以不能对子类特有的方法和属性进行调用

  ```java
  public class Animal {
      public void eat(){
          System.out.println("吃东西");
      }
      public void jump(){
          System.out.println("跳");
      }
  }
  
  class Dog extends Animal{
      public void eat(){
          System.out.println("吃狗粮");
      }
      public void jump(){
          System.out.println("狗跳");
      }
  }
  class Cat extends Animal{
      public void eat(){
          System.out.println("吃猫粮");
      }
      public void jump(){
          System.out.println("猫跳");
      }
  }
  
  class Test{
      public static void main(String[] args) {
          Test test=new Test();
          test.adopt(new Dog());//输出Dog类的方法
          test.adopt(new Cat());//输出Cat类的方法
      }
      public void adopt(Animal animal){
          animal.eat();
          animal.jump();
      }
  }
  ```

​	

##### 向下转型

- 之前上文提到的多态性的弊端，是由于声明的是父类对象的引用，所以无法调用子类特有的方法和属性，可以通过向下转型的方式将父类对象转化为子类的对象来解决

  ```java
  Person p1=new Student();
  //此时的p1是无法调用Student中特有的方法的
  Student s1=(Student) p1;
  //现在打s1就可调用Student中特有的方法和属性，但这里的s1和p1都指向的是堆中的同一个对象而不是两个不同的对象
  System.out.println(p1==s1);//输出是true，即两者的地址是一样的 
  ```

##### instanceof 关键词

- 当以Person作为父类，Man和Woman作为子类时，若Woman的对象想转化为Man则会报出异常，为了避免这样的问题，在每一次类型转化前都先使用instanceof关键字

  ```java
  Person p=new Woman();
  if(p instanceof Man){//则不会进入
  	Man m=(Man) p;
  }
  if(p instanceof Woman){//则会进入,将Woman换成其父类也能判断为true
  	Woman m=(Woman) p;
  }
  ```

  

### Object类

- 每一个类都直接或者间接继承Object类，所以其声明的结构就具有通用性
  - Object类中没有声明属性
  - Object类提供了一个空参的构造器
  - Object类中声明的方法

#### clone()方法

- 创建并返回当前对象的复制品，是在堆空间中新造了一个对象，而不是原对象的副本，也就是说两者用"=="判断的结果是false，即两者地址不一样 

#### finalize()方法

- 在被垃圾回收之前自己会调用该方法，所以可以重写该方法，在回收之前做一些检查工作保存数据等，但是在JDK9之后就不建议再使用该方法了，因为可能会导致循环引用导致该对象无法被回收了

#### equals()方法

- 和“==”是一样的，判断两个对象是否地址相同

  - 所以一般在自定义类中要调用equals()方法都需要重写，不然直接用“==”就好啦

- 在自定义类中如果没有重写equals()方法，则调用的是基类Object类中的equals()方法

  ```java
  /**
  * String类中重写了equals()方法
  * 不在是判断两者的地址是否相同，而是字面量是否相同
  */
  String s1="123";
  String s2="123";
  System.out.println(s1.equals(s2));//结果是true
  ```

- equals()方法的重写来判断两个对象是否相同

  - 手动重写

  ```java
  public class User {
      private int age;
      private String name;
      public User(int age,String name){
          this.age=age;
          this.name=name;
      }
  
      @Override
      public boolean equals(Object obj) {
          if(this==obj){
              return true;
          }else{
              if(obj instanceof User){
                  User user =(User) obj;
                  return this.age==user.age && this.name.equals(user.name);
              }
          }
          return false;
      }
  }
  ```

  - IDEA自动实现

- ”==“和equals()方法的区别

  - ”==“的使用范围
    - 基本数据类型：判断数值是否相等
    - 引用数据类型：判断地址是否相同

  - equals()方法
    - 只能在引用数据类型
    - 对于自定义类中要判断是否需要重写equals()方法

#### toString()方法

- 在自定义类中如果没有重写toString()方法会默认返回当前对象的地址值，但在String，File，Date等类中重写过toString()方法返回的是对象的实体内容

- 在实际开发中对于自定义类我们想关注的一般也是对象的实体内容而不是其地址值，所以需要将其重写

  - 手动实现

    ```java
    public class User {
        private int age;
        private String name;
    	
    	@Override
    	public String toString() {
        	return this.age+this.name;
        }
    }
    ```

  - IDEA自动实现

## static关键字

#### 类属性和类方法

- 类属性：我们在每次new的时候，会在堆中生成一个对象，这些对象都是相互独立不能相互访问的，但有时有些属性是需要被类中所有实例所共享的，则将其用static修饰，成为类变量

- 类方法：在类中声明的方法，在类的外部需要通过该类实例化的对象去调用，但有些方法的调用者和该类无关，则将该方法用static修饰，成为静态方法。例如System.out，直接通过System类就调用了out方法而不需要去实例化System对象

#### static修饰属性

- 静态和实例的区别

  - 个数

    - 静态变量：整个堆空间中只有一份，被整个类共享
    - 实例变量：在每一个对象中各自拥有单独的一份实例变量

  - 存放位置

    - 静态变量：在JDK6之前存放在方法区，JDK7之后存放在堆中

    - 实例变量：存放在堆中

  - 加载时机

    - 静态变量：在类加载之后就能加载，由于类只会加载一次，所以只会有一份静态变量
    - 实例变量：在对象创建之后才会加载

  - 调用
    - 静态变量：可以通过类或者对象来调用
    - 实例变量：只能通过对象调用
  - 消亡时机
    - 静态变量：随着类的消亡而消亡
    - 实例变量：随着对象的消亡而消亡

#### static修饰方法

- 静态方法可调用的结构

  - 静态方法可调用其他静态方法，静态属性，但不能调用非静态的方法和非静态的属性

    >
    >
    >因为非静态的方法在创建对象的时候才会存在，而此时刚加载完类，堆中只有静态的方法和变量

- 静态方法可以被对象调用，也可以被类调用，但常常习惯都是直接通过类来调用

- 静态方法中不能使用“this”关键字，也不能使用“super“关键字

  >
  >
  >因为this关键字实际上指的是调用该方法的对象，而在静态方法中可能都没对象被创建，所以自然不能使用this关键字，而super也是基于当前对象来说

- 开发中什么时候需要设置为static

  - 属性

    - 该结构需要被类共享
    - 常常将一些常量声明为静态，比如Math.PI

  - 方法

    - 对于操作的变量都是静态变量则将该方法设置为静态方法

    - 对于常用的工具类常常声明为静态方法，比如Arrays类，Math类等等

### 单例模式

- 在整个软件系统中，保证某个类只能存在一个对象实例，并且该类只提供一个获取该对象实例的方法

- 实现思路
  - 由于每new一次就能新生成一个对象，所以就必须限制new的使用，所以将构造器的权限设置为private，则就可保证不能在外部通过new来新建对象，在类的内部创建好对象
  - 但由于在类的外部不能产生对象，所以得到该对象的方法就必须是静态方法来返回类中生成的对象，这样就可以通过类来调用，否则只能通过对象调用，但又无法创建对象
  - 由于静态方法不能调用实例变量，所以该类中该对象的属性必须全是静态的

- 实现方式

  - 饿汉式

    ```java
    public class Ehanshi {
        private Ehanshi(){
    
        }
        //声明并创建
        private static Ehanshi ehanshi=new Ehanshi();
    
        public static Ehanshi getInstance(){
            return ehanshi;
        }
    }
    class EhanshiTest{
        public static void main(String[] args) {
        	//即使多次实例化，返回的都是同一个对象，所以输出是true
            Ehanshi ehanshi1=Ehanshi.getInstance();
            Ehanshi ehanshi2=Ehanshi.getInstance();
            System.out.println(ehanshi1 == ehanshi2);
        }
    }
    ```

  - 懒汉式

    ```java
    public class Lanhanshi {
        private Lanhanshi(){
            
        }
        //只是先声明但先不创建实例
        private static Lanhanshi lanhanshi=null;
        
        public static Lanhanshi getInstance(){
            if(lanhanshi==null){
                lanhanshi=new Lanhanshi();
            }
            return lanhanshi;
        }
    }
    ```

  - 两种模式的区别

    - 饿汉式：“立即加载”

      - 优点：
        - 写法稍微简单一些
        - 在内存中较早加载，使用时更快更方便，线程是安全的
      - 缺点：
        - 由于一来就创建好，但使用的时间又不是很多，并且由于是static的所以生命周期很长就导致了占用内存的时间长

    - 懒汉式：“延迟加载”

      - 优点：在需要的时候才会被创建，所以会节省内存空间

      - 缺点：线程不安全

        >
        >
        >当两个线程同时判断是null的时候，进行了两次实例的创建，就违背了单实例的需求

- 使用场景
  - 任务管理器
  - 回收站
  - 日志文件
  - 数据库连接池等

#### main函数的解析

```java
public static void main (String []args)
```

- public：表面该方法权限很高，在工程的每个地方都能访问
- static：因为main是程序的入口，随着类的加载而执行，如果不是static则需要用对象去调用，但现在连程序入口都没有更别说创建对象了
- void：没啥需要返回的东西了，main执行完也就程序结束了

- String []args：与控制台交互，通过命令行或者编译器中传参

### 代码块

- 又可称为初始化块，用来初始化类或对象的成员变量，至多只能使用static修饰

- 静态代码块和非静态代码块：可声明变量，调用属性，方法，编写输出语句等

  - 是否用static修饰
  - 静态代码块：
    - 随着类的加载而调用执行
    - 由于类只会加载一次，所以只会执行一次
    - 用于初始化类的信息
  - 非静态代码块：
    - 随着每次对象的创建而执行，也就是说创建多个对象的时候会执行多次
    - 用于初始化对象的信息

  ```java
  public class Person {
      private String name;
      private int age;
      private static String country;  
      
      public Person(){
          
      }
      
      //静态代码块，随着类的加载而执行,初始化静态属性
      static {
          country="China";
      }
      
      //非静态代码块，随着对象的创建而执行，初始化非静态属性
      {
          age=1;
      }
  }
  ```

### final关键字

- 可用于修饰类，方法，变量

  - 修饰类：表示该类不能被继承

  - 修饰方法：表示该类不能被重写

  - 修饰变量：既可以修饰成员变量，也能修饰局部变量，即该变量不能再被更改，也就相当于const

    >
    >
    >const现在作为了java的保留字，也就是说在未来的版本可能会拓展，现在const还是常用于C,C++中

- final修饰属性的初始化位置：必须得确保该变量一定有值
  - 显示赋值
  - 构造器
  - 代码块
- final和static的搭配
  - 修饰成员变量：称为全局常量，在全局都可调用但都不可更改的常量信息

### 抽象类和抽象方法

#### abstract关键字

- 抽象类：随着继承中一个个新子类的定义，每一个子类越来越具体，而子类变得越来越一般，这时将父类设计为抽象类，对于抽象类是不能创建具体的对象
  - 抽象类不能实例化
  - 抽象类中具有构造器
    - 因为抽象类会被继承，而子类一定会直接或间接的调用父类的构造器
  - 抽象类中可能不具备抽象方法

- 抽象方法：在父类中声明的某些方法，只具备方法名不具备方法体，比如求图形的面积等，对于每个不同的图形都应该有其各自的面积公式，所以求面积的方法的方法体应该在各自子类中进行重写，而父类中不应该有具体求法。抽象方法只能出现在抽象类中！（其实也就是接口啦）

  - 只有方法的声明，不具有具体实现
  - 抽象方法的功能是确定的，但是具体实现还没给出
  - 子类如果不是抽象类则需要将所有的抽象方法重写

  ```java
  public abstract class GeometricObject {
      //求几何图像的面积，具体实现交给子类实现
      public abstract double findArea();
      //求几何图像的周长，具体实现交给子类实现
      public abstract double findCircumference();
  }
  class Circle extends GeometricObject{
      private int r;
      //对抽象方法的具体实现
      public double findArea(){
          return Math.PI*r*r;
      }
      //对抽象方法的具体实现
      public double findCircumference(){
          return Math.PI*2*r;
      }
  }
  abstract class Triangle extends GeometricObject{
      /**
       * 不对抽象类的抽象方法进行具体实现，所以该类又成为一个抽象类
       * 当然也能重新定义自己的抽象方法
       */
      public abstract double findAngle();
  }
  ```

  >
  >
  >当子类继承的是一个抽象类的时候，也就是说会继承其抽象方法，所以该子类要么就将抽象方法具体实现，要么就也成为一个抽象类，因为抽象方法只能出现在抽象类中

- abstract不能修饰的结构
  - 私有方法：私有方法不允许被重写，但抽象方法一定在最终会被实现也就是重写，所有矛盾
  - 静态方法：静态方法是可以通过类名直接调用的，但是抽象方法连方法体都没有是不允许被调用的
  - final方法：final方法是一定不能被重写的，抽象方法一定要重写的
  - final类：final类不能有子类，抽象类必须有子类来进行实现

### 模板方法的设计模式

- 简单来说就是将已经确定的方法在抽象类中固定下来，也就是将方法体都给出，而那些暂时不明确的方法写为抽象方法，留给子类具体实现去

```java
public abstract class Bank {
    private int num;
    //取号是固定下来的，无非就是来一个号码嘛
    public void takeNum(){

    }
    //不同的窗口有不同的业务，所以办理业务的具体实现应该放到不同的窗口子类中实现
    public abstract void transact();
}

```

### 接口

- 定义接口的关键字：interface

- 接口的理解：接口是和类并列的，本质上就是一种标准，类描述的是“is-a”关系，而接口描述的是“has-a”关系，具备了某些性质，常常是一些功能，飞，跑步等，而类常常是一些名词，学生，人等

- 接口内部可声明的结构
  - 属性：必须是public static final修饰
  - 方法：
    - JDK8之前：只能声明抽象方法
    - JDK8：可以声明静态方法，默认方法
    - JDK9之后：可以声明私有方法

- 不能声明的结构

  - 构造器
    - 也就是说接口是不允许造对象的
  - 代码块

  ```java
  public interface Flyable {
      public static final int MIN_SPEED=0;
      //权限修饰符等是可以省略的
      int MAX_SPEED=1000;
      
      public abstract void fly();
      //同样因为权限都是一样的，所以就可以将其省略了
      void stop();
  }
  ```

- 接口和类的关系

  - 是一直实现关系：也就是在类中重写接口中的抽象方法，类是可以同时实现多个接口的

  - 格式：

    ```java
    class A extends B implements C,D{
        //A相较于B来说是其子类
        //A相较于CD来说是其实现类
    }
    ```

  - 注意

    - 类是可以同时实现多个接口
    - 类对于接口的多实现，一定程度弥补了类只能单继承的局限性
    - 接口其实也就相当于是一个抽象类，而实现类也就相当于其子类，所以实现类必须实现接口中的所有方法，否则实现类就只能是一个抽象类

- 接口和接口的关系

  - 接口与接口之间是可多继承的

    ```JAVA
    interface A extends B,C{
    
    }
    ```

- 接口的多态性

  - 接口名+变量名 = new 实现类对象

  - 对比类的多态性：父类名+变量名 = new 子类对象

    ```java
    public class UsbTest {
        public static void main(String[] args) {
            Printer printer=new Printer();
            //1.创建接口实现类的对象
            Computer computer=new Computer();
            computer.transation(printer);
            
            //2.创建接口实现类的匿名对象
            computer.transation(new Printer);
            
            //3.创建接口匿名实现类的对象(因为之前new后面的类是什么就是什么类的对象)
            //由于接口是抽象的不允许创建对象，所以这临时将抽象方法重写
            Usb usb1=new Usb(){
                  public void start(){
           			 System.out.println("相机开始工作");
       			 }
      			  @Override
      			  public void stop(){
        		    System.out.println("相机停止工作");
      			 }
           }
           computer.transation(usb1); 
            //4.创建接口匿名实现类的匿名对象
           computer.transation(new Usb(){
                @Override
                public void start(){
                    System.out.println("U盘开始工作");
                }
                @Override
                public void stop(){
                    System.out.println("U盘停止工作");
                }
            });
        }
    }
    
    
    interface Usb{
        public static final int LENGTH=10;
        public static final int WINDTH=5;
    
        public abstract void start();
        public abstract void stop();
    }
    
    class Printer implements Usb{
        @Override
        public void start(){
            System.out.println("打印机开始工作");
        }
        @Override
        public void stop(){
            System.out.println("打印机停止工作");
        }
    }
    
    class Computer {
        public void transation(Usb usb){
            usb.start();
            usb.stop();
        }
    }
    ```

- 抽象类和接口的区分
  - 相同点
    - 都可以声明抽象方法
    - 都不能实例化对象
  - 不同点
    - 抽象类是有构造器的，只是一个能生不生，一个直接没能力生
    - 类和类直接是继承关系且是单继承，接口和类之间是实现关系且可以多实现，接口和接口之间的继承关系是多继承

### 内部类

- 将一个类A定义在了类B的内部，则称A为内部类
- 为什么要声明内部类
  - 当一个类的内部需要一个完整的结构B来进行描述，但结构B只是一个变量又不能满足该需求，并且结构B只对A提供服务，不在其他地方单独使用，这时候就会将B定义为内部类
  
  - 常用于Node的声明，以及Thread类中的State类的声明（表示线程的生命周期）

- 内部类的使用上和外部类基本相同，只是外部类只能由public和缺省修饰，但是内部类四种权限修饰符均可

- 内部类的声明

  ```java
  public class Animal {
      //声明静态内部类
      static class Dog{
  
      }
      //声明非静态内部类
      class Bird{
  
      }
  
      //声明局部内部类，可以放在方法，构造器，代码块中
      public void methods(){
          class cat{
              
          }
      }
  }
  ```

- 内部类的实例化

  ```java
  public class AnimalTest {
      //实例化静态内部类对象
      Animal.Dog dog=new Animal.Dog();
  
      //实例化非静态内部类对象,非静态只能通过对象去调用
      Animal animal=new Animal();
      //注意不是new animal.Bird(),是得通过animal对象去调用构造器
      Animal.Bird bird=animal.new Bird();
  }
  ```

### 枚举类

- 类的对象是有限的，只有固定的几个，不允许用户随意创建
  - 星期
  - 性别
  - 月份
  - 支付方式等  
- 枚举类的实现

  - JDK5.0之前，手撸枚举类

    ```java
    public class Season {
    
        //声明枚举类的实例变量
        private final String name;
        private final String describe;
    
        /*
         *   由于只能按照枚举类中预想的样子声明变量
         *   所以不能把构造器暴露出去，于是定义为私有的构造器
         */
        private Season(String name,String describe){
            this.name=name;
            this.describe=describe;
        }
        //提供一个get方法
        public String getName() {
            return name;
        }
    
        public String getDescribe() {
            return describe;
        }
    
        /**
         * 由于不能通过对象调用，所以将其设置为静态
         * 由于不能在外部进行修改，所以将其设置为final
         */
        public static final Season SPRING=new Season("春天","春暖花开");
        public static final Season SUMMER=new Season("夏天","夏日炎炎");
        public static final Season AUTUMN=new Season("秋天","硕果累累");
        public static final Season WINTER=new Season("冬天","白雪皑皑");
    }
    ```

  - JDK5.0之后，通过Enmu关键字定义

    ```JAVA
    public enum Season1 {
        /**
         * 由于创建对象的时候前后有很多固定的东西
         * 所以在enmu关键字中将相同部分省略
         * 不同对象之间用“,”隔开
         */
    //    public static final Season SPRING=new Season("春天","春暖花开");
    //    public static final Season SUMMER=new Season("夏天","夏日炎炎");
    //    public static final Season AUTUMN=new Season("秋天","硕果累累");
    //    public static final Season WINTER=new Season("冬天","白雪皑皑");
        SPRING("春天","春暖花开"),
        SUMMER("夏天","夏日炎炎"),
        AUTUMN("秋天","硕果累累"),
        WINTER("冬天","白雪皑皑");
        //声明枚举类的实例变量
        private final String name;
        private final String describe;
    
        /*
         *   由于只能按照枚举类中预想的样子声明变量
         *   所以不能把构造器暴露出去，于是定义为私有的构造器
         */
        private Season1(String name,String describe){
            this.name=name;
            this.describe=describe;
        }
        //提供一个get方法
        public String getName() {
            return name;
        }
    
        public String getDescribe() {
            return describe;
        }
    
    
    }
    ```

- 对接口的实现

  - 枚举类实现接口，在枚举类中重写接口的抽象方法，当通过不同的枚举对象调用的都会是同一个方法

    ```java
    public enum Season1 interface A{
        SPRING("春天","春暖花开"),
        SUMMER("夏天","夏日炎炎"),
        AUTUMN("秋天","硕果累累"),
        WINTER("冬天","白雪皑皑");
        //声明枚举类的实例变量
        private final String name;
        private final String describe;
    
        /*
         *   由于只能按照枚举类中预想的样子声明变量
         *   所以不能把构造器暴露出去，于是定义为私有的构造器
         */
        private Season1(String name,String describe){
            this.name=name;
            this.describe=describe;
        }
        //提供一个get方法
        public String getName() {
            return name;
        }
    
        public String getDescribe() {
            return describe;
        }
        
        /**
         * 实现接口中的抽象方法
         * 当通过不同的枚举对象调用的都会是同一个方法
         */
        public void show(){
        	XXX;
        }
    
    
    }
    ```

    

  - 让每一个枚举类的对象重写抽象方法，当通过不同的对象调用此方法时，执行的是不同的方法

    ```java
    public enum Season1 interface A{
    	/**
         * 实现接口中的抽象方法
         * 当通过不同的枚举对象调用的都会是不同的方法
         */
        SPRING("春天","春暖花开"){
        	public void show(){
        		XXX;
        	}
        },
        SUMMER("夏天","夏日炎炎"){
        	public void show(){
        		XXX;
        	}
        },
        AUTUMN("秋天","硕果累累"){
        	public void show(){
        		XXX;
        	}
        },
        WINTER("冬天","白雪皑皑"){
        	public void show(){
        		XXX;
       	 	}
        };
        //声明枚举类的实例变量
        private final String name;
        private final String describe;
    
        /*
         *   由于只能按照枚举类中预想的样子声明变量
         *   所以不能把构造器暴露出去，于是定义为私有的构造器
         */
        private Season1(String name,String describe){
            this.name=name;
            this.describe=describe;
        }
        //提供一个get方法
        public String getName() {
            return name;
        }
    
        public String getDescribe() {
            return describe;
        }
    
    }
    ```

    

- 也可以通过枚举类来实现单例模式
  - 在枚举类中只定义了一个对象，然后有一个get对象方法即可

### 注解

 

- 可以像修饰符一样，对包，类，构造器，方法，属性，参数等声明进行修饰，注释可以在类编译和运行时加载，体现不同的功能
- 区分注解和注释
  - 注释
    - 无论是单行注释还是多行注释都是写给程序员看的，在编译阶段都会被删除
  - 注解
    - 注解是可以通过编译器或者其他程序读取的，也就是在编译之后仍然会存在的
- 三种java内置的基本注释
  - @Override：只能修饰方法，意为该方法一定是重写的方法，如果不是方法的重写就会报错
  - @Deprecated：表面被修饰部分不推荐使用，在未来的JDK版本可能会被删掉，但是仍然可以使用，只是不推荐（为了向前兼容）
  - @SuppressWarnings：抑制后续可能出线的异常警告，不再进行提示

- 自定义注解：在使用框架的时候会大量使用注解，在自己写框架的时候才会使用 
  - 框架=注解+反射+设计模式

- 元注解：对注解进行解释的注解

### 单元测试

- 测试的分类
  - 黑盒测试：不需要写代码，只需要给输入看输出对不对即可
  - 白盒测试：需要写代码，并且会关注程序的具体执行过程

- main测试VS单元测试

  - 之前的测试都是在main中进行的，对于有很多方法需要测试的时候需要手动注释不需要的部分会很麻烦，于是才有了单元测试，并且main中对于非静态方法还需要通过创建对象调用

  - 单元测试一般都直接写在了类的内部，并且对于不同的单元测试通过多个@Test分隔开彼此互不干扰，由于在类的内部对于非静态的方法不需要创建对象可以直接调用

    ```java
    public class JUnit {
    
        @Test
        public void test(){
            haha();
        }
    
        public void haha(){
            System.out.println("haha");
        }
    }
    ```

- 前提

  - 需要两个jar包，可以直接IDEA右键联网构建，无网的时候则手动导入jar包

  - 单元测试类必须是public，非抽象的，有唯一的空参构造器，返回值是void，且是空参的

    > 
    >
    > 对于非抽象是注解会自动生成对象来调用，所以在单元测试方法中只需要写调用部分

- 注意
  - 在默认情况下Scanner会在单元测试中失效，可以在IDEA的help-VM Options中添加"-Deditable.java.test.console=true"进行设置

- 将单元测试设置为自定义模板

  - File-Setting-Editor-Live Templates中自定义一个文件夹并加入模板，并将其运用于java

    ```java
    @Test
    public void test$begin$(){//begin为初始光标位置
        $end$//end为回车后的位置
    }
    ```

### 包装类

- 包装类的引入：由于数据类型分为基本数据类型和引用数据类型，而基本数据类型的执行效率更高，但有的时候传参等必须传入的是引用数据类型，此时会将基本数据类型进行封装成包装类，也就是说使基本数据类型具备了引用数据类型的特征

- 包装类的分类

  - byte：Byte

  - short：Short

  - int：Integer

  - long：Long

  - float：Float

  - double：Double

  - boolean：Boolean

  - char：Charactor

    ```java
    public static void main(String[] args) {
        int haha=10;//封装前，只是在栈中存在
        Integer hehe=new Integer(10);//封装后，会在堆中产生对象
    }
    ```

#### 基本数据类型和包装类转换

- 为什么要进行相互转换：

  - 对于数据类型：有时对于基本数据类型需要让其具备引用数据类型
  - 对于包装类：包装类的对象是不能进行加减乘除操作，只有基本数据类型才能进行加减乘除运算

- 如何转换

  - 基本数据类型$\rightarrow$包装类

    - 使用包装类构造器（不推荐使用，在JDK8之后被标记）

    ```java
    public static void main(String[] args) {
        int haha=10;//封装前，只是在栈中存在
        Integer hehe=new Integer(10);//封装后，会在堆中产生对象
    }
    ```

    - 使用包装类的valueof()方法

    ```java
    public static void main(String[] args) {
        int haha=10;//封装前
        Integer hehe=Integer.valueOf(10);
    }
    ```
  
  - 包装类$\rightarrow$基本数据类型
  
    - 通过包装类中内置的方法
  
    ```java
    public static void main(String[] args) {
        Integer hehe=Integer.valueOf(10);
        int i=hehe.intValue();
        i++;
        
        Double haha=Double.valueOf(3.14);
        double d=haha.doubleValue();
        d++;
    }
    ```

- JDK5之后的新特性

  - 自动装箱与拆箱：直接通过赋值号，自动进行类型转化

    - 装箱：基本数据类型$\rightarrow$包装类
    - 拆箱：包装类$\rightarrow$基本数据类型

    ```java
    public static void main(String[] args) {
        int num=5;
        Integer integer=num;
        
        Double d=Double.valueOf(3.14);
        double d1=d;
    }
    ```

### String类与基本数据类型和包装类的转化

#### String和包装类的转化

- tips：由于自动装箱，拆箱的存在，可以将包装类和基本数据类型归为一类讨论

- 基本数据类型，包装类$\rightarrow $String

  - 调用String重载的静态方法valueOf()

  - 使用基本数据类型的连接运算

    ```java
    public static void main(String[] args) {
        int num=123;
        //1.通过String重载的valueOf()方法
        String str1=String.valueOf(num);
        
        //2.通过基本数据类型的连接运算
        String str2=num+"";
    }
    ```

- String$\rightarrow $基本数据类型，包装类

  - 通过包装类中的内置方法

  ```java
  public static void main(String[] args) {
      String str="1234";
      int num=Integer.parseInt(str);
  
      //当字符串中包含有多种基本数据类型时这样的转化会有异常NumberFormatException
      String str1="123a";
      int num1=Integer.parseInt(str1);
  }
  ```

### 面对对象章节的面试题

#### static关键字

- 静态变量和实例变量的区别
  - 个数

    - 静态变量：整个堆空间中只有一份，被整个类共享
    - 实例变量：在每一个对象中各自拥有单独的一份实例变量

  - 存放位置

    - 静态变量：在JDK6之前存放在方法区，JDK7之后存放在堆中

    - 实例变量：存放在堆中

  - 加载时机

    - 静态变量：在类加载之后就能加载，由于类只会加载一次，所以只会有一份静态变量
    - 实例变量：在对象创建之后才会加载

  - 调用
    - 静态变量：可以通过类或者对象来调用
    - 实例变量：只能通过对象调用
  - 消亡时机
    - 静态变量：随着类的消亡而消亡
    - 实例变量：随着对象的消亡而消亡
- 静态属性和静态方法是否可以被继承，是否可以被重写？其原因
  - 静态方法不能被重写
    - 对于重写只能是非static，如果是static方法，则子类父类只是重名方法，因为调用是通过类来调用，和对象都没关系
  - 静态方法可以被继承
- static方法能否调用非static方法？
  - 当然不能，因为static方法是通过类的加载而加载的，此时肯定是没有对象的，而非static方法是需要通过对象调用的，所以自然是不能的。同理，static内部还只能操作静态属性不能调用实例属性，这同样是因为没有创建对象
- 被static修饰的成员能否再被private修饰？
  - 可以，除了代码块

#### 设计模式

- 大概有哪些设计模式
  - 单例模式
  - 模板方法
  - 主要是MVC等框架

#### main方法

- public能否改为private
  - 当然可以，但这样的话main方法就变成了一个普通的自定义方法，不再是程序的入口
- main方法是否能调用非静态方法
  - 其实也就是静态方法能不能调用非静态方法，所以肯定不能的

#### 代码块

- 类的属性值的赋值顺序
  - 
- 静态代码块，普通代码块，构造方法，从类的加载开始的执行顺序
  - 静态代码块，普通代码块，构造器

#### final关键字

- 对于final的理解
- 使用final修饰一个变量时，是引用不可改变，还是引用指向的对象不可改变
  - 引用是不能改变
  - 但如果final修饰的对象实体中的属性如果没有final再修饰的话，是可以改变的
- final能否修饰构造器？
  - 当然不能，构造器的声明本来就是权限+类名，连返回值都没有，并且也不可能子类去重写构造器，所以这样的修饰没有任何意义
- final或者static final修饰成员变量，其能否++？
  - 自然是不能的，该变量直接不能被修改

#### 接口和抽象类

- 什么是抽象类，如何识别抽象类？
  - 抽象类：首先其中肯定包含了抽象方法，对于抽象类是不允许创建对象实例的
  - 识别：看该类是否被abstract修饰即可
- 为什么不能用abstract修饰属性，私有方法，构造器，静态方法，final方法？
  - 因为两者之间就有矛盾，abstract所修饰的东西一定会在子类中实现，或者说重写，而构造器私有方法等都一定不可能在子类中被重写
- 接口和抽象类的区别
  - 定义不同
    - 抽象类：可以包含抽象方法
    - 接口：内部的方法肯定是抽象方法（JDK8之前）
  - 组成不同
    - 抽象类：和普通类是差不多，只是没有代码块
    - 接口：全局常量和抽象方法（在JDK8之前，之后会有默认方法和私有方法）
  - 使用不同
    - 抽象类：子类继承
    - 接口：子类实现
- 接口是否能继承接口，抽象类是否可以实现接口，抽象类是否可以继承实现类
  - 都能
  - 对于抽象类实现接口，也就是没有将接口里面的所有抽象方法都实现，那么就还剩下一些抽象方法，那么自然该实现类就变成了抽象类
- 接口可以有自己的属性吗？
  - 可以，但一定是public static final的

#### 内部类

- 内部类有哪些？
  - 成员内部类
  - 局部内部类等等
- 内部类的特点
- 匿名类
  - 常常是只会在该处用到一个类的实例，或者该类很小只有几行，或者只给一个类名不太容易理解等

#### 枚举类

- 枚举类可以继承吗？
  - 如果是是自己自定义的那没问题
  - 如果是用Enmu关键字定义的该类的父类就是Enmu类就不能再继承其他类了

#### 包装类

- 基本类型和包装类的区别



## 异常

- 定义：在程序执行过程中，出现的非正常情况导致JVM非正常的停止
  - 理解：程序在运行的过程当中会遇到一些问题，这些问题依靠代码是不能解决的
  - 比如：
    - scanner获取用户输入时本意是要获取int值，但是用户非要输入一个String
    - 读取的文件被删除了
  
- java的异常抛出机制 
  - java将不同的异常封装成不同的类，当发生某种异常的时候就会创建该异常类型的对象，并且抛出(throw)，程序员可以捕获该异常(catch)，如果捕获则程序可继续运行，如果没有被捕获则程序停止
  
- 异常的体系结构
  - Error：java虚拟机无法解决的问题
    - StackOverFlowError：栈溢出
    - OutOfMemoryError：堆溢出
  
  - Exception：可以通过针对性代码进行处理，使程序继续运行，否则一旦发生异常不进行处理也会导致程序崩溃
    - 运行时异常
      - 空指针访问：只要是对象没有指向一个实体
  
      - 数组越界：ArrayIndexOutOfBoundException
  
      - 强转异常：ClassCastException
  
      - 数字格式化异常：NumberFormatException
  
      - 输入类型不匹配：InputMismatchException
  
      - 算数异常：ArithmeticEception
  
        ```java
        public class ExceptionTest {
        
            //NullPointerException
            @Test
            public void test1(){
                String str=null;
                str.length();
            }
        
            //ArrayIndexOutOfBoundsException
            @Test
            public void test2(){
                int []array=new int[10];
                array[10]=1;
            }
        
            //ClassCastException
            @Test
            public void test3(){
                Object s = new String();
                Date date=(Date) s;
            }
        
            //NumberFormatException
            @Test
            public void test4(){
                String s = "abc";
                int i = Integer.parseInt(s);
            }
        
            //InputMismatchException
            @Test
            public void test5(){
                Scanner scan = new Scanner(System.in);
                /**
                 *   本意是让用户输入整形数据
                 *   但是如果用户输入字符串等数据时就会抛出异常
                 */
                int num=scan.nextInt();
            }
        
            //ArithmeticException
            @Test
            public void test6(){
                int x = 0;
                //出现被除数为零等算数错误
                int y = 10/x;
            }
        
        }
        ```
  
    - 编译时异常
  
      - 类未找到异常：ClassNoFoundException
      - 文件未找到异常：FileNoFoundException
      - IO异常：IOException

 

### try—catch

 #### 捕获异常(try-catch-finally)

- 语法结构

  ```java
  try{
  	/**
  	*	加入可能出现异常的代码
  	*	其中当有异常出现时，该行之后的代码不再执行
  	*	转向catch语句
  	*/
  	xxx;
  }
  catch(异常类型1 e){
  	xxx //当发生异常类型1时的处理措施
  }
  catch(异常类型2 e){
  	xxx //当发生异常类型2时的处理措施
  }
  finally{
  	xxx//无论是否发生异常都会执行的部分，常常为关闭资源
  }
  ```

- 基本过程

  - 抛：
    - 在try中一旦发生异常，就会生成对应异常类的对象，并将其抛出，一旦抛出后，后续代码则不会继续执行
  - 抓：
    - 对于抛出的异常对象进行捕获，一旦对异常进行了处理，代码就可继续执行（try-catch之后的代码）

  >
  >
  >对于所有运行时异常的父类RunTimeException应当放到最后不然会将所以的运行时异常都捕获，而不知道是什么具体的异常也不好处理，常常放最后来收尾，怕有没想到的异常出现

- catch处理异常的方式
  - 自己编写输出语句进行提示
  - printStackTrace()，打印异常的详细信息（推荐）
  - getMessage()，获取发生异常的原因

#### finally的使用

- 一定要被执行的代码常声明在finally中，无论try-catch中是否有仍未处理的异常，甚至是有return语句都一定会执行

- 可以直接try-finally，而没有catch是可以

- 放在finally中的常常是对资源的关闭，不然垃圾回收器是不会自动回收，这会导致内存泄漏

  >
  >
  >所以也就会出现说有垃圾回收器，所以java就不会出现内存泄漏这样的问题，肯定就是错的了

### throws

- 在方法的声明处

```java
public void methods throws 异常类型1，异常类型2...{
	xxx;
}
```

>
>
>将该异常抛出，不做具体处理，谁调用该方法谁就去处理，当然调用该方法的方法仍然可以继续抛出，但如果是main方法就不能再抛出啦，其实在本质上来说throws是没有真正处理异常的，真正处理异常的手段还是try-catch

- 对于方法的重写

  - 子类重写的方法抛出的异常可以和父类被重写的抛出的异常类型相同，也可以是父类异常的子类(针对于编译型异常，运行时异常就无所谓了)

    >
    >
    >比如子类是空指针异常，而父类时运行时异常，也就是说必须父类要能包住子类就行，其实也就是多态

- 对于两种异常方式的选择

  - try-catch

    - 设计资源的关闭
    - 对于父类没有抛出异常，而子类有编译型异常

  - throws

    - 在方法的递进调用时，在本方法中不能很好的处理异常时

      >
      >
      >在a中调用b，在b中又调用了c
      >
      >本来当a中出现编译型异常时，bc就不需要执行了，在main中catch异常就好，如果是各自使用try-catch则a剩余的部分是不会执行了，但bc仍然可能是会执行的

#### 手动抛出异常

- 之前的异常都是自动产生并抛出的，但有时候我们可能面临该异常对于jdk是不存在的，但又不满足我们的需要

  - 比如说：对于定义的变量表示人数，在语言层面整形变量是可以为负值的，但负的人数显然不满足我们的实际需要，于是这个时候就可以手动抛出一个异常

    ```JAVA
    private int num;
    public void getNum(int num){
        if(num>=0){
            this.num = num;
        }else{
            throw new RuntimeException("输入了一个错误的人数");
        }
    }
    ```

    >
    >
    >当然如果抛出的是运行时异常就可以不进行处理，但如果是抛出了一个编译型异常就需要通过try-catch或者是throws进行处理了

#### 自定义异常类

- 如何定义

  - 本质还是一个类，但又不能是普通的类，是继承于RuntimeException(运行时异常)或者Exception(编译型异常)的类

  - 通常会提供几个重载的构造器，去jdk定义好的类复制就行，其原因是能满足当有异常发生时能自动产生对象

  - 提供一个全局常量了标记该类

    ```java
    static final long seriaVersionUID=12345L;//取值是多少无所谓，唯一即可
    ```

- 自定义异常类的目的：让我们能明确的知道发生了是什么异常，这样就能便于处理



## 多线程

### 相关概论

#### 程序、进程、线程

- 程序：为满足特定任务，用某种语言编写的一组指令集合
  - 是静态代码
  
- 进程：程序的一次执行过程，或是正在内存中运行的应用程序
  - 每个进程都有自己独立的栈空间，系统运行一个程序即是一个进程的创建，运行到消亡的过程
  - 程序是静态的，而进程是其动态的过程
  - 进程是OS调度和分配资源的最小单位，系统在运行时会为每个进程分配不同的内存区域
  - 现代的OS大多都支持多进程，比如后台同时运行多个应用
  
- 线程：进程的进一步划分，也可以称为是轻量级进程，是程序内部的一条执行路径，一个进程至少有一个线程，同一个进程的不同线程共享进程资源，线程内部有自己独有的栈空间，但是不具备堆空间
  - 一个进程同一时间如果能并行多个线程，就是支持多线程的![image-20230329095320533](image\image-20230329095320533.png)
  
  - 线程是cpu调度和执行的基本单位
  
  - 线程有独立的栈空间
  
    >
    >
    >线程之间的通讯是依靠于进程的堆空间，两个线程操作同一个数据的时候也就相当于是在通讯了，当然进程之间也是需要通讯并且是很必要的，比如在淘宝中打开支付宝支付，vx访问相册等，但进程之间的通讯就会复杂很多

#### 线程调度

- 分时调度：线程轮流执行cpu的使用权，每个线程使用固定时间
- 抢占式调度：优先级高的线程优先使用cpu，如果优先级相同则会随机选择一个，java使用的就是抢占型调度，但这个时候就会带来饥饿甚至是饿死的情况

#### 多线程的优点

- 提高了应用程序的响应，可以同时干多件事情 ，比如qq可以一边发消息一边收消息，而不是在收消息的时候就不能发消息了
- 提高了cpu的利用率，将一堆线程都丢给cpu让他自己调度，能充分利用cpu
- 改善程序结构，将又长又复杂的进程分为多个线程，独立执行，便于理解和修改

### 线程的创建

#### 继承Thread类

- 创建过程	

  - 创建一个继承于Thread类的子类

  - 重写Thread类中run方法（方法体也就是线程要执行的操作）

  - 创建该子类的对象

  - 通过对象调用start()：启动线程，并调用该线程的run()

    >既然没有在子类中重写start()方法，那也就是说start()是继承于父类Thread中的
    >
    >可以通过Thread.currentThread().getname()来获取该线程的名

- 注意事项

  - 虽然说start()是在调用run()，但是我们不能说直接通过对象去掉run()，这样会导致并没有创建线程，而只是单纯的调用了一个方法

  - 对于已经调用start()的对象是不能再被start()的，也就是说如果要创建多个线程就得创建多个对象，然后再对每一个对象调用start()

  - 由于线程的调度具有随机性，所以每次执行的中间过程可能是不同的

    ```java
    //标准写法
    
    //线程输出一百以内的偶数
    class EvenPrint extends Thread{
        @Override
        public void run() {
            for(int i = 0;i <= 100;i++){
                if(i % 2 == 0)
                    System.out.println(Thread.currentThread().getName()+": "+i);
            }
        }
    }
    //线程输出100以内的奇数
    class OddPrint extends Thread{
        @Override
        public void run() {
            for(int i = 0;i <= 100;i++){
                if(i % 2 != 0)
                    System.out.println(Thread.currentThread().getName()+": "+i);
            }
        }
    }
    
    public class ThreadTest{
        public static void main(String[] args) {
            EvenPrint evenPrint = new EvenPrint();
            OddPrint oddPrint = new OddPrint();
            evenPrint.start();;
            oddPrint.start();
        }
    }
    
    
    
    
    //匿名子类的写法
    public class Test {
        public static void main(String[] args) {
            new Thread(){
                @Override
                public void run() {
                    for(int i = 0;i <= 100;i++){
                        if(i % 2 != 0)
                            System.out.println(Thread.currentThread().getName()+": "+i);
                    }
                }
            }.start();
            new Thread(){
                @Override
                public void run() {
                    for(int i = 0;i <= 100;i++){
                        if(i % 2 == 0)
                            System.out.println(Thread.currentThread().getName()+": "+i);
                    }
                }
            }.start();
        }
    }
    ```

#### 实现Runnable接口

- 创建一个实现类去实现Runnable接口

- 实现接口中的run()

- 创建当前实现类的对象

- 将实现类的对象作为参数传递到Thread类的构造器中，创建Thread类的实例对象

- 通过Thread类的对象调用start()

  ```java
  public class RunnableTest{
      public static void main(String[] args) {
          /**
          *	但其实声明的Runnable1的对象在进行传参的时候
          *	调用构造器创建对象，其实传入的Runnable1对象就相当于是一个形参数据
          *	所以如果只是产生新的分线程，是可以复用Runable1对象的
          *	也就是两个线程但完成的是同样的功能
          */
          Runnable1 runnable1 = new Runnable1();
          Runnable2 runnable2 = new Runnable2();
          Thread thread1 = new Thread(runnable1);
          Thread thread2 = new Thread(runnable2);
          thread1.start();
          thread2.start();
          
      }
  }
  class Runnable1 implements Runnable{
      @Override
      public void run() {
          for(int i = 0;i <= 100;i++){
              if(i % 2 == 0)
                  System.out.println(Thread.currentThread().getName()+": "+i);
          }
      }
  }
  
  class Runnable2 implements Runnable{
      @Override
      public void run() {
          for(int i = 0;i <= 100;i++){
              if(i % 2 != 0)
                  System.out.println(Thread.currentThread().getName()+": "+i);
          }
      }
  }
  
  
  //匿名实现的接口方式
  public class Test {
      public static void main(String[] args) {
          new Thread(new Runnable(){
              @Override
              public void run() {
                  for(int i = 0;i <= 100;i++){
                      if(i % 2 == 0)
                          System.out.println(Thread.currentThread().getName()+": "+i);
                  }
              }
          }).start();
          new Thread(new Runnable(){
              @Override
              public void run() {
                  for(int i = 0;i <= 100;i++){
                      if(i % 2 != 0)
                          System.out.println(Thread.currentThread().getName()+": "+i);
                  }
              }
          }).start();
      }
  }
  ```

#### 两者对比

- 相同点

  - 启动线程，使用的都是Thread类中的run()
  - 创建的线程对象，都是Thread类或者其子类的实例

- 不同点：

  - 一个是类的继承，一个是接口的实现

- 建议使用：实现接口

  - 实现接口避免了单继承的局限性

  - 共享数据的处理会更加方便，继承必须是静态数据

    >
    >
    >Threadl类其实也是实现的是Runnable接口

### Thread类中的常用方法和生命周期

- 线程中的构造器
  - public Thread()：分配一个新的线程对象
  - public Thread(String name)：分配一个名字为name的新的线程对象
  - piblic Thread(Runnable target)：指定创建一个线程的目标对象，实现Runnable接口中的run()
  - public Thread(Runnable target , String name)：创建一个名字为name的实现Runnable接口的线程对象

- 线程中常用方法
  - start()：启动线程，调用线程的run()
  - run()：将线程要执行的操作，写在方法体中
  - currentThread()：获取当前执行的代码对应的线程
  - getName()：获取线程名
  - setName()：设置线程名
  - sleep()：静态方法，在调用时，可以使当前线程睡眠指定的毫秒(形参给出)
  - yield()：静态方法，主动释放cpu的使用权 
  - join()：在线程a中通过线程b调用join()，则线程a阻塞直到线程b执行结束
  - isAlive()：查看线程是否存 活

- 线程优先级

  - 三个默认常量

    - MAX_PRIORITY(10)
    - MIN_PRIORITY(1)
    - NORM_PRIORITY(5)

  - 优先级常用方法

    - getPrioirity()

    - setPriority()：范围1-10

      >
      >
      >优先级只是执行的概率，优先级大的执行概率高，而不是说高的执行完之后才执行低的

- 生命周期

  - JDK1.5之前

  ![image-20230331113813670](image\image-20230331113813670.png)

  - JDK1.5之后![image-20230331114145679](image\image-20230331114145679.png)

  

>
>
>也就是将阻塞状态进行三种细致的划分，并且将就绪和运行合并为了Runnable状态

### 线程的安全问题

- 其实线程的安全问题，也就是不同线程同时操作共享数据，导致了共享数据和预期不一致的情况，比如同时修改修改或者还没修改结束又被读取等，这种时候就可以通过锁机制来解决，当一个线程在操作共享数据的时候对其上锁，当其操作结束后才允许别的线程对该共享数据进行操作

- 实现同步的两种方式

  - 同步代码块

    - 格式：

      ```java
      synchronize (同步监视器){
      	//需要被同步的代码，其实也就是对共享数据的操作部分
      }
      ```

      >
      >
      >同步监视器是任意一个唯一的对象就行
      >
      >在实现Runnabble接口中常常用this比较方便，因为常常是创建一个实现的对象去给不同的Thread对象赋值，所以只会有一个this对象
      >
      >但是对于继承Thread类的方法就不靠谱了,因为这时一定是多次new，也就有多个对象，那么不同的this指向的是不同的对象，这个时候需要在类成员变量中写一个static对象即可，但最常用的是使用类名.class，这是每一个Class类（JDK中定义的）的对象，具体讲解会在反射中给出

    - 说明

      - 需要被同步的代码，也就是操作共享数据的代码

      - 共享数据，也就是多线程都能访问的数据

        比如实现接口只定义了一个变量，创建一个接口实现类对象给不同的Thread对象赋值

        再比如继承Thread类，在子类中将变量声明为static

      - 同步监视器可以是任意一个类的对象，是多个线程必须共用同一个同步监视器
      - 获得同步监视器，也就是锁的线程可以执行后续代码其余的线程必须等待，即阻塞住

    - 实现Runnable接口：

      ```java
      class Nump implements Runnable{
          int num=0;
          //Object object = new Object();
          @Override
          public void run() {
              while (true){
                  try {
                      Thread.sleep(5);
                  } catch (InterruptedException e) {
                      throw new RuntimeException(e);
                  }
                  synchronized (this){
                      if(num <= 100){
                          System.out.print(Thread.currentThread().getName()+": ");
                          System.out.println(num);
                          num++;
                      }
                      else{
                          break;
                      }
                  }
              }
          }
      }
      
      public class NumberPrint {
          public static void main(String[] args) {
              Nump nump = new Nump();
              Thread thread1 = new Thread(nump);
              Thread thread2 = new Thread(nump);
              Thread thread3 = new Thread(nump);
      
              thread1.start();
              thread2.start();
              thread3.start();
          }
      
      
      }
      ```

    - 继承Thread类

      ```JAVA
      class NumP extends Thread{
          static int num = 0;
          @Override
          public void run() {
              while (true){
                  try {
                      Thread.sleep(5);
                  } catch (InterruptedException e) {
                      throw new RuntimeException(e);
                  }
                  synchronized (NumP.class){
                      if(num <= 100){
                          System.out.print(Thread.currentThread().getName()+": ");
                          System.out.println(num);
                          num++;
                      }
                      else{
                          break;
                      }
                  }
              }
          }
      }
      public class NumThread {
          public static void main(String[] args) {
              Thread thread1 = new NumP();
              Thread thread2 = new NumP();
              Thread thread3 = new NumP();
      
              thread1.start();
              thread2.start();
              thread3.start();
          }
      }
      ```

      

  - 同步方法：将需要同步的代码抽出成为一个方法，用synchronize修饰

    - 实现Runnable接口

      ```java
      class NumP1 implements Runnable{
          int num = 0;
          Boolean isFlag = true;
      
          @Override
          public void run() {
              while (isFlag){
                  show();
              }
          }
      
          public synchronized void show(){
              try {
                  Thread.sleep(5);
              } catch (InterruptedException e) {
                  throw new RuntimeException(e);
              }
              synchronized (this){
                  if(num <= 100){
                      System.out.print(Thread.currentThread().getName()+": ");
                      System.out.println(num);
                      num++;
                  }
                  else{
                      isFlag = false;
                  }
              }
          }
      }
      
      public class NumberPrint {
          public static void main(String[] args) {
              NumP1 nump = new NumP1();
              Thread thread1 = new Thread(nump);
              Thread thread2 = new Thread(nump);
              Thread thread3 = new Thread(nump);
      
              thread1.start();
              thread2.start();
              thread3.start();
          }
      
      
      }
      ```

    - 继承Thread类

      ```java
      class NumP1 extends Thread{
          static int num = 0;
          static Boolean isFlag = true;
          @Override
          public void run() {
              while (true){
                  show();
              }
          }
      
          public static synchronized void show(){
              try {
                  Thread.sleep(5);
              } catch (InterruptedException e) {
                  throw new RuntimeException(e);
              }
              if (num <= 100) {
                  System.out.print(Thread.currentThread().getName() + ": ");
                  System.out.println(num);
                  num++;
              } else {
                  isFlag = false;
              }
      
          }
      }
      
      public class NumThread {
          public static void main(String[] args) {
              Thread thread1 = new NumP1();
              Thread thread2 = new NumP1();
              Thread thread3 = new NumP1();
      
              thread1.start();
              thread2.start();
              thread3.start();
          }
      }
      ```

    >
    >
    >对于同步方法其默认的监视器是this，所以当我们用继承Thread类的方式实现多线程一定会创建多个对象，则这样显然每个this就是不同的对象，this还不能修改，当仅仅满足需要的时候可以将其变为静态方法则监视器就是类.class，但这样会有局限性，因为可能别人就行想要实例方法，比如人家会调用实例变量，于是这种时候可以在方法内部使用同步代码块的方式实现

    - 改进后的实现

    ```java
    class NumP1 extends Thread{
        static int num = 0;
        static Boolean isFlag = true;
        @Override
        public void run() {
            while (true){
                show();
            }
        }
    
        public synchronized void show(){
            try {
                Thread.sleep(5);
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
            synchronized (NumP1.class){
                if (num <= 100) {
                    System.out.print(Thread.currentThread().getName() + ": ");
                    System.out.println(num);
                    num++;
                } else {
                    isFlag = false;
                }
            }
    
        }
    }
    
    public class NumThread {
        public static void main(String[] args) {
            Thread thread1 = new NumP1();
            Thread thread2 = new NumP1();
            Thread thread3 = new NumP1();
    
            thread1.start();
            thread2.start();
            thread3.start();
        }
    }
    ```

- synchronize的优劣

  - 优点：解决了线程安全的问题

  - 缺点：对于共享数据，其实是很粗暴的将本来应该并行执行直接变为串行执行，显然效率是会     降低的

    >
    >
    >其实也就是OS中的PV锁，或者是DB的两段锁协议等，当只读的时候是可以共享都读，当要修改共享数据的时候才上锁才是比较好的实现方式

### 解决懒汉式的线程安全问题

```java
public class LanhanThread {
    static Bank bank1 = null;
    static Bank bank2 = null;
    public static void main(String[] args) {
        Thread thread1 = new Thread(){
            @Override
            public void run() {
                bank1 = Bank.getBank();
                System.out.println(bank1);
            }
        };
        Thread thread2 = new Thread(){
            @Override
            public void run() {
                bank2 = Bank.getBank();
                System.out.println(bank2);
            }
        };

        thread1.start();
        thread2.start();

    }
}

class Bank{
    private Bank(){
    }
	
    //private static Bank bank = null;
    //避免指令重排
    private static volatile Bank bank = null;

    //public static Bank getBank(){//也就是在这把获取单例的方法改为同步方法，当然也可以是同步代码块的方式实现
    
    //同步方法
    public static synchronized Bank getBank(){
        try {
            Thread.sleep(10);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }
        if(bank == null){
            bank = new Bank();
        }
        return bank;
    }
    
    //同步代码块
    /**
    *	两层if嵌套的目的是为了优化，即当已经有实例对象的时候只需要通过if判断即可，
    *	有了直接就return，不用大伙都在那排队，好不容易才排到自己了然后发现已经有了
    *	也就是说只有真正没有的时候才去排队，就让排队都有意义了
    */
    public static Bank getBank(){
        if(bank == null){
            synchronized(Bank.class){
                try {
                    Thread.sleep(10);
                } catch (InterruptedException e) {
                    throw new RuntimeException(e);
                }
                if(bank == null){
                    bank = new Bank();
                }
            }
        }
        return bank;
    }
}
```

>
>
>但即使是这样也会有其他问题：指令重排
>
>在第一个线程正在new的时候，其实对象的创建是分好多步骤的，当其还没创建完成的时候当第二个线程进入第一个if判断发现已经不是null了就把还未创建完成的对象拿走了，解决方法就是在对象声明的时候加上volatile关键字，也相当于一个锁，当创建完全完成的时候才把对象返回给主存



### 死锁

- 不同的线程分别占用对方需要的同步资源， 都在等待对方放弃自己需要的同步资源，自己又不放弃



- 死锁产生的条件
  - 互斥条件：对于同步资源不能共享访问，也就是说有用访问的时候我就不能访问
  - 占用且等待：当我在等待其他资源的时候，还不放弃手中已经占用的资源
  - 不可抢占：当我需要访问的同步资源正在被别的线程访问时我只能等他访问结束而不能抢夺
  - 循环等待：我在等你的，你又在等我的 
- 解决死锁：也就是破坏一个死锁产生的条件
  - 针对1：为了线程的安全，就是需要满足互斥条件，所以是不能破坏条件1的
  - 针对2：一次性申请线程所需的所有资源
  - 针对3：
    - 设置优先级，高优先级的可以线程可以抢占低优先级线程的资源
    - 当线程等待一段时间后，主动回退释放手中占用的资源
  - 针对4：将所有资源线性编号，已经有了小号的资源才可申请大号资源

### Lock的使用

- 使用步骤

  - 创建Lock的实例，由于是锁就需要多个线程共用一个Lock实例，所以应该设置为static

  - 执行lock()进行上锁

  - 执行unlock()进行解锁

    ```java
    class LockThread extends Thread{
        static int num = 0;
        //1.lock的声明
        private static ReentrantLock lock = new ReentrantLock();
    
        @Override
        public void run() {
            while (true){
                try {
                    //2.对同步资源上锁
                    lock.lock();
                    try {
                        Thread.sleep(10);
                    } catch (InterruptedException e) {
                        throw new RuntimeException(e);
                    }
                    if(num <= 100){
                        System.out.println(Thread.currentThread().getName()+": "+num);
                        num++;
                    }else break;
                }finally {
    
                    //3.对同步资源解锁
                    lock.unlock();
    
                }
            }
        }
    }
    
    public class LockTest {
        public static void main(String[] args) {
            Thread thread1 = new LockThread();
            Thread thread2 = new LockThread();
            thread1.start();
            thread2.start();
        }
    }
    ```

>
>
>为什么要把lock()和unlock()用try-finally包裹？
>
>如果不包裹则当一个线程到结束条件的时候直接break了但这个时候是没有解锁的，虽然这个程序不会有安全问题，但程序会一直运行无法结束，为了一定能有解锁操作所以把上锁和解锁用try-finally包裹

- synchronized和Lock的区别
  - synchronized对于资源的释放是在{}结束之后，而Lock是在unlock()方法的调用处，更灵活
  - Lock作为接口有很多实现类，对于更多复杂情况会有更适合的锁



### 线程间的通信

-   有时我们需要多个线程共同完成一件事，并且我们希望他们是有规律的执行，那么在多线程之间就会存在通信机制来协调他们之间的工作

- 三个方法的使用

  - wait()：线程一旦执行此方法，就会进入到阻塞状态，并且会释放对同步监视器的调用

  - notify()：一旦执行此方法，会唤醒优先级最高的线程，如果被wait()的线程优先级相同，则随机唤醒一个线程

  - notifyAll()：唤醒所有wait的线程

    >
    >
    >- 三个方法的调用者都是同步监视器，所以一定是使用在同步代码块或者同步方法中，不能使用与Lock中，对于Lock有自己的通信机制
    >- 这三个方法都声明在Object类中，任意对象都可能调用这三个方法，因为同步监视器可以是任何一个类的对象

- wait()和sleep()的区别

  - 相同点：一旦执行都会使线程进入阻塞状态
  - 不同点：
    - 声明位置不同：
      - wait()声明在Object类中
      - sleep声明在Thread类中并且是静态的
    - 使用场景不同：
      - wait()只能使用在同步代码块和同步方法中
      - sleep()可以使用在线程的任何地方
    - 对于同步监视器的占用：
      - wait()会立即释放对同步监视器
      - sleep()不会释放同步监视器就进入了阻塞状态
    - 结束阻塞状态的方式
      - wait()可以是时间到，也可以被notify()唤醒
      - sleep()则一定是时间到

### 生产者消费者问题

```java
//店员
public class Clerk {
    private int num = 0;

    public synchronized void incNum(){
        if(num < 20){
            num++;
            System.out.println("生产生产生产！！ 库存为：" + num);
            notify();
        }else{
            try {
                wait();
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
        }
    }

    public synchronized void decNum(){
        if(num == 0){
            try {
                wait();
            } catch (InterruptedException e) {
                throw new RuntimeException(e);
            }
        }else{
            num--;
            System.out.println("消费消费消费！！ 库存为：" + num);
            notify();
        }
    }

}
//生产者
public class Producer implements Runnable {
    private Clerk clerk;
    Producer(Clerk clerk){
        this.clerk=clerk;
    }
    @Override
    public void run() {
        while (true){
            produce();
        }
    }

    public synchronized void produce(){
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }
        clerk.incNum();
    }
}
//消费者
public class Consumer implements Runnable {
    private Clerk clerk;
    Consumer(Clerk clerk){
        this.clerk=clerk;
    }
    @Override
    public void run() {
        while (true){
            consumer();
        }
    }
    public synchronized void consumer(){
        try {
            Thread.sleep(2000);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }
        clerk.decNum();
    }
}

//Test
public class ProduceTest {
    public static void main(String[] args) {
        Clerk clerk = new Clerk();
        Producer producer = new Producer(clerk);
        Consumer consumer = new Consumer(clerk);
        Thread thread1 = new Thread(producer);
        Thread thread2 = new Thread(consumer);

        thread1.start();
        thread2.start();

    }
}
```

### JDK5.0之后新增的两种创建线程的方式

#### 实现Callable接口

- 其实Callable接口也就是将Runnable接口再封装一下
- 实现Callable接口和Runnable接口的区别
  - 重写的方法不同
    - Callable接口：重写call()
    - Runnable接口：重写run()
  - 返回值
    - Callable接口：可以有返回值，并且使用泛型参数甚至能指明具体的返回值类型是什么
    - Runnable接口：没有返回值
  - 异常处理
    - Callable接口：可以抛出异常不做处理（编译型和运行时都可）
    - Runnable接口：只能try-catch
- Callable的缺点
  - 主线程是处于阻塞状态

#### 使用线程池

- 原因：并发的时候，如果并发需要的线程很多，并且每一个线程的执行时间又比较短，频繁的创建销毁线程会导致效率低下

- 设计思路：提前创建很多线程，放入到线程池中，使用时直接获取，使用完就放回，重复利用， 不在需要频繁的创建销毁的过程

- 好处
  - 提高了程序执行的效率，线程已经提前准备好了不需要创建
  - 提高了资源复用率，执行结束的线程并没有销毁，还可以重复使用
  - 可以设置相关参数：比如更加网络情况设置最大线程数等等，自己创建线程则无法约束

### 面试真题

- 什么是线程
  - 进程中的一条执行路径，是cpu调度的最小单位
- 进程和线程的区别
  - 进程对应一个执行中的程序
  - 线程对应运行中进程的一个执行路径
- 多线程使用场景
  - 下载行为
  - Tomcat服务器的web应用：多个客户端发起请求，针对不同的请求用不同的线程响应
- 如何实现多线程
  - 也就是四种线程的实现方式
- start()和run()的区别
  - start()：开启线程，调用线程的run()
  - run()：如果只是执行run()，就相当于是执行了一个普通方法，是没有开辟线程的
-   Runnable和Callable的区别 
- sleep()和yield()区别
  - sleep()：进入阻塞状态
  - yield()：还在运行态，只是把cpu的使用权让出
- 线程安全问题等
- synchronized加在静态方法和普通方法的区别
  - 静态方法：同步监视器是类.class
  - 普通方法：同步监视器是this
-  产生死锁的原因，怎么避免死锁
- notify()和notifyAll()的区别

- 为什么wait()和notify()必须在同步块中调用
  - 其调用者规定是同步监视器
- wait()和sleep()区别



## 常用类的API

### String类

#### 类的声明

- public final class String implements java.io.Serializable , Comparable<String>，CharSequence
  - final：说明String是不可被继承
  - Serializable：可序列化接口，实现该接口的对象可以在网络或本地流进行数据传输
  - Comparable<String> : 实现该接口的对象可以直接比较对象的大小
  - CharSequence

#### 内部声明的属性

- private final char value[]

  - 对于字符串的具体实现，其实就是在内部定义了一个字符数组，也就是将字符串中的每一个字符分别填入在字符数组之中

    >
    >
    >由于是定义为的final所以该数组一旦定义就不能改变，但在实际中我们明明是能对字符串的自变量进行改变的，这不是矛盾的吗？其实我没每次对字符串的改变都是新建了一个数组，并且将新的数组的自变量赋给了字符串对象

#### 字符串常量的存储位置

- 字符串常量存储在字符串常量池(String Table)中

- 对于字符串常量池是不能有两个相同的字符串常量

  ```java
  String s1 =  "hello";
  
  String s2 = "hello";
  
  System.out.println(s1==s2)//true
  ```

- JDK7之后常量池之后都放在堆空间中

#### String的不可变性

- 当字符串常量重新赋值时，需要重新指定一个字符串常量的位置进行赋值(也就是相当于重新开辟了一个字符数组，因为在之前说过String内部的字符数组是final不可改变的)，不能在原来的位置改变之前的值

  ```java
  @Test
  public void test(){
      String s1 = "hello";
      String s2 = "hello";
      s2 = "hi";
      System.out.println(s1);//hello
      System.out.println(s2);//hi
  }
  ```

- 对字符串进行拼接操作时，同样也不能在原来的位置直接进行操作，同样也需要新开辟一个字符串常量的位置，但这时的位置不再是字符串常量池了，而是在堆中

  ```java
  @Test
  public void test2(){
      String s1 = "hello";
      String s2 = "hello";
      s2 += "world";
      System.out.println(s1);//hello
      System.out.println(s2);//helloworld
  }
  ```

  

- 对于replace()方法，其不是在原来的字符串上进行修改，也是重新定义了一个字符串接收修改后的结果并且返回，同样新字符串也是在堆中

  ```java
  @Test
  public void test3(){
      String s1 = "hello";
      String s2 = "hello";
      String s3 = s2.replace("l","a");
      System.out.println(s1);//hello
      System.out.println(s2);//hello
      System.out.println(s3);//heaao
  }
  ```

  >
  >
  >虽然字符串常量池由于不能有相同的字符串常量，也就相当于说不能定义两个同名变量是一样的，虽然当两个字符串字面量相同的时候地址值是一样的，但这时对其中一个字符串进行修改的时候是不影响另一字符串的，因为在修改的时候就不是在原字符串常量上进行修改，而是重新开辟了一个字符串常量，所以肯定是会影响原字符串常量的字符串对象

#### String的实例化

- 两种方式创建String对象

  - String s1 = "hello";

  - String s2 = new String("hello");

  - 区别

    ```java
    String s1 = "hello";
    String s2 = "hello";
    String s3 = new String("hello");
    String s4 = new String("hello");
    
    //判断地址
    System.out.println(s1 == s2);//true
    System.out.println(s3 == s4);//false
    System.out.println(s1 == s3);//false
    System.out.println(s1 == s4);//false
    
    //判断字面量
    System.out.println(s1.equals(s2));//true
    System.out.println(s3.equals(s4));//true
    System.out.println(s1.equals(s3));//true
    System.out.println(s1.equals(s4));//true
    ```

    >
    >
    >对于字面量声明的方式，由于之前说的字符串常量池不能有相同的两个常量，所以地址是一样的，对于构造器的方式，都是先在堆中产生一个对象，该对象的值又指向字符串常量池中的对象

  - eg：对于构造器的方式内存中产生了几个对象

    - 两个，一个是堆中的对象，一个是字符串常量池中的对象

      ![image-20230403154229582](image\image-20230403154229582.png)

#### 字符串的连接操作

- 常量+常量

  - 结果仍然存储在字符串常量池中，返回字符串常量池中的地址

- 变量+常量，变量+变量

  - 通过在堆中new一个新的对象，返回堆中字符串的地址

    ```java
    String s1 = "hello";
    String s2 = "world";
    String s3 = "hello"+"world";//返回字符串常量池中的地址
    String s4 = s1 + "world"//放回堆中字符串的地址
    ```

    >
    >
    >final修饰的变量也就是常量
    >
    >final String s1 = "hello";
    >
    >String s2 = "world"
    >
    >String s3 = s1 + "world" //返回的也是字符串常量池中的地址 

>
>
>在java规范中所有有关索引的区间都是左闭右开，所以比如快排传入两个下标的时候是0和length



#### StringBuffer和StringBuilder

- 和String的对比

  - String：不可变的字符序列（每次的修改都是在字符常量池或者堆中新建）
  - StringBuffer：可变的字符序列(在源字符串位置直接改变，是线程安全的)
  - StringBuilder：可变的字符序列(线程不安全的，但是效率更高 )

- 三者底层实现

  - String：

    ```java
    String s1 = new String(); //char[] value = new char[0];
    String s2 = new String("abc");//char[] value = new char [3]{'a','b','c} 
    ```

    由于都定义为定长数组所以其长度不可变，底层的value定义为final所以地址也不可能改变

  - StringBuilder

    ```java
    StringBuilder sb1 = new StringBuilder();//char[] value = new char[16];
    StringBuilder sb1 = new StringBuilder("abc");//char[] value = new char[16+"abc".length]
    ```

    - 内部属性

      - char[] value;//存储字符序列
      - int count;// 实际存储的字符的个数

      >
      >
      >其默认长度为16，在实际字符串之前空出16个下标来给后续的增加，当加了第十七个字符时，就会新建一个数组容量为原容量的两倍＋2，再把原数组元素复制到新数组

- 使用提示

  - 开发中需要频繁对字符串进行增删改等操作时建议用StringBuilder和StringBuffer来代替String，String的效率较低
  - 如果开发中不涉及到线程安全问题，建议使用StringBuilder来替换StringBuffer，不需要同步方法来获得锁
  - 如果在开发中大致知道操作的字符个数，建议使用带有int capacity参数的构造器，可避免多次扩容来提高性能

- 常用的方法

  - 增
    - append(xx)：在尾部进行添加，容量不够则扩容

  - 删
    - delete(int start，int end)：删除从start到end之间的元素，左闭右开
    - deleteCharAt(int index)：删除对应下标的元素
  - 改
    - replace(int start , int end , String str)：把从start到end之间的字符修改为str
    - replaceCharAt(int  index , char c )：把index下标的字符修改为c
  - 查
    - charAt(int index)：查询index对应的字符
  - 插
    - insert(int index , xx)：在index下标处插入xx
  - 长度
    - length()
  - 反转：
    - reverse()



### 时间日期的API

#### JDK8之前的

##### System类中

- currentTimeMillis()
  - 获取当前时间对应的毫秒数，当前时间与1970.1.1日零时零分零秒之间的毫秒值
  - 常用于计算时间差

```JAVA
//System
@Test
public void test1(){
    System.out.println(System.currentTimeMillis());//1680760108528L
}
```

##### 两个Date类

###### util类下

- 两个构造器
  - 空参：创建一个基于当前系统时间的Date实例
  - 传入Long值：创建一个指定时间戳的Date实例
- 两个方法
  - toString()：放回人能读懂的当前时间格式
  - getTime()：返回时间戳，也是基于1970年的时间戳

```JAVA
//util.Date
@Test
public void test2(){
    Date date1 = new Date();
    System.out.println(date1.toString());//Thu Apr 06 13:48:28 CST 2023
    System.out.println(date1.getTime());//1680760108528L

    Date date2 = new Date(date1.getTime());
    System.out.println(date2.toString());//Thu Apr 06 13:48:28 CST 2023
}
```

###### sql类中

- 其实也就是util的一个子类
- 对应数据库中的Date类型
- 只有一个构造器
  - 传入具体的时间戳J

```JAVA
//sql.Date
@Test
public void test3(){
    java.sql.Date date1 = new java.sql.Date(1680760108528L);//由于之前已经导入了util的Date所以必须显示声明
    System.out.println(date1.toString());//2023-04-06
    System.out.println(date1.getTime());//1680760108528L
}
```

##### SimpleDateFormate类

- 用于时间日期的格式化和解析

  - 格式化：日期 --->字符串
  - 解析：字符串--->日期

  ```java
  @Test
  public void test4() throws ParseException {
      Date date = new Date();
      SimpleDateFormat sdf = new SimpleDateFormat();
      //格式化为默认格式
      String time = sdf.format(date);
      System.out.println(time);//23-4-6 下午2:52
      //格式化为指定格式,有很多格式可以选择，具体格式定义看官方的API文档
      SimpleDateFormat sdf1 = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
      String time1 = sdf1.format(date);
      System.out.println(time1);//2023-04-06 14:57:47
      //解析
      Date date2 = new Date();
      date2 = sdf.parse("23-4-6 下午2:52");
      System.out.println(date2);//Thu Apr 06 14:52:00 CST 2023
  }
  ```

##### Calendar类

- Date类中很多API都过时了，被Calendar类所取代

- 实例化

  - 由于Calendar类是一个抽象类，不能创建对象，所以我们需要创建其子类对象，或者通过Calendar类中的静态方法getInstance()来获取实例

    ```java
    Calendar calendar = new GregorianCalendar();
    Calendar calendar1 = Calendar.getInstance();
    ```

- 常用方法

  - get(int field)：返回实例的静态常量信息

  - set(int field,xx)：把实例的静态常量信息重设

  - add(int field,xx)：把实例的天数前后推移等，操作数为正则后退，为负则前推

  - getTime()：返回一个Date实例

  - setTime()：用一个指定的Date重置一个Calendar实例

    >
    >
    >Field是Calendar类中定义的一些静态常量具体的看看API就好

    ```java
    @Test
    public void test6(){
        //2023-4-6,周四
        Calendar calendar = Calendar.getInstance();
        //get()
        System.out.println(calendar.get(Calendar.DAY_OF_WEEK));//5,默认周天是1
        System.out.println(calendar.get(Calendar.DAY_OF_MONTH));//6
        //set()
        calendar.set(Calendar.DAY_OF_WEEK,1);//将其改为了这个周的第一天
        System.out.println(calendar.get(Calendar.DAY_OF_WEEK));//1
        //add()
        calendar.add(Calendar.DAY_OF_WEEK,3);//将其改为这周的三天后
        System.out.println(calendar.get(Calendar.DAY_OF_WEEK));//4
        calendar.add(Calendar.DAY_OF_WEEK,-2);//将其改为这周的两天前
        System.out.println(calendar.get(Calendar.DAY_OF_WEEK));//2
        //getTime()
        Date date = calendar.getTime();
        System.out.println(date);//Mon Apr 03 15:39:08 CST 2023
        //setTime
        Date date1 = new Date();
        calendar.setTime(date);
        System.out.println(calendar.get(Calendar.DAY_OF_WEEK));//2,因为上面已经改为了这周的第二天
    
    }
    ```

#### JDK8中的日期API

- 之前日期API的缺点

  - 可变性：对于日期时间应该像String一样是不可变的，即其本身时间不可改变，返回一个修改过的时间

    >
    >
    >就比如上面的代码示例，最后一行代码应该输出是周四的第五天，而不是之前修改过变为的第二天，也就相当于我们传入的形参应该只是值，最后返回期望的结果，而不对原数据进行修改

  - 偏移性：Date中的起始日期是1970年开始

    ```java
    Date date = new Date(2023,4,6);//但最终生成的对象是从1970开始偏移的所有压根就不是我们想要的这个日期而是Sun May 06 00:00:00 CST 3923
    ```

  - 格式化：Date大部分都被Calendar替代，但是格式化只支持Date类

  - 无论是Date还是Calendar都是线程不安全的，也不能出现闰秒等

- 三个不同的类

  - LocalDate：日期
  - LocalTime：时间
  - LocalDateTime：日期加时间

- 两种获取实例的方式

  - now()：静态方法，获取当前日期和时间的实例

    ```java
    @Test
    public void test7(){
        LocalDate localDate = LocalDate.now();
        LocalTime localTime = LocalTime.now();
        LocalDateTime localDateTime = LocalDateTime.now();
        System.out.println(localDate);//2023-04-06
        System.out.println(localTime);//16:31:02.153
        System.out.println(localDateTime);//2023-04-06T16:31:02.153
    }
    ```

  - of()：静态方法，获取指定日期和时间的实例

    ```java
    @Test
    public void test8(){
        LocalDate localDate = LocalDate.of(2023,4,5);
        LocalTime localTime = LocalTime.of(16,3,5);
    
        System.out.println(localDate);//2023-04-05
        System.out.println(localTime);//16:03:05
    }
    ```

- 常用的方法
  - 和Calendar中的增删改意思差不多，但是具体使用看官网API文档即可，这些方法都不会改变调用的实例，只是返回了期望的结果

- DateTimeFormatter：

  - 也类似于SimpleTimeFormatter用于格式化和解析

    ```java
    @Test
    public void test9(){
        //格式化
        DateTimeFormatter dtf = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss");
        LocalDateTime localDateTime = LocalDateTime.now();
        String time = dtf.format(localDateTime);
        System.out.println(time);//2023-04-06 17:00:27
    
        //解析
        String time1 = "2002-02-02 07:13:52";
        TemporalAccessor parse = dtf.parse(time1);//进行解析的时候是通过TemporalAccessor实现，其实现类就是日期类
        LocalDateTime localDateTime1 = LocalDateTime.from(parse);
        System.out.println(localDateTime1);//2002-02-02T07:13:52
    }
    ```

### 比较器

- 由于基本数据类型除了Boolean之外需要比较大小直接通过数学运算符即可，但是有时我们往往会给引用数据类型的对象排序，而引用数据类型存的是地址，对地址比较大小显然是不合适的，那么我们就需要通过对象的某些属性为标准来进行大小比较

#### Comparable接口：自然排序

- 对于普通String类是可以直接比较大小是因为String类实现了Comparable接口所以可以直接使用sort方法

  ```java
  @Test
  public void test1(){
      String str[] = new String[]{"Tom","Jack","Tony","Rose"};
      Arrays.sort(str);
      for(int i = 0; i < str.length; i++){
          System.out.println(str[i]);//Jack Rose Tom Tony
      }
  }
  ```

- 如果自定义类未实现Comparable接口则会直接进行比较则会抛出异常

  ```java
  public class Product {
      private String name;
      private double price;
  
      public Product(String name, double price) {
          this.name = name;
          this.price = price;
      }
  
      public String getName() {
          return name;
      }
  
      public void setName(String name) {
          this.name = name;
      }
  
      public double getPrice() {
          return price;
      }
  
      public void setPrice(double price) {
          this.price = price;
      }
  
      @Test
  	public void test2(){
      Product[] product = new Product[3];
      product[0] = new Product("huaweiMate50",7999);
      product[1] = new Product("iphone14pm",9999);
      product[2] = new Product("oppofindx6",4999);
    Arrays.sort(product);//java.lang.ClassCastException:Compare.Product cannot be cast to java.lang.Comparable
  }
  ```

- 自定义类实现了Comparable接口之后

  ```java
  public class Product implements java.lang.Comparable {
      private String name;
      private double price;
  
      public Product(String name, double price) {
          this.name = name;
          this.price = price;
      }
  
      public String getName() {
          return name;
      }
  
      public void setName(String name) {
          this.name = name;
      }
  
      public double getPrice() {
          return price;
      }
  
      public void setPrice(double price) {
          this.price = price;
      }
  
      @Override
      public String toString() {
          return "Product{" +
                  "name='" + name + '\'' +
                  ", price=" + price +
                  '}';
      }
  
      /**
       * 根据价格来比较大小升序排序
       * @param o the object to be compared.
       * @return  为正则当前对象大
       *          为负则当前对象小
       *          相等则两者一样大
       */
      @Override
      public int compareTo(Object o) {
          if(this == o)
              return 0;
         	if(o instanceof Product){
              Product p = (Product) o;
              //直接调用包装类的比较方法，前一个数和后一个数比，前者大则返回1,小返回-1，相等返回0
              return Double.compare(this.price , p.price);
          }
          throw new RuntimeException("类型不匹配");
      }
      @Test
      public void test2(){
          Product[] product = new Product[3];
          product[0] = new Product("huaweiMate50",7999);
          product[1] = new Product("iphone14pm",9999);
          product[2] = new Product("oppofindx6",4999);
          Arrays.sort(product);
          for(int i = 0; i < product.length; i++){
              System.out.println(product[i].toString());
          }
          /**
           * 结果：
           * Product{name='oppofindx6', price=4999.0}
           * Product{name='huaweiMate50', price=7999.0}
           * Product{name='iphone14pm', price=9999.0}
           */
      }
  }
  ```

- 具体步骤
  - 实现类A实现Comparable接口
  - 重写接口中的compareTo(Object o)方法，在方法内指明判断大小的标准
  - 创建类A的多个实例，就可以直接调用sort()来比较大小了

#### 使用Comparator接口：定制排序 

- 提出的原因

  - 有时对于一个类其本身没有实现Comparable接口，但是我们又不能更改其源码，比如说JDK中的Date类没有实现Comparable接口我们不可能说为了满足我们的需求去改JDK中的源码，我们也改不了
  - 对于那些实现了Comparable接口的类所实现的排序不是我们想要的结果，比如String类实现Comparable接口后是从小到大排序，但如果说我们的需求是从大到小排序呢，这个时候就无法满足我们需求了

- ```java
  @Test
  public void test3(){
      String str[] = new String[]{"Tom","Jack","Tony","Rose"};
      Comparator comparator = new Comparator() {
          @Override
          public int compare(Object o1, Object o2) {
              if(o1 instanceof String && o2 instanceof String){
                  String s1 = (String) o1;
                  String s2 = (String) o2;
  
                  return -s1.compareTo(s2);
              }
              throw new RuntimeException("类型不匹配");
          }
      };
      //在进行排序的时候同时传入Comparator的对象实例，每一个对象实例都可以定制一种排序方式
      Arrays.sort(str,comparator);
      for(int i = 0; i < str.length; i++){
          System.out.println(str[i]);//Tony Tom Rose Jack
      }
  }
  ```

- 具体步骤

  - 创建一个实现类A实现Comparator接口

  - 实现类重写compare(Object 01 , Object 02)，在此方法中指明要比较大小的对象的大小关系

    >
    >
    >因为这个时候的o1,o2并不是实现类A的对象，比如上述使用匿名类都没有实现类A，o1,o2是需要待比较大小的类，比如上述的String，或者其他自定义类等

  - 创建实现类A的对象，并将此对象作为参数传入给相关方法

#### 两者对比

- 角度一
  - 自然排序标准是唯一的
  - 定制排序标准是可变的，根据自己的需求变化而不同
- 角度二
  - 自然排序是一劳永逸的，所以常常使用于默认的情况
  - 定制排序是临时的，在每次使用的时候都需要创建专门的对象 
- 角度三
  - 自然排序是实现Comparable接口，重写compareTo(Object o)方法
  - 定制排序是实现Comparator接口，重写compare(Object o1, Object o2)方法

### 复习题

#### String

- 以下两种创建String对象有什么不同

  ```java
  String str = new String("test");
  String str = "test";
  ```

  >
  >
  >第一种是在堆空间中创建一个对象，如果字符串常量池中已经有了"test"，则直接引用其地址
  >
  >第二种是直接在字符串常量池中创建，所以要确保字符串常量池中不会有相同的字面量

- String s = new String("xyz")创建了几个String对象

  - 两个，一个在堆，一个在字符串常量池

- String a = "abc" ; String b = "a"+"bc"; 

  问a==b?

  - 是相等的

    >
    >
    >常量加常量出来的仍然是常量返回字符串常量池地址，有变量参与的返回堆空间的地址，当然有final修饰的变量也就视为常量了

- String类中的"+"怎么实现

  - 常量+常量：直接是在字符串常量池新建之后拼接
  - 有变量参与的：通过StringBuilder对象，通过append()添加字符串，然后通过toString()返回，在toString()内部new了一个String的实例

- String能否有子类等

  - String是final的所以不能被继承

- String为什么是不可变的

  - 在开发中String是用的很频繁的，所以很多字符串信息就可以共用，就可以不用新建，即节省了空间和时间

- subString()的实现

  - new了一个string然后其值是指定的下标中间的元素

#### String和StringBuilder，StringBuffer

- 三者的区别

  - String：不可变的序列，底层使用char[]实现，后面是Byte[]  (JDK9之后)

  - StringBuilder：可变的字符序列，效率高，但是是线程不安全的，底层实现和String相同

  - StringBuffer：可变的字符序列，效率较低，但是是线程安全的，底层实现和String相同

    >
    >
    >在前面空出了16个字符单元，当长度不够的时候进行扩容两倍+2

#### Comparator和Comparable

- 两者的区别和场景
  - 前者实现的是定制排序，其重写方法传入的是两个参数，每次都需要构造对象，并将对象作为参数传入到排序方法中
  - 后者实现的是自然排序，其重写的方法只传入一个参数，基本上作为一种默认排序的手段

## 集合框架

### 数组

- 存储数据的特点

  - 数组一旦初始化，其长度就确定了
  - 数组中的多个数据紧密排列，有序，可重复
  - 数组一旦初始化完成，其元素一定是规定的类型，不是该类型的元素是无法添加到该数组中
  - 数组的元素既可以是基本数据类型，也可以是引用数据类型

- 弊端

  - 数组一旦初始化，其长度就无法改变
  - 数组中存储的数据是单一的。无法满足无序的，或者不可重复的情景
  - 数组能用的API很少，功能大多都需要自己实现

  - 针对于元素的增删性能差

### Java集合框架体系

- 是只能存放引用数据类型，如果要存放基本数据类型则是存放其包装类，所以就会涉及到自动拆箱和自动装箱

##### Collection

- 存储的是一个一个单独的数据

###### List

- 存储有序的，可重复出现的数据，又称为动态数组
- 具体的实现类
  - ArrayList(主要的实现类)
  - LinkList
  - Vector

###### set

- 存储无序的，不可重复出现的数据
- 具体的实现类
  - HashSet(主要实现类)
  - LinkedHashSet
  - TreeSet

##### Map

- 存储的是一对一对的数据（key--value键值对）

- 具体实现类
  - HashMap(主要实现类)
  - LinkedHashMap
  - TreeMap
  - HashTable
  - Properties

#### Collection接口中的方法测试

##### 常用方法

- add(Object obj)：添加一个元素，因为是Object所以什么引用类型都可以，基本类型就自动装箱

- addAll(Collection coll)：把coll中的所有元素添加

  >
  >
  >对于一个Collection coll也能使用add方法，但这个时候是把整个集合作为一个元素整体添加进去

- clear()：清空，不是简单的size置位0，这样会导致内存泄漏，就是单纯的遍历把每一个都置为null

- isEmpty()：为空则返回true，反之返回false

- size()：返回元素个数

- contains(Object obj)：是否包含obj有则返回true，没有返回false

- containsAll(Collection coll)：集合是否包含coll中的所有元素
- retainAll(Collection coll)：取两个集合的交集

- remove(Object obj)：把集合中的obj元素移除掉
- removeAll(Collection coll)：也就是求调用集合减去coll的剩余部分，也就是差集
- toArray()：把集合变为数组后返回
- iterator()：迭代器遍历集合

###### 集合和数组的转化

- 集合到数组：toArray()
- 数组到集合：Arrays中的静态方法asList()

###### 向Collection中添加元素的要求

- 一定要重写equals()
  - 因为在Collection中的相关方法，(contains() / remove())在使用时会调用元素所在类的equals()

##### 迭代器

- 作用：用于遍历集合中的元素

- 具体步骤

  - 首先获得迭代器的对象

    ```java
    Iterator iterator = coll.iterator();//利用多态返回一个迭代器接口的实现类
    ```

  - 通过迭代器对象调用next() , hasNext()配合使用来遍历集合

    ```java
    @Test
    public void test(){
        Collection collection = new ArrayList();
        collection.add("zfh");
        collection.add("haha");
    
        Iterator iterator = collection.iterator();//一开始指向集合头，是无元素的
        while (iterator.hasNext()){//指针是不动的
            System.out.println(iterator.next());//指针下移之后，返回当前的值
        }
    }
    ```

##### 增强for循环

- 主要用于遍历数组，集合

- 格式

  - for(要遍历的集合元素的类型 	临时遍历 ：要遍历的集合或者数组名){

    ​	通过操作临时变量来进行输出

    }

    ```java
    @Test
    public void test1(){
        Collection collection = new ArrayList();
        collection.add("zfh");
        collection.add("haha");
    
        for(Object obj : collection){//对于集合，底层实现还是通过迭代器
            System.out.println(obj);
        }
    }
    ```

- 两种for循环的对比
  - 普通for循环
    - 是在栈中新建一个变量之后，指向了堆空间的地址，所以在进行修改的时候是实打实的修改了堆空间中的内容
  - 增强型for循环
    - 是在栈中新建一个变量之后，把堆空间中对应的值赋给了栈变量，所以在增强型内部修改的都是临时变量，那么自然不会影响堆空间原本的值，所以增强型仅仅是用于实现遍历

##### List接口

- 由于List是有序的，可重复的单个数据，所以就会增加一些通过索引完成的操作

- 新增的方法

  - set(int index , Object obj)：修改指定未知的元素
  - get(int index)：获取指定下标的元素
  - add(int index , Object obj)：在指定下标插入元素
  - addAll(int index , Object obj)：在指定位置插入多个元素，也就是插入一个结合集合

  - List subList(int begin , int end)：获得一个左闭右开区间的子集合
  - int indexOf(Object obj)：获得obj首次出现时的索引
  - int lastIndexOf(Object obj)：获得obj最后一次出现时的索引

###### List中不同实现类的区别

- ArrayList：List的主要实现类，是线程不安全的，效率高，底层使用Object [] 数组存储

- LinkedList：底层使用双向链表的方式进行存储

- Vector：List最古老的实现类，线程安全的，效率低，底层使用Object [] 数组存储

  >
  >
  >即使ArrayList是线程不安全的，也不会去使用Vector，通常我们都是自己将ArrayList实现为线程安全的，或者直接调用Collections工具类将其变为线程安全的

##### Set接口

- 用于存储无序的，不可重复的单个数据
- 对于Set是没有新增方法的，List新增方法是因为有序有了索引，所以才增加了和索引有关的方法
- 对于无序性和不可重复性的理解
  - 无序性：
    - ！= 随机性：不是说每一次的输出都是不一样的，随机的，每一次的遍历都是固定的
    - 也不是说遍历的顺序和输出的顺序一定不一样，LinkHashSet就是输入和输出顺序一样，而其作为Set的实现类，一定是满足无序性的
    - 无序性是说其存储位置根据Hash算法来确定，而不是像ArrayList一样，一个一个有序的排列
  - 不可重复性
    - 添加Set中的元素是不同的，通过判断hashCode()得到的哈希值和equals()得到的结果，哈希值相同并且返回true才说明两者真的是同样的元素，所以当使用自定义类的时候一定要重写equals()

###### Set中不同实现类的区别

- HashSet：底层实现是HashMap，即使用数组+单向链表+红黑树进行存储
- LinkHashSet：在HashSet的基础上在添加了一个双向链表，可以按照添加的属性来进行遍历，方便频繁的查询
- TreeSet：底层使用红黑树进行存储，可以按照添加元素指定的属性的大小进行遍历

>
>
>因为TreeSet会比较大小，并且所有集合都是只能放引用数据类型，所以肯定就会要用到两种比较器接口，肯定需要同类才能比较大小，所以TreeSet是只能放同类对象的，但其余两个就不会有这样的限制

#### Map不同实现类的对比

- HashMap：主要实现类，线程不安全的，效率高，可以添加null的key和value值，底层实现是数组+单向链表+红黑树	

  - LinkedHashMap：是HashMap的子类，在其数据结构的基础上增加了双向链表，那么就可以在输出的时候按输入的顺序遍历

- HashTable：古老实现类，线程安全的，效率低，不能添加null的key和value值，底层实现是数组+单向链表

  - Properties：其Key和Value都是String，常用于处理属性文件

- TreeMap：底层使用红黑树进行存储，可以按照添加的键值对中key元素指定的属性的大小进行遍历

  >
  >
  >Map中的Key就相当于是一个Set，所以肯定不能有相同的Key，而Value就相当于是一个Collection，是无序存放，但是又是可以重复的，所以既不是Set也不是List，只能笼统的说是Collection，对于整个键值对就构成了一个entrySet

#### Map中的常用方法

- 增

  - put(Object key , Object value)
  - putAll(Map m)

- 删 

  - Object remove(Object key)

- 改

  >
  >
  >由于Map是根据key值来定位value，并且一个key对应一个value，所以在改操作的时候直接复用增中的put()方法来覆盖掉原来的value即可

- 查
  - Object get(Object key)
- 长度
  - size()
- 遍历
  - 遍历key：Set keySet()
  - 遍历value：Collection values()
  - 遍历entry：Set entrySet()

##### Properties

- 作为HashTable的一个子类，常常用于编写配置文件，其key和value都一定是String类型
- 为什么要使用配置文件
  - 当我们在使用一些例如用户名，密码这样的数据时，如果我们将其定义在代码中，则会导致数据和代码的耦合度过高，那么如果我们想要修改数据的时候其实就是在修改代码，那么我们就得重写编译，但如果我们将其写入配置文件中，配置位置从始至终都是txt文件，所以在修改配置文件之后程序不需要重新编译就可以直接运行，这样就降低了数据和代码的耦合度

### Collections工具类

- 是操作List，Set，Map等集合的工具类

- 区分Collection和Collections

  - Collection：集合框架中用于存储一个一个元素的接口，其中又有List和Set等子接口
  - Collections：用于操作集合框架的工具类

- 常用方法（工具类肯定都是静态方法）

  - 排序操作
    - reverse(List)：翻转List中元素的顺序
    - shuffle(List)：将List中的元素随机排序
    - sort(List)：自然排序 
    - sort(List,Comparator)：定制排序
    - swap(List,int ,int)：将List中指定的两个索引的元素交换

  - 查找操作

    - Object max(Collection)：自然排序后返回最大的元素
    - Object max(Collection,Comparator)：定制排序后返回最大的元素
    - Object min(Collection)
    - Object min(Collection,Comparator)
    - int binarySearch(List list , T key)：在list中查找key，由于是二分法所以原list必须有序
    - int binarySearch(List list , T key ，Comparator c)
    - int frequency(Collection c , Object o)：返回集合中o出现的次数 

  - 复制和替换

    - void copy(List dest , List src)：将src中的内容复制到dest中

      ```java
      @Test
          public void test2(){
              List src = Arrays.asList(1,2,3,4,5);
              /**
               * 错误写法：
               * 由于copy()要求dest.size()要大于scr.size()
               * 而new的ArrayList的size是0，记住这里可不是容量而是实打实的size
               * 所以抛出异常Source does not fit in dest表示size不足
               */
      //        List dest = new ArrayList<>();
      //        Collections.copy(dest,src);
      
              /**
               * 正确写法
               */
              List dest = Arrays.asList(new Object[src.size()]);
              Collections.copy(dest,src);
              System.out.println(dest);//[1, 2, 3, 4, 5]
          }
      ```

    - Boolean replaceAll(Collection c , Object old , Object new)

    - unmodifiablexxx()：返回视图(只能读不能写)

  - 同步

    - Collection synchronizedxxx()：返回xxx的同步后的集合，也就是之前为什么即使在有同步的线程安全需求的时候我们仍然会用ArrayList的原因

### 面试例题

- Collection

  - List，Set，Map是否都继承Collection

  - List，Set，Map三者区别

  - List，Set，Map的实现类并说说特点

  - 常见集合类的区别和适用场景

  - 集合的父类是？哪些是安全的？

  - 变量集合的方式
    - 迭代器，但其是只能用于Collection，不能用于Map，而在Map中虽然也用到了迭代器，但其实是对于entrySet使用，这个其本质是一个Set自然可以用迭代器
    - 增强for循环：底层实现仍然是迭代器
    - 一般for循环：循环List

- List
  - List的实现类
  - ArrayList和LinkedList区别
  - ArrayList和Vector的区别？为什么要用ArrayList代替Vector？
    - Vector的效率很低 
  - 常用方法
  - ArrayList是有序还是无序的？为什么
    - 有序的，底层用数组实现
- Set
  - 有哪些实现类，分别的特点
  - List和Set的区别
  - Set中的元素不能重复使用“==”还是equals()区分？
    - hashCode()和equals()共同使用
  - TreeSet两种排序方式在使用时候起什么作用
    - 通过自然排序或者定制排序来看在插入元素的时候是在左子树还是右子树
  - TreeSet的数据结构
    - 红黑树
- Map
  - Map的类型有哪些
  - final修饰Map后能继续添加数据吗
    - 可以，只是Map的地址不能变了
  - Set和Map的比较
    - HashSet的底层是HashMap
    - LinkedSet的底层是LinkedHashMap
    - TreeSet的底层是TreeMap
  - HashMap线程安全吗
    - 不安全
  - HashMap和Hashtable的区别
  - Hashtable的实现，为什么是线程安全的
    - 数组+单向链表，方法都有synchronized修饰
  - HashMap和LinkedHashMap的区别
    - 后者加了个双向链表
  - HashMap和TreeMap的区别
  - HashMap中实际装的是什么
    - Node，其属性是key和value
    - entry（JDK7之前）
  - 自定义类型可以作为key吗
    - 可以，但是要重写hashCode()和equals()

## 泛型

- 简单来说也就是用于限制容器中的类型 ，用"<>"表示

  - 常常一个集合中放的元素都是同一个类型

    ```java
    List list1 = new ArrayList<>();//add()参数为Object，所以就可能导致类型不一致
    List<Integer> list2 = new ArrayList<>();//参数只能是Integer则保持一致
    ```

- 使用说明
  - 集合框架在声明接口和其实现类时，没有使用泛型则默认为Object类型，如果使用了泛型，则必须指明泛型的具体类型，到底是String，还是Integer等

### 在比较器中使用泛型

- 自定义类型

```java
public class Student implements Comparable<Student>{
    private String name;
    private int age;
    private MyDate date;

    public Student(String name, int age, MyDate date) {
        this.name = name;
        this.age = age;
        this.date = date;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public MyDate getDate() {
        return date;
    }

    public void setDate(MyDate date) {
        this.date = date;
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", date=" + date +
                '}';
    }

	//
    @Override
    public int compareTo(Student o) {
        return this.name.compareTo(o.name);
    }
}
class MyDate{
    private int year;
    private int month;
    private int day;

    public MyDate(int year, int month, int day) {
        this.year = year;
        this.month = month;
        this.day = day;
    }

    public int getYear() {
        return year;
    }

    public void setYear(int year) {
        this.year = year;
    }

    public int getMonth() {
        return month;
    }

    public void setMonth(int month) {
        this.month = month;
    }

    public int getDay() {
        return day;
    }

    public void setDay(int day) {
        this.day = day;
    }
    @Override
    public String toString() {
        return "MyDate{" +
                "year=" + year +
                ", month=" + month +
                ", day=" + day +
                '}';
    }
}
```

- 自然排序

  ```java
  @Override
  public int compareTo(Student o) {
      return this.name.compareTo(o.name);
  }
  ```

- 定制排序

  ```java
  Comparator<Student> comparator = new Comparator<Student>() {
      @Override
      public int compare(Student o1, Student o2) {
          if(o1.getDate().getYear() != o2.getDate().getYear())
              return o1.getDate().getYear() - o2.getDate().getYear();
          else{
              if(o1.getDate().getMonth() != o2.getDate().getMonth())
                  return o1.getDate().getMonth() - o2.getDate().getMonth();
              else return o1.getDate().getDay() - o2.getDate().getDay();
          }
      }
  };
  ```

- 测试类

  ```java
  //自然排序
  @Test
  public void test(){
      TreeSet<Student> set = new TreeSet<>();
      Student student1 = new Student("zfh",20,new MyDate(2002,2,2));
      Student student2 = new Student("zcb",21,new MyDate(2001,10,29));
      Student student3 = new Student("chr",22,new MyDate(2000,3,5));
      set.add(student1);
      set.add(student2);
      set.add(student3);
  
      for(Student s : set){
          System.out.println(s);
      }
      /**
       * Student{name='chr', age=22, date=MyDate{year=2000, month=3, day=5}}
       * Student{name='zcb', age=21, date=MyDate{year=2001, month=10, day=29}}
       * Student{name='zfh', age=20, date=MyDate{year=2002, month=2, day=2}}
       */
  }
  //定制排序
  @Test
  public void test1(){
      Comparator<Student> comparator = new Comparator<Student>() {
          @Override
          public int compare(Student o1, Student o2) {
              if(o1.getDate().getYear() != o2.getDate().getYear())
                  return o1.getDate().getYear() - o2.getDate().getYear();
              else{
                  if(o1.getDate().getMonth() != o2.getDate().getMonth())
                      return o1.getDate().getMonth() - o2.getDate().getMonth();
                  else return o1.getDate().getDay() - o2.getDate().getDay();
              }
          }
      };
      TreeSet<Student> set = new TreeSet<>(comparator);
      Student student1 = new Student("zfh",20,new MyDate(2002,2,2));
      Student student2 = new Student("zcb",21,new MyDate(2001,10,29));
      Student student3 = new Student("chr",19,new MyDate(2003,3,5));
      set.add(student1);
      set.add(student2);
      set.add(student3);
      for(Student s : set){
          System.out.println(s);
      }
      /**
       * Student{name='zcb', age=21, date=MyDate{year=2001, month=10, day=29}}
       * Student{name='zfh', age=20, date=MyDate{year=2002, month=2, day=2}}
       * Student{name='chr', age=19, date=MyDate{year=2003, month=3, day=5}}
       */
  }
  ```

>
>
>在上述例子中使用TreeSet，对其在进行定制排序的时候需要传入Comparator对象，但如何传入？首先由于泛型的约束导致不能将其作为参数传入，但也不能将其作为泛型内容定义，而是应该在Tree创建过程中作为参数传入实现类中

- 对于TreeSet的补充

  ```java
  //错误做法1
  TreeSet<Student> set = new TreeSet<>();
  Student student1 = new Student("zfh",20,new MyDate(2002,2,2));
  set.add(student1,comparator);
  
  //错误做法2
  TreeSet<Student，Comparator> set = new TreeSet<>();
  Student student1 = new Student("zfh",20,new MyDate(2002,2,2));
  set.add(student1,comparator);
  
  //正确做法
  TreeSet<Student> set = new TreeSet<>(comparator);
  Student student1 = new Student("zfh",20,new MyDate(2002,2,2));
  set.add(student1);
  ```

## 集合的源码解析

### List

#### ArrayList

- JDK7

  - 一开始底层会初始化数组，数组长度为10

    ```java
    Object[] elementData = new Object[10];
    ```

    

  - 当要添加第十一个元素的时候，底层发现数组满了，则需要扩容，默认扩容为原长度的1.5倍，并将原数组中的元素添加到新数组

- JDK8

  - 一开始底层会初始化数组，但不会指定数组长度

    ```java
    Object[] elementData = new Object[]{};
    ```

  - 当插入第一个元素的时候，再给数组初始化长度

    ```java
    Object[] elementData = new Object[10];
    ```

  - 当要添加第十一个元素的时候，底层发现数组满了，则需要扩容，默认扩容为原长度的1.5倍，并将原数组中的元素添加到新数组

  >
  >
  >JDK7和JDK8是一个分水岭，在JDK7的最新版本中很多方式已经和JDK8比较相似，所以也可能在最新的小版本中出现在最开始的也没有初始化了长度的情况

#### Vector

- 和JDK7中的ArrayList的实现几乎一模一样，只不过其是线程安全的，并且扩容的时候是两倍扩容

  >
  >
  >之所以不提Vector的JDK版本是因为其基本在开发中都不会使用了，所以在JDK8中也就没有对其进行改进

#### LinkedList

- 内部声明

	```java
	private static class Node<E>{
		E item;
		Node<E> next;
		Node<E> prev;
	}
	```



- 对于LinkedList的声明其实没有干什么实际的事情，当添加元素的时候，先将该元素封装成一个Node结点，然后在将其添加到双向链表中去，比较特殊的是添加首元素的时候，其没有next和prev都是null

### Map

#### HashMap

- JDK7中：底层实现是数组+单向链表实现

  - 在创建Map对象过程中

    ``` java
    HashMap<String,Integer> map = new HashMap<>();
    //其底层会声明如下数组
    Entry[] table = new Entry[16];
    ```

    >
    >
    >对于Entry是将键值对（key，value）封装成了一个Entry对象，并且将这个对象添加到table数组中

  - 具体的添加/修改过程（因为都同用put()）

    将（key1,value1)添加到map中的过程

    - 首先调用key1中的hashCode()计算key1的哈希值1，并将该哈希值1传入hash()中得到哈希值2，再将哈希值2通过indexFor()计算其下标索引值，即确定该键值对在table数组中下标位置i

    - 如果table[i]没有元素，则将(key1,value1)添加到table[i]

    - 如果table[i]有元素(key2,value2)，则继续比较key1,key2的哈希值2-->哈希冲突

      - 如果哈希值2不同，证明这是两个不同的键值对，只是经过经过indexFor()的计算之后正好下标相同，那么将(key1,value1)添加到table[i]之后以单向链表的方式指向(key2,value2)，则添加成功

      - 如果哈希值2相同，则继续比较key1,key2的equals()，调用key1所在类的equals()，把key2作为参数传入

        >
        >
        >因为map中的key是唯一存在的，所以当哈希值2相同的时候，我们需要判断这两个key是真的相同，还是说在计算哈希值的时候恰巧两者结果是一样的，但其实是不同的key

        - 若返回false，则两者不同，把(key1,value1)添加到table[i]中，并且同样用以单向链表的方式新值指向旧值
        - 若返回true，则两者真的相同，那么就用value1来覆盖value2的值，也就是修改操作

    ![image-20230415144210471](image\image-20230415144210471.png)

  - 扩容

    - (size > threshold) && (null != table[i])

      - threshold = 数组的长度 * 加载因子
        - 加载因子是自己设定的，用于控制数组的散列程度，太小则会太散形成浪费，太大则会链表过长，查找的效率又降低，默认为0.75

    - 满足之后进行扩容，默认扩容为原来的2倍大小

      >
      >
      >当添加的元素个数size大于设置的临界值就会考虑扩容，以最开始为例，默认的临界值是12，不是说当加入第13个元素的时候就一定会扩容，而是会判断在加入第13的元素时如果table[i]正好是null，那么我们就先不扩容，因为不会导致链表变长，也就是说不会影响效率。如果在添加第13个元素的时候table[i] != null，也就是说如果不扩容就会增长链表，那么这个时候就需要扩容为原来的2倍了

- ==JDK8==

  - 初始化数组的位置不同
    - 在声明HashMap实例的时候没有立即初始化table数组，而是仅仅进行声明，当第一次添加元素的时候进行判断，发现table没有初始化，那么在这个时候才对table进行初始化
  - 用于存储键值对的类型由Entry类型变为了Node类型，也就是说table[]类型变为了Node

  - 新元素的位置不同
    - 在JDK7中是新元素添加到table[i]中，并指向旧元素（头插法）
    - 在JDK8中是旧元素仍然在table[i]中，然后指向新元素（尾插法）

  - 底层结构不同

    - JDK7中：数组+单向链表

    - JDK8中：数组+单向链表+红黑树

      - 当table[i]上的链表元素个数达到8，并且数组长度超过64时，这时会把索引i位置上的单向链表改为红黑树进行存储

      - 当table[i]上的链表元素个数小于6之后，红黑树又将退化为单向链表

        >
        >
        >因为如果是单向链表过长的话查找的效率是很慢的，但如果用红黑树进行查询，由于红黑树是一种二叉排序树每次都能剔除一半的元素，就会类似于二分查找，相率就能够更好。
        >
        >为什么不一来就直接使用红黑树，而是红黑树和单链表进行转化的原因？
        >
        >当数据量少的时候两者的查询效率相当，但是红黑树所需的存储空间相当于单链表的2倍

  ![image-20230415150748755](image\image-20230415150748755.png)

#### LinkedHashMap、HashSet

- LinkedHashMap
  - 作为HashMap的子类，在HashMap的基础之上再添加了双向链表  ，用于记录(key,value)添加的先后顺序，便于我们便利所有的(key,value)

- HashSet
  - 对应的不同Set底层的实现都是对应的Map

### 面试例题

#### List

- ArrayList的默认大小以及扩容机制
  - 10，当插入第11个的时候扩容为1.5倍
- ArrayList的底层实现 

- ArrayList中remove后面的元素怎么办
  - 依次前移
- ArrayList在JDK7和JDK8中的区别
- 数组和ArrayList的区别
- 什么是线程安全的List？
  - Vector：线程安全的
  - ArrayList：线程不安全，但是常常用工具类Collections包装为同步的，或者手动实现

#### Map

- HashMap的底层实现
- HashMao初始值16，临界值12怎么算出
  - 数组长度 * 加载因子（默认为0.75）
- HashMap长度为什么是2的幂次方
  - 方便计算添加元素的索引
- HashMap怎么计算哈希值和索引？扩容机制以及怎么处理哈希冲突？
- HashMap的底层为什么要加入链表，以及达到一定长度后为什么要转化为红黑树
  - 解决哈希冲突
  - 红黑树是二叉排序树，在进行查找的时候效率高O(logn)
- 红黑树和单向链表的相互转换
- hashCode()和equals()怎么重写
  - 参与equals()计算的属性，通常也会参与hashCode()的计算，来尽量保持两者的一致性

- equals()和==的区别，equals()相等则hash值一般都相等

#### Set

- HashSet存放数据的方式
  - 底层实现使用HashMao
- 如何保证唯一性
  - 比较哈希值和equals()
- 用哪两种方式实现集合的排序
  - 两种比较器
    - 自然排序：Comparable
    - 定制排序：Comparator



## File类与IO流

### File

- 概述

  - File类位于java.io包下
  - File类的一个对象就是操作系统下的一个文件或者一个文件夹（与是什么操作系统无关）

- 文件目录

  - 绝对路径

    - 以windows为例，包含盘符在内的文件或者文件目录的完整路径

      如：d：\haha\hello.txt

      或者d：/haha/hello.txt

      >
      >
      >可以用"\ "或者“/ ”来表示一级目录结构，但是由于java中用“ \ ”来充当转义字符所以在使用时为” \ \ "表示

  - 相对路径

    - 相对于某个文件目录来说的相对位置
      - 在单元测试方法中：相对于当前的module来说
      - 在main方法中：相对于当前的project来说

- 内部API的声明

  - 构造器

    - public File (String pathname)：以pathname为路径创建一个File对象，可以是绝对路径也可以是相对路径

    - public File (String parent , String child)：以parent为父路径，child为子路径创建一个File对象

    - Public File (File parent , String child)：以File对象的parent为父路径，child为子路径创建一个File对象

      ```java
      @Test
      public void test(){
          //public File (String pathname)
          File file1 = new File("d:\\javaFileTest\\hello.txt");
          File file2 = new File("hello.txt");
      
          //public File (String parent , String child)
          File file3 = new File("d:\\javaFileTest","hello.txt");
      
          //Public File (File parent , String child)
          File file4 = new File("d:\\javaFileTest");
          File file5 = new File(file4,"hello.txt");
      }
      ```

      >
      >
      >对于第二种和第三种构造器其实本质上是一样的，都是通过一个父路径创建一个子路径，两者只是传入的参数不同，一个传入的是String，一个传入的是File对象
      >
      >即使当文件路径有问题，在创建File对象的时候也不会报错，只是会在对该对象进行具体操作的时候有问题

  - ​	常用的方法

    - 获取文件信息
      - String getName()：获取文件名
      - String getPath()：获取文件路径
      - String getAbsolutionPath()：获取文件绝对路径
      - File getAbsolutionFile()：获取绝对路径所表示的文件
      - String getParent()：获取上层文件目录的路径，如果没有则返回null
      - long length()：获取文件长度，即字节数，但是不能获取文件目录的长度
      - long lastModified()：获取文件最后一次修改的时间，是毫秒值
    - 列出当前目录的下一级
      - String[] list()：返回一个String数组，表示该File目录下的所有子文件，或者子文件目录
      - File[] listFiles()：返回一个File数组，表示该File目录下的所有子文件，或者子文件目录

    - 文件重命名

      - Boolean renameTo(File dest)

        >
        >
        >file1.renameTo(file2)
        >
        >如果想返回true则必须保证：file1存在file2不存在，且file2所在文件的目录也要存在

    - 判断类方法
      - boolean exist()：文件是否存在
      - boolean isDirectory()：是否是一个文件目录
      - boolean isFile()：是否是一个文件
      - boolean canRead()：是否可读
      - boolean canWrite()：是否可写
      - boolean isHidden() ：是否隐藏

    - 文件的创建和删除

      - boolean createNewFile()：创建文件，若文件已经创建则返回一个false

      - boolean mkdir()：创建一个文件目录，如果该目录已经存在则返回false，若上层目录不存在也返回false

      - boolean mkdirs()：创建一个文件目录，如果已经存在则返回false，若无上层目录则一并创建

      - boolean delete()：删除一个文件或者文件夹

        >
        >
        >在java中删除的文件是不会进入回收站的，也就是说一旦删除就真的没了
        >
        >当删除一个文件目录的时候，需要保证其是一个空的文件目录才能删除

- 例题：计算某文件目录下占用的字节数

  ```java
  @Test
  public void test1(){
      File file = new File("d:\\leetCode");
      System.out.println(getLenth(file));//235955字节
  
  }
  public long getLenth(File file){
      long size = 0;
      if (file.isFile())
          size += file.length();
      else{
          File[] file1 = file.listFiles();
          for(File f : file1)
              size += getLenth(f);
      }
      return size;
  }
  ```

### IO流

#### IO流的分类

- 按照流向不同来划分（都是站在程序的角度来说的）
  - input输入流：读取外部数据（磁盘，光盘等）到程序（内存）中。
  - output输出流：反之

- 按操作数据的单位来划分

  - 字节流：以字节为基本单位，读写数据的流
    - 以InputStream和OutputStream结尾
  - 字符流：以字符为基本单位，读写数据的流
    - 以Reader，Writer结尾

- 按IO流的角色划分

  - 节点流：直接从数据源连接到目的地来读写数据数据

    ![image-20230416144428711](image\image-20230416144428711.png)

  - 处理流：不直接连接到数据源或目的地，而是连接到已经存在的流上（节点流和处理流都可），通过对数据的处理来为程序提供更强大的读写功能

    ![image-20230416144448275](image\image-20230416144448275.png)

#### 读取写出文本数据

- 具体步骤
  - 创建File对象，绑定我们需要操作的文本文件hello.txt
  - 创建输入型字符流，用于读取数据
  - 读取数据显示到控制台
  - 流对象的关闭，否则会引发内存泄漏

## 网络编程

### 软件的架构

- C/S架构：指客户端和服务端的架构。比如通过qq，美团APP，360安全卫士等来访问

  ![image-20230416155402573](image\image-20230416155402573.png)

- B/S架构：指浏览器和服务端的架构。通过浏览器输入一个网址来获取服务

  ![image-20230416155449248](image\image-20230416155449248.png)

>
>
>两者各有利弊，对于C/S架构会稳定且体验好，而不同的浏览器可能会有不兼容的问题，但APP总是会需要升级更新，不然可能导致有的功能无法实现

### 实现网络通信需要解决的问题

- 问题
  - 如何准确的定位网络上的一台或者多台主机
  - 找到主机后如何定位主机上的特定应用
  - 找到主机后如何进行可靠地，高效的数据传输
- 实现网络传输的三要素
  - 使用IP地址：用于准确定位到网络上的主机
  - 使用端口号：用于定位到主机上的特定应用
  - 使用网络传输协议：进行可靠，高效的数据传输

### 网络三要素（讲解可以见计网笔记）
#### IP

- IP地址用于给网络中的一台计算机作唯一的编号
- 本地回路地址：127.0.0.1

##### IP地址的分类

- 方式一
  - IPv4：占用4个字节
  - IPv6：占用16个字节
- 方式二
  - 公网地址（万维网使用）
  - 私有地址（局域网使用）：192.168开头

##### 域名

- 由于IP地址是不便于记忆的，所以我们通过域名的方式使域名和IP地址一一对应来访问IP地址

  如：www.baidu.com等

- 域名解析：那么我们怎么知道域名所对应的IP地址是多少呢？就靠的是域名解析
  - 通过DNS将域名转化为IP地址，再访问该IP地址就能建立连接获取资源
  - 在每一次记DNS解析之后都会把该映射关系记录在本地文件中，所以其实是首先找本地映射文件，如果其中没有才会通过DNS服务器去解析

 #### 端口号

- 可以唯一标识主机中的进程，也就是应用程序

- 不同的进程会分配不同的端口号

- 端口号的范围：0~65535

  - 公认端口：0-1023，已经被服务通信预先定义了

    - HTTP:80
    - FTP:21

  - 注册端口：1024-49151，分配给用户进程或者应用程序

    - Tomcat：8080
    - MySQL：3036

  - 动态/私有端口：49152-65535

    >
    >
    >如果端口号被另一个应用所占用，会导致当前程序启动失败

#### InetAddress类的使用

- 作用

  - 每一个实例化的对象就对应一个IP地址

- 实例化方式：

  - InetAddress getByName(String host)：传入指定域名或者IP地址返回与之绑定的实例对象

  - InetAddress getLocalHost()：获取本机的IP地址对应的实例对象 

    >
    >
    >不是通过new来实例化，而是通过静态方法来返回实例对象

```java
InetAddress inetAddress1 = InetAddress.getByName("192.168.1.1");
InetAddress inetAddress2 = InetAddress.getByName("www.baidu.com");
System.out.println(inetAddress1);//    /192.168.1.1
System.out.println(inetAddress2);//    www.baidu.com/110.242.68.4

InetAddress inetAddress3 = InetAddress.getLocalHost();
System.out.println(inetAddress3);//    LAPTOP-VB926321/10.198.161.111
```

- 常用方法
  - byte[] getHostName()：获取当前对象的域名
  - byte[] getHostAddress()：获取当前对象的ip地址
