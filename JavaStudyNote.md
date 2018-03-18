# JavaStudyNote
- [记录一下，学习的过程 ] 
- ## 结构和简单名词的分析
 ### 主函数结构分析
 ```java
 public static void main(String[] args)
   主函数：是一个特殊的函数，作为程序的入口，可以被JVM调用
   主函数的定义：
   public：代表着主函数的访问权限是最大的。
   static:代表主函数随着类的加载已经存在了
   void:主函数没有具体的返回值
   main：不是关键字
   String[] arr：函数的参数，参数类型是一个数组，该数组类型是一个数组，该数组中的元  
   素是字符串，字符串类型的数组
   主函数的固定格式，能被JVM识别。
 ```
 ### private关键字分析
 ```java
 private ：私有，权限修饰符：用于修饰类中的成员（成员变量，成员函数）
           私有只在本类中有效
 将AGE私有化以后再类意外即使建立了对象也不能直接访问
 但是人应该有年龄，就需要在Person类中提供对应访问age的方式
 注意：私有仅仅是封装的一种表现形式
 之所以对外提供访问方式，就是因为可以再访问方式中加入逻辑
 判断等语句对访问的数据进行操作,提高代码的健壮性
 ```
 ### 继承概念
 ```java
 继承的使用：
 1. 提高的代码的复用性
 2. 让类与类之间产生了关系。有了这个关系，才有了多态的特性
 //注意：千万不要把为了获取其他类的功能，简化代码而继承，
 //必须是类与类之间有所属的关系才可以继承，要产生类于类之间的关系
 3. 子类所有的构造函数默认都会访问父类中空参数的构造函数
 因为子类每一个构造函数的第一行都有一个隐式的Super();
 
 >Java语言中:简单来说只支持单继承，不支持多继承。
 >多继承容易带来安全隐患:当多个父类中定义了相同功能，但功能内容不同是不确定要运行哪一个
 >但是java保留了这种机制，并用另一种体现形式来完成表示。
 
 
 >Java多实现：
 1.Java支持多层继承，也就是一个继承体系，如何使用一个继承体系中功能？
 想要使用体系，先查阅体系中父类的描述，因为父类中定义的功能是该体系的共性功能只要了解
 这个类中的共性功能就可以基本使用这个类的体系了，但是在具体调用时候，要创建最子类  
 对象因为父类有可能不能创建对象，如抽象对象。
 
 class a{
   void show()
   {
     System.out.println("a");
   }
 }
 class b{
   void show()
   {
    System.out.println("b");
   }
 }
 class C extends a,b{
   void show()
   {
     System.out.println("a");
   }
 }
 C .c=new C();
 c.show();
 子父类出现后，类成员的特点：
 类中成员：
 1. 变量
 2. 函数
 3. 构造函数
 
 1. 变量：this 代表的是子类对象的应用，super 代表的是父类对象的应用
 2. 函数：“覆盖” = 重写  
   当子类继承父类，沿袭了父类的功能，到子类中，但是功能不同时候用覆盖方法。
 记住：
    重载：只看同名函数的参数列表
    重写：子父类情况要一模一样。
 class Fu
 {
   int num = 4;
 }
 class zi extends Fu
 {
   int num = 5;
   void show()
   {
     System.out.println(num);
   }
 }
 public static void main(String[] args) {
   Zi .z = new Zi();
   z.show();  
 }
```
### final关键字
 ```java
 final关键字
 作为一个修饰符。
 1. 可以修饰类，函数，变量
 2. 被 final 修饰的类不能被继承
 3. 被 final 修饰的方法不可被复写
 4. 被 final 修饰的变量是一个常量只能被赋值一次。
 ```
### 抽象类
 ```java
 抽象类(abstract)：
 1. 抽象方法一定在抽象类中
 2. 抽象方法和抽象类都必须被abstract关键字修饰
 3. 抽象类不可以用 new 创建对象，因为调用抽象方法没有意义  
 4. 抽象类中的方法要被使用，必须由子类复写所有的抽象方法后嗲气用，建立子类对象的调用
     如果子类只覆盖部分抽象方法，那么该子类还是抽象类  
 ```
### 接口
 ```java
 接口（ interface ）:
 接口定义：
 1. 接口中常见定义，常量，抽象方法
 2. 接口中的成员都有固定修饰符
     常量：public static final
     方法: public abstract
 3. 接口是不可以创建对象的，因为有抽象方法。
  需要被子类实现，子类对接口中的抽象方法全部覆盖后，子类才可以实例化。
接口可以被类多实现，也是对多继承不支持的转化形式，java支持多实现。
    >一个类在继承一个类的同时还可以多实现接口
 接口的特点：
 1. 接口是对外暴露的规则
 2. 接口是程序功能的扩展
 3. 接口可以用来多实现
 4. 接口与类之间是实现关系，而且类可以继承一个类的同时实现多个接口
 5. 接口于接口之间也可以有继承关系
  ```
### 多态
  ```java
 多态：可以理解为事物存在的多种体现形态
 关键对于向上转型和向下转型的理解
 人：男人，女人；
 动物：猫，狗
 猫 x =  new 猫;
 动物 x = new 猫；
 1.多态的基本体现
     父类的引用指向了自己的子类对象
     父类的应用也可以接受自己的子类对象
 2.多态的前提
     必须是类与类之间有关系，要么是继承，要么实现
 3.多态的好处
      多态的出现大大提高了程序的扩展性
 4.多态的弊端
     提高了扩展性，但是智能使用父类的引用访问父类中的成员
 4.多态的应用
 Abstract class Animal
 {
   abstract void eat();
 }
 Class Cat extends Animal
 {
   public void eat()
   {
     System.out.println("吃鱼");
   }
   public void catchMouse()
   {
     System.out.println("抓老鼠")
   }
 }
 Class Dog extends Animal
 {
   public void eat{
    System.out.println("吃骨头");
  }
   public void KanJia(){
     System.out.println("看家");
   }
 }
 Class Pig extends Animal
 {
   public void eat()
   {
     System.out.prinln("饲料")
   }
   publci void gongdi()
   {
     System.out.prinln("供地")
   }
 }
 Class DuoTaiDemo
{
   public static void main(String[] args) {
     System.out.println("Hello World");
     Cat c = new Cat;
     c.eat();
     Cat c1 = new Cat();
     c1.eat;
   }
   public static void function(Animal a)
   {
     a.eat();
   }
 /*  public static void function(Cat c)
   {
     c.eat;
   }
   public static void function(Dog d)
   {
     d.eat;
   }public static void function(Pig p)
 {
      p.eat;
   }
 }*/
 class DuoTaiDemo2
 {
    public static void main(String[] args) {
      Animal a = new Cat();//类型提升，向上转型
      a.eat();
      //如果想要调用猫的特有方法时候，如何操作？
      //强制将父类应用，转成子类类型,向下转型，
      //不可将父类对象转化成子类对象
     //能转化的是父类应用指向了自己子类对象时候，该应用可以被提
    //升，也可以被强制转化
     // Animal a= new Animal();
     //Cat c = (Cat)a;
      Cat c = (Cat)a;
      c.catchMouse();
     }
 }
 ```
## 特有结构分析
### 异常
 ```java
 1.异常由来：问题也是现实生活中的一个具体的事物，也可以通过java类的形式进行描述，并封装成对象
          其实就是java对不正常情况进行描述后的对象体现
 对于问题的划分为严重问题和非严重问题
 对于严重的，java通过error类进行描述
       对于Error一般不编写针对性的代码进行处理
 对于非严重，java通过Exception类进行描述
      对于Exception可以使用针对性的处理方式进行处理
 2.异常处理：java 提供了特有的语句进行处理
 /*try{
   需要被检测的代码
 }
 catch(异常类 变量){
     处理异常代码：(处理方式)
 }finally
 {
   一定会处理的语句；
 }*/
 class Demo
 {
   int div（int a,int b）
         return a/b;
 }
 class ExceptionDemo
 {
   public static void main(String[] args)
   {
     Demo d= new Demo();
     try{
       int x = d.div(4,0);
     System.out.println("x="+ x);
    }catch(Exception e){
       System.out.prinln("除0了 ！");
       System.out.prinln(e.getMessage());//by zero
       System.out.prinln(e.toString());//异常名称：异常信息
     e.printStackTrace();//异常名称和信息以及异常出现的位置
    }
 
       //byte[] arr = new byte[1024*1024*600];
  }
 }
 3.异常抛出
 class Demo
 {
   int div（int a,int b）throws Exception//在功能上通过throws的关键字申明了该功能有可能出现问题
         return a/b;
 }
 class ExceptionDemo
 {
   public static void main(String[] args)//throws Exception
   {
       Demo d= new Demo();
     try{
       int x = d.div(4,0);
       System.out.println("x="+ x);
     }catch(Exception e){
       System.out.prinln("除0了 ！");
       System.out.prinln(e.getMessage());//by zero
       System.out.prinln(e.toString());//异常名称：异常信息
       e.printStackTrace();//异常名称和信息以及异常出现的位置
     }
 }
 4.多异常处理
   申明异常时，建议声明更为具体的异常，这样处理的可以更具体
   对于声明几个异常就对应有几个catch块，不要定义多余的catch类
   如果多个catch块中的异常出现继承关系，父类异常catch放到最下面
 class Demo
 {
   int div（int a,int b）throws ArithmeticException,ArrayIndexOutOfBoundsException//在功能上通过throws的关键字申明了该功能有可能出现问题
         return a/b;
         int[] arr = new int[a];
         System.out.prinln(arr[4]);
 }
 class ExceptionDemo
 {
   public static void main(String[] args)//throws Exception
  {
     Demo d= new Demo();
     try{
       int x = d.div(4,0);
       System.out.println("x="+ x);
     }catch(ArithmeticException e){
       System.out.prinln("除0了 ！");
       System.out.prinln(e.getMessage());//by zero
       System.out.prinln(e.toString());//异常名称：异常信息
      e.printStackTrace();//异常名称和信息以及异常出现的位置
    }catch(ArrayIndexOutOfBoundsException e){
       System.out.prinln(e.toString());
       System.out.prinln("角标越界了！");
     }catch(Exception e){
      System.out.prinln(e.getMessage());
    }
 }
 5.自定义异常
 因为项目中会出现特有的问题
 而这些问题并没有被java所描述并封装对象
 所以对于这些特有的问题可以按照java的封装思想将特有的问题，进行自定义异常封装
 class FuShuException extends Exception
 {
     private String msg;
    FuShuException(String msg)
     {
       this.msg =msg;
     }
     public String getMessage(){
      return msg;
     }
 }
 class Demo
 {
  int div（int a,int b）
         return a/b;
 }
 class ExceptionDemo
{
   public static void main(String[] args)
   {
     Demo d= new Demo();
     try{
       int x = d.div(4,0);
       System.out.println("x="+ x);
     }catch(FuShuException e){
       System.out.prinln("负数了 ！");
       System.out.prinln(e.getMessage());//by zero
       System.out.prinln(e.toString());//异常名称：异常信息
       e.printStackTrace();//异常名称和信息以及异常出现的位置
     }

       //byte[] arr = new byte[1024*1024*600];
   }
 }
 ```
 ### 多线程
 ```java
 进程:是一个正在执行中的程序
       每一个进程执行都有一个执行顺序，该顺序是一个执行路径，或者叫一个控制单元
 线程:就是进程中的一个独立的控制单元
           线程在控制着进程的执行
 一个进程中至少有一个进程
 Java VM : 启动的时候会有一个进程叫 java.exe。
 该进程中至少有一个线程来负责java程序的执行
 而且这个线程运行的代码存在于main方法中
 该线程称之为主线程
 扩展：其实更细节说明jvm，jvm启动不止一个线程，还有负责垃圾回收机制的线程
 
 1.如何在自定义的代码中，自定义一个线程呐？
 通过对api的查找，java已经提供了对线程这类食物的描述，就Thread类
 创建线程的第一种方式：继承Thread类
 步骤：
 1.定义类继承Thread
 2.复写Thread中的Run方法
   目的将自定义的代码存储在RUN方法中，让线程运行
 3.调用线程的Start方法,
 该方法有俩个作用：启动线程，调用run方法
 **重点**创建线程的第二种方法：实现Runadle接口
 步骤：
 1.定义类实现Runnable接口
 2.覆盖Runnable接口中的RUN方法
     将线程要运行的代码放在该run方法中
 3.通过Thread类建立线程对象
 4.将Runnable接口的子类对象作为参数传递给Thread类的构造函数
     为什么要将Runnable接口的子类对象传递给Thread的构造函数
     因为，自定义的run方法，就必须明确该run方法所属对象
 5.调用Thread类的Start方法开启线程并调用Runnable接口子类的run方法
 
 发现运行结果每一次都不同
 因为多线程都能获取CPU的执行权，CPU执行到谁，谁就运行
 明确一点，在摸个时刻，只能有一个程序在运行（多核除外）
 CPU在做着快速的切换，以达到看上去是同时运行的效果
 我们可以形象吧多线程的运行行为在互相抢夺CPU的执行权
 这就是多线程的一个特性，随机性，谁抢到就是谁执行，至于执行多长CPU说了算
 
 为什么要覆盖RUN方法：
 Thread类用于描述线程
 该类就定义了一个功能，用于存储线程要运行的代码，该存储功能就是RUN方法
 class Demo extends Thread
 {
   public void run()
   {
     for (int x=0; x<4000; x++)
     System.out.println("demo run----"+x);
   }
 }
 class ThreadDemo
 {
   public static void main(String[] args) {
    //for (int x=0; x<4000; x++)
     //System.out.println("Hello World!");
     Demo d = new Demo();//创建好一个线程
     d.Start();
     for (int x=0; x<4000; x++)
     System.out.println("Hello World!");
   }
 }
 多线程安全问题：发现，打印出0，-1，-2等错票
 
 多线程的运行出现了安全问题。
 
 *重点*问题的原因：
       当多条语句在操作同一个线程共享数据是，一个线程对多条语句只执行一部分，还没有执行完
       另一个线程参与进来执行
 解决办法：
       对多条操作共享数据的语句，只能让某一时间段让一个线程都执行完，让其他线程不可以参与执行
 java对于多线程的安全问题提供了专业的解决方式
 
 同步代码块：
 synchronized(对象)
 {
   需要被同步的代码（那些语句在操作共享数据那些代码就需要进行同步）
 }
 对象如同锁，持有锁的县城可以在同步中执行
 没有持有锁的线程即便获取了CPU的执行权，也进不去，因为没有获取锁

 
 同步前提：
 1.必须要有俩个或者俩个以上的线程
 2.必须是多个线程使用同一个锁
 
 必须保证同步当中只能有一个线程能运行
 
 好处：解决了多线程的安全问题
 弊端：多个线程都需要判断锁，较为消耗资源
 ```
### 基本数据类型对象包装类
byte Byte
 
 
short short
 
 
int Integer
 
long Long
 
boolean boolean
 
 
 char Character
 
 
 float Float
 

 基本数据类型对象包装类的最常见作用
 就是用于基本数据类型和字符串类型之间做转换
 基本数据类型转成字符串。
 
     基本数据类型+“”
     基本数据类型。toString（基本数据类型值）；
     如：Integer.toString(34);//将34整数变成“34”
 
 字符串转成基本数据类型。
 
   xxx a = xxx.parsexxx（String）;
 
   int a = Integer.paresInt("123");
 
   double b =Double.parseDouble("123");
 
   boolean b = Boolean.parseBoolean("true")
 
 ```java
 class IntegerDemo
 {
   public static void sop(String str )
   {
     System.out.println(str);
   }
   public static void main(String[] args) {
   sop("int max:"+Integer.MAX_VALUE);
   }
 }
 ```
 #### Object类：是所有对象的直接或间接父类，对象中的上帝
 Object类中已经提供了对对象是否相同的比较方法
 如果自定义类中也有比较相同的功能，建立自己特有的比较内容即可，也就是覆盖
 ```java
 Class Demo {
 
 }
 class objectDemo
 {
   public static void main(String[] args)
   {
     Demo d1 = new Demo();
     Demo d2 = new Demo();
     Demo d3 = d1;
     System.out.println(d1.equals(d3));
     System.out.println(d1==d2);
     System.out.println(d1==d3);
   }
 }
 ```
### 集合类
 #### 集合框架
 为什么我会出现这么多的容器？
 
 
 因为每一个容器对数据的存储方式都有不同
 
 
 这个存储方式称之为：数据结构
 ####  Collection
 ```java
 import java.util.*;
 class CollectionDemo
{
  public static void main(String[] args) {
     //创建一个集合容器，使用Collection接口的子类，ArrayList
     ArrayList a1 = new ArrayList();
     //1。添加元素
     a1.add("java01");
     a2.add("java02");
     a3.add("java03");
     a4.add("java04");
     //2.获取个数，集合长度
     sop("size:"+a1.size);
   }
}
 ```
#### Vector
 ```java
 import java.util.*;
 class VectorDemo{
   public static void main(String[] args) {
     Vector v = new Vector();
     v.add("java01");
     v.add("java02");
     v.add("java03");
     v.add("java04");
   }
 }
 ```