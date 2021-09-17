## JAVA - 
- [局部变量和成员变量的区别](#局部变量和成员变量的区别)
- [collection集合集合是java中提供的一种容器可以用来存储多个数据](#collection集合集合是java中提供的一种容器可以用来存储多个数据)

### 局部变量和成员变量的区别
1.定义位置不一样
局部变量：在方法的内部， 
成员变量：在方法外部
2.内存位置不一样
  局部变量位于栈中，而成员变量位于堆中
3.生命周期不一样
  局部变量随着方法进栈而诞生，同理随着出栈而消失  
  成员变量随着对象创建而诞生，随着JVM垃圾回收而消失

### this
谁调用方法谁就是this
例如person.set() 那么this指向的pers
###构造方法
构造方法什么都不用写，不用写其函数类型，不能人return
### super
指向父类的属性或者方法
### 继承方法中的覆盖重写
创建子类对象优先用子类方法，（必须是方法而不能是对象和成员变量）
####注意事项
1.父子类方法相同参数列表同样相同(@override)用这个来检测是否是覆盖重写
2.子类方法的返回值必须小于等于父类（范围方式）比如父返回obj类，子类返回string类 （返回值父大子小）
3.子类方法的权限必须大于等于父类例如子类为protected 那么父类只能选择protected以下的如默认的和private（权限子大父小）
### 应用场景 
继承关系中，父子类构造方法的访问特点  
1.子类构造方法当中有一个默认的``super()``调用，所以一定先调用父类构造  
2.可以通过``super()``关键字来子类调用父类重载构造
3.super的父类构造调用，必须是子类构造方法的第一个语句,不能一个子类构造调用多个super构造  
4.子类必须调用父类的构造放啊，不写贼默认super且必须写在第一个语句有且只有一个
![avatar][base64str]
### 继承特点
1.java中的继承是单继承  
2.java可以多级继承比如父亲有儿子儿子又有儿子  
3.一个子类只能有唯一一个父类，但一个父类可以拥有众多子类   
### 抽象

例如知道正方形，圆形而图形是他们的父类，如何从图形上计算方法就是抽象方法
#### 抽象方法必须在抽象类之中
### 接口
   接口就是一种公共的规范标准，只要符合标准规范，就可以大家通用的。  
   接口就是多个类的公共规范，接口是一种引用数据类型，最重要的内容就是其中的抽象方法   
   ``public interface 接口名称 {
   //接口内容
   }``
java9中包括常量、抽象方法、默认方法、静态方法、私有方法等5个内容
任何版本的Java中都能定义抽象方法，接口中的抽象方法固定式两个关键字 public、abstract，接口不能直接使用必须实现该接口  
格式
`` public class 实现类名称 implement 接口名称
{
    //......
}``
同上文抽象类一样实现类必须覆盖重写（实现）
不能直接new接口只能new实现类
#### 接口默认方法
接口默认方法可以通过实现对象直接调用，同时也可以被覆盖重新
``// public default 返回值类型 方法名称(参数列表){
//     ```方法体```，默认方法可解决接口升级问题
// }``
#### 接口静态方法
静态方法就是将abstract或者default换成static带上方法体即可，不能用过接口实现类的对象来调用接口中的静态方法
#### 私有方法
java9之后可以定义私有方法可定义普通私有或者静态私有  
1.普通私有方法类型
``private 返回值类型 方法名称(参数列表){
    方法体
}``  
2.静态私有方法类型  
``private static 返回值类型 方法名称(参数列表){
    方法体
}``
#### final关键字
不可改变一旦使用final意味着不可修改，接口中的常量必须进行赋值，不能不赋值 
#### 总结
1.成员变量其实是常量，且必须赋值，用大写  
2.接口中最重要的是抽象方法，格式``public abstract 返回值类型 方法名称(参数列表)方法体不写``  
3.允许默认方法格式``public defau 返回值类型 方法名称(参数列表){ 方法体 }``  
4.允许定义静态方法 格式如上将 default 换成 static即可  
5.允许定义私有方法 普通私有方法类型  
``private 返回值类型 方法名称(参数列表){
    方法体
}``  
静态私有方法类型  
``private static 返回值类型 方法名称(参数列表){
    方法体
}``
6.接口没有静态代码块，且不能写构造方法，接口是不能new的，一个类只有一个父类，但是可以同时实现多个接口，即作为多个接口的实现类
继承优先于接口实现

### 接口和类总结
   类于类之间是单继承的，直接父类只有一个，类与接口之间是多实现的一个类可以实现多个接口
   接口继承：多个父接口当中的抽象方法如果重复，没关系，多个父接口当中的默认方法如果重复那么子接口必须进行默认方法的重写

### 多态
一个对象拥有多种形态这就是对像的多态性，extends继承或者implements实现，是多态性的前提 
1.直接通过对象名称访问成员变量，看等号左边是谁优先用谁，没有向上找  
2.间接通过成员变量访问的。  
3.在多态代码中，成员方法的访问规则是，看new的是谁，就优先用谁，没有就向上找(编译看左边，运行看右边)与成员方法的覆盖重写不同成员变量是  
全部看左（**注意多态中不能新添加子类方法添加新的子类方法是无法访问到的，只能对父类方法覆盖重写或者是继续沿用，无法啊新添加方法）
多态用法抽象类或者接口调用某个东西，通过子类或者实现类实现后因为成员方法是编译看左运行看右，所以可以及执行不同子类的不同方法  
#### 对象转型
向上转型写法 格式： 父类名称  对象名 = new 子类（）(含义右侧创建了一个子类对象，把他当成父类来看待使用，** 注释向上转型一定是安全的 ）  
向下转型 ：多态中向下转型其实就是还原动作类似于强制转换类型  
格式 子类名称 对象名 = （子类名称）父类对象 含义将父类对象还原为原本的子类对象（new 的什么才能还原成什么）
如何才能知道父类引用对象本来是什么子类呢？
#### `instanceof`类名称这回得到一个bool值判断是否可行

### final关键字
表示最终的不可改变的  注意abstract和final不能同时使用，因为抽象类必须有子类来实现但是final又不能有子类所以不可同时出现
常见四种用法  
1.可以修饰一个类    格式 public final class 类名称  特点不能用有子类到此终结   
2.可以修饰一个方法  当修饰一个方法是就是最终方法不能被覆盖重写 final 类型 名称  
3.可以修饰局部变量  不能被重新修改，final的引用类型变量其地址不能改变，但是可以把地址里的内容改变（本质来说final定的是地址）  
4.可以修饰成员变量   final后成员变量不会再给默认值了，所以必须手动赋值，final的成员变量要么直接赋值要么构造赋值，而这只能选一个  
必须保证类当中所有的重载方法都最终会对final的成员变量进行赋值

### 权限修饰符 public > protected > default(不写) > private   
       同一个类下（自己访问自己）： 这些都能访问  
       同包不同类（邻居）： 只有private不能访问  
       不同包子类（父亲）： default 和private 不能访问  
       不同包非子类（陌生人）：只有public可以支持这种访问
### 内部类  
如果一个事务的内部包含另一个事物，如人身体包含心脏，那么心脏就是人身体的内部类  
分类：1.成员内部类  定义格式 修饰符 （public）clas 类名称里面再放一个类
      2.局部内部类
内部类可以用this而内部类访问外部类就要outer
*** 从java8开始只要局部变量事实不变，那么final关键字可以省略  
  因为： 1.new出来的对象在堆内存中  
        2.局部变量是跟着方法走的所以在栈内存中  
        3.方法运行结束后，立刻出战，局部变量会消失  
        4.new出来的对象在内存中会持续存在，知道jvm的垃圾回收后为止，所以当局部变量消失时，new出的对象还要用所以必须保证其成员变量不能被改变


### ***匿名内部类（用处是最多的）  
匿名掉接口实现的类  

### StringBuilder类和String类
字符串缓冲区，可以提高字符串的操作效率，可以看成长度变化的字符串，底层是一个数组但没有被final修饰所以可以改变长度，而String类创建后不能更改底层是被final修饰的数组  
进行字符串相加时内存会多个字符串占用空间多效率低下
#### apend（）
可以添加任意类型数据的字符串格式，并返回当前对象自身
#### toString（）
可以把StringBuild转换成String，String转StringBuild是通过其构造方法及StringBuild（str）即可  
### 包装类  
数据分为基本数据类型和引用数据类型，基本数据类型没有对应的方法来操作这些数据，我们可以通过一个类吧一个基本类型数据包装起来，  
在包装类中我们可以定义一些方法，用来操作基本类型的数据 （基本数据类型4类八种）
包装类用处比如字符串转int或者其他 除了char类型其他类型从字符串转换都可以用类型+parse类型
    ` java
    String s1 = "100";
    int a = Integer.valueOf(s1);
    int a = Integer.parseInt(s1)
    `  
    反之亦然
    ` int a = 100;
      string s1 = String.valueOf(100)
    `
    其他转字符串可以直接tostring

### collection集合集合是java中提供的一种容器可以用来存储多个数据
 数组是固定长度，而集合是不固定的，数组可存储对象可存储数据，而集合只能存储对象

集合:定义的是所有单列集合的共性方法，不带索引  

list接口  
1.有序的集合（存储取出元素顺序相同）  
2.允许重复元素  
3.有索引可以使用普通的for循环遍历  
set接口  
1.不允许重复的元素  
2.没有索引不能通过for循环便利，可以用迭代器访问
![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20210601173852.png)  

collection中提供的常用方法
add() remove() clear() contain() isEmpty() size() toArray()返回一个object的数组  
### Iterator(迭代器)
对应没有索引的进行便利例如set接口用法： 
1.boolean hasNext()如果有元素可以迭代则返回true   
2.next（）
### forEach循环
for(集合/数组的数据类型 变量名 : 集合名/数组名)，只能是数组或者collection
### 泛型 
泛型是一种未知的数据类型，当我们不知道是用什么数据类型时可以使用泛型，反省也可以是一个变量，来接受数据类型
E e : Element 元素  
T t ：Type类型  
集合在定义时不知道使用什么类型所以使用E
![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/2.png)  
>> 创建集合对象，不使用泛型
>> >好处：集合不使用泛型，默认类型就是object类型，可存储任意类型数据  
>> >弊端：不安全，会引发异常  
>> >集合对象使用泛型  
>> >好处：避免了类型转换的麻烦，存储的什么类型，取出的就是什么类型  
>> >弊端：反省是什么类型，只能存储什么类型  
#### 泛型的方法
泛型也可以用在方法上，定义在修饰符和返回值类型之间
泛型方法如下`public <E> void method1(E m)`
泛型接口 接口写法第一种使用方式：我可以指定接口实现的类型
`public interface iterfa <E>{
  public abstract void method2(E e);
}`
#### 抽象接口方法
实现方法：可以选择直接实现类或继续使用泛型
第一种实现方法
``` java
public class impl implements iterfa<String> {

  @Override
  public void method2(String s) {
    // TODO Auto-generated method stub
    System.out.println(s);
  }
```
第二种实现方法： 
``` java
public class impl1<E> implements iterfa<E>{

  @Override
  public void method2(E e) {
    // TODO Auto-generated method stub
    System.out.println(e);
  }

}
```
#### 泛型通配符
 ？代表任意的数据类型，使用方式，不能创建对象使用，只能作为方法的参数使用  
 定义一个方法，能遍历所有类型的ArrayList集合，这时候我们不知道ArrayList集合使用什么类型的数据，可以采用泛型的通配符来接受数据类型
 ，因为泛型是没有任何继承的概念的，所以采用泛型通配符。  
 泛型通配符的高级用法：泛型的上限和下限。  
 上限：？ extends E 代表只能是E类型的子类或者本身
 下限：？ super E 代表只能是E类型的父类或者本身（工作中用的不是很多）
### 集合
若集合中不重写tostring方法则返回集合对象就是对象存在的地址
### Linklist集合
查询慢增删快，底层是链表实现的，里面包含了大量的操作首位的方法，
### set
接口是一个不包含重复元素的集合，无索引。hash set不保证顺序永恒不变，即无序（存和取的顺序可能不一致先存的不一定先出）
#### 哈希set集合
底层采用数组和红黑树+链表，特点查询速度快。西安存储数据到集合中，计算元素的哈希值，在jdk1.8之后如果挂载超过8个（链表长度），就会转化成红黑树。 
采用系统自带的hashcode为数据赋值
#### set集合不允许存储重复的原理
先根据生成的hashcode存数据，如果发现另一个数据的hashcode已经存储过了，然后就调用equals方法比较是否相同，如果相同不在存储  
前提：必须重写hashcode方法和equals方法所以如果存储自定义类型元素，必须在方法上覆盖重写这两个方法。
#### LinklistHashSet 
具有可预知迭代顺序接口的哈希表和链表实现。与set不同之处在于，后者维护这一个运行于所有条部的双重连接列表。继承了hashset集合。  
与本身的hashset相比他保证了元素有序，多了一条链表。
### 可变参数
当方法的参数列表数据类型已经确定，但是参数的个数不确定是就可以采用可变参数。
#### 可变参数原理 
可变参数底层就是一个数组，根据传递参数个数不同，会创建不同长度的数组，来存储这些参数传递的参数个数。
参数传 类型 ....arr
*** 注意事项：1.一个方法的参数列表只能有一个可变参数 
             2.如果方法参数有多个，只能把可变参数写在末尾。
             3.可以用object类来接受任意类型数据
### collections的工具类
 collections中有addall方法可添加多个元素
 sort方法排序。静态方法，默认升序，第一种方法要重写排序方法compareTo。 
                                 第二种方法自己new 一个compartor，然后直接覆盖重写方法
### map
键值对，k必须唯一，及键唯一值可重复，键相当于坐标而值相对与数值，不同步多线程的。可以通过get（key）找value  
put方法把指定的键值对添加到map中 put（k，v）返回值v,若key不重复，返回null,若key重复返回被替换的v  
remove方法把指定的建所对应的键值对元素在map中删除，返回删除元素  
containskey 方法判断键值对中有无这个key，有返回true，没有返回false  
keysey方法 遍历map集合，把map集合中的所有key取出来放到set集合中 set<k>keyset() 该方法返回一个set<k>类  增强for循环遍历即可   
Entry<k，v> 映射项，在map接口中有个内部接口entry,作用，党map集合一创建，在map集合中回 创建一个Entry对象，用来记录键与值（键值对象，键与值的映射关系）    
可以用他来遍历map集合，该方法把map的Entry对象取出放到set集合中Entry是map类中的静态方法，会绑定map中的所有键值对，entryset是将返回的键值对存储到set中   

####  hashmap
  hashmap中如果要用自己定义的类作为key，就必须重写equal和hashcode方法。
 ### hashtable  同步实现类（单线程）
  早期的双链集合，哈希table不能存储空，无论键和值都不能空，因为是单线程的集合所以速度很慢
##  Jdk9新特性
  List，map，set接口里面添加了一个静态方法of，可以给集合一次添加多个元素.  
  static<E> list <E> of(E ... element)  
  使用前提:当集合中存储的元素个数已经确定，不再进行改变了。（of方法只适用于set，list，map，但不适用于接口的实现类）  
          of方法的返回值是不能改变的集合，集合不能在使用add，put方法进行添加元素，否则会抛出异常    
          map和set在调用接口的of方法时，不能有任何重复元素，否则会抛出异常  

  ### Debug调试程序  
  可以让大妈逐行执行，查看代码执行的过程，调试程序中出现的bug 
  执行程序 f8 ：逐行执行  
          f7 ： 进入到方法中  
          shift+f8 ： 跳出方法  
          f9：跳到下一个断点，如果没有就结束程序  
          console：切换到控制台
  ### java中的异常  
  异常体系机制中有个公共父类叫Throwable类
 ![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/throw%E7%B1%BB.png)
 throwable类：是所有错误或者异常的超类。
  exception和erro是throwable下的两个子类  
  Exception：编译器异常，进行编译时出现的问题。  
  Error：错误，相当于无法治愈的问题，必须修改源代码，程序才能继续执行。 
  处理异常thow抛出给虚拟机，try{}catch{}，能查看异常也能执行后续代码   
  异常产生过程分析：jvm检测到程序出现异常后，  
 **1.jvm会根据异常的原因创建一个对象，这个对象包含了异常的产生（内容，原因，位置）  
  `new ArrayIndexOutOfBoundsException`（"3"）  
  2. 在方法中没有异常处理逻辑如（try catch），那么JVM会把异常对象抛出给方法的调用者，若调用者也没有，就在网上调用，最终返回给JVM，    
    jvm接受这个异常对象（原因，位置，内容）打印到控制台然后中断当前执行的程序**  
  #### 异常的处理
  throw关键字  
  作用：可以使用throw关键字在指定的方法中抛出异常  
  使用格式： throw new xxException（异常产生的原因）  
  注意 :  1.throw关键字必须写写在方法的内部  
          2.throw关键字后new对象必须是Exception或者其子类对象  
          3.throw关键字抛出异常，我们就必须对这个异常进行处理要么throw，要么try catch
          4.如果方法内部抛出多个异常且具有父子关系，那么直接声明父类异常即可  
          5.如果声明了异常就必须交给方法的调用者处理
  object类中有requireNonNull方法判断是否为空。
  #### try catch 
 `try{
    可能异常代码
  }catch{
    异常处理的逻辑  
  }
  ...catch{
    
  }
  //try中可能回抛出多个异常对象，那么就可以使用多个catch来处理这些异常对象  
    如果try中产生了一场，那么就会执行异常的执行逻辑
  `
  #### throwable类中定义了3个异常处理的方法  
  public string getMessage()  获取异常的描述信息  
  public string tostring()  获取异常的类型和异常描述信息 （返回异常描述）默认调用   
  public void printStackTrace() 打印异常的跟踪栈信息并输出到控制台  异常信息最为全面  

  #### final代码块  
  有一些特定的代码无论一场是否发生，都需要执行，另外，因为异常发生程序跳转，导致有些语句执行不到。而finally就是解决这个问题的，在finally代码块中存放的  
  代码块一定会被执行，try中出现异常会立即抛个catch，无法执行后面的，但finally可以  
  finally无论是否出现异常都会继续执行 
  #### 多异常捕获  
  1.多个异常分别处理  
  2.多个异常一次捕获多次处理  
  3.多个异常一次捕获一次处理  
  2. 一个try可以对应多个catch  （一次捕获多次处理）**  catch定义的异常类中如果有父子关系，子类必须写在上面，父类在下面  
    原因（多态性）抛出异常对象是会从上倒下一次赋值给catch中定义的异常变量 如下图  
    ![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/%E5%BC%82%E5%B8%B8%E5%A4%84%E7%90%86.png)    
  
  3. 只要catch定义的异常可以处理任何try中的，即可，例如expection异常可以处理一切异常
  #### 父子类异常  
  1.父类什么异常子类什么异常  
  2.子类重写时，抛出父异常的子类  
  3.不抛出任何异常  
  4.父类没有抛出异常，子类重写父类方法时，不能声明式抛出，只能捕获异常（try catch）

#### 自定义异常  
java提供的异常类，不够使用时，需要进行自己定义异常类格式
  `public class xxxxx extends Exception||RuntimeException
  { 添加空参数构造方法,
    添加一个带异常信息的构造方法
  }
  `
  继承exception，那么自定义的一场就是编译异常，如果方法内部抛出编译异常，就必须进行处理，要么throws，要么try，catch
  继承RuntimeException，那么自定义类就是个运行异常，交给jvm处理即可例子   
  `public class index extends Exception {

  public index() {
  }

  public index(String message) {
    super(message);
  }//查看源码发现，所有异常类都会有一个带异常信息的构造方法，方法内部会调用父类带异常信息的构造方法，交给父类来处理

}
`
 ### 多线程  
  #### 并发与并行
  并发：指两个以上的事在用以时间段发生。  （交替执行）  
  并行：两个以上的事在同一时刻发生。（同时执行）    
#### 线程与进程  
  进程：(Process)是系统进行资源分配的基本单位，每个进程都有其独立的内存空间
  线程：是进程调度的基本单位，是进程执行的一个基本单元，线程是轻量级的进程，是执行单元。通过线程调度到cpu进行处理

  线程调度  
     分时调度，所有线程轮流使用
  抢占式调度，优先让优先级高 的
 #### Thread类
  主线程（执行main方法的线程）。
  JVM执行main方法是，main方法会进入到栈内存，JVM会找操作系统开辟一条main方法通向cpu的执行路径，cpu就可以通过这个路径来执行main方法，而这个路径有个名字叫主线程  
  ![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/%E4%B8%BB%E7%BA%BF%E7%A8%8B.png)
  创建多线程执行方法有两种，一种是将类声明为Thread的子类。该子类应重写Thread类的run方法  
  实现步骤创建子类，覆盖重写run方法，调用thread类中的方法，开启新的线程调用start方法，执行run方法  
  void start（）是该线程程序开始执行，java虚拟机调用该线程的run方法。结果是两个线程并发运行，当前线程和另一个线程  
  （创建的新线程，执行其run方法）多次启动一个线程是非法的，特别是当线程已经结束执行后，不能再重新启动  
  java属于抢占式调度，哪个线程优先级高，哪个先执行，同优先级随机执行  随机抢占谁抢到谁执行,随机打印 
    ![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/%E7%BA%BF%E7%A8%8B%E9%9A%8F%E6%9C%BA%E5%8E%9F%E7%90%86.png)
  #### 多线程原理，多线程内存图
一旦调用xx.start,开辟新的空间新的栈，执行新的方法
 ![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/%E5%A4%9A%E7%BA%BF%E7%A8%8B%E5%B7%A5%E4%BD%9C%E5%8E%9F%E7%90%86.png)
   #### Thread类中的方法
 ![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/Thread%E7%B1%BB%E5%B8%B8%E7%94%A8%E6%96%B9%E6%B3%95.png)
   ##### 获取当前名称    
        1.使用Thread类的方法getName  返回名称  
        2.可以获取到当前正在执行的线程使用线程中的方法currentThread.getName方法获取线程的名称
   #### 创建多线程程序的第二种方法  
        实现Runable接口，其中实现类必须定义一个run的无参方法创建实现对象，将对象从Thread的构造类中传入开启start方法即可
   #### Thread类和Runable的区别
        1.避免单继承的局限性：一个类只能继承一个类（一个类只能有有一个父类），继承Thread就不能继承其他
        2.增强程序的扩展性，降低程序的耦合性（解耦）
          实现Runable接口的方式，把设置线程任务和开启新线程进行分离（解耦）
          实现类中重写run方法用来设置线程任务；
          尽量采用runable接口方式


 #### 线程安全
  当多线程访问共享数据可能会出现线程安全问题
  线程安全是不能产生问题的，我们可以让一个线程在访问共享数据时，无论是否失去cpu的执行全，
  让其他的线程只能等待，当前线程卖玩票后， 其他线程方可访问。保证一个线程访问共享数据源。
  解决线程安全问题方式：同步方式有三种方法  
    1.同步代码块  
        1.同步代码块中的锁对象，可以是任意对象   
        2.但是必须保证多个线程使用的锁对象是同一个   
        3.锁对象的作用  （把同步代码块所著，只让一个线程在同步代码块中执行） 
     原理：使用了一个锁对象，这个锁对象叫做同步锁，也叫做对象监视器，3个线程一起抢夺cpu的执行权，谁抢到了谁执行run方法，t0抢到了cpu，
  遇到`synchronlzed`代码款只是t0会检查代码块是否有锁对象，发现有就会获取捣碎对象进入到同步执行   
          当他抢到时候，执行run方法，遇到synchronized代码块这是会检查synchronized代码块是否有锁对象，发现没有，进入到阻塞状态，会
  一直等着t0归还锁对象，直到归还时候t1才能获取到锁对象进入到同步执行中  
    特点：同步代代码块只能有一个线程在同步中执行共享数据，但降低了效率

    2.同步方法   
       定义同步方法定义一个`synchronized`的关键字 ,其锁对象就是this指向的对象   
       静态同步方法中，锁对象不能是this，this是创建对象之后产生的，静态方法优先于对象，静态方法的对象是本类
  的class属性--->class文件对象（反射） 
    3.锁机制（lock锁）  
      使用lock锁的方法 ：`void lock()`获取锁`void unlock()`释放锁 
      使用步骤：1.在成员位置创建一个ReentranLock对象
               2.在可能会出现安全问题的代码前调用lock的获取锁  
               3.在结束时调用unlock（就是操作系统的pv操作）（放在finally操作中） 
  #### 线程的状态  
  ![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/%E7%BA%BF%E7%A8%8B%E7%8A%B6%E6%80%81%E6%A6%82%E8%BF%B0.png)
  #### 等待唤醒两种方法  
  1.`synchronized(obj)`在需要等待的程序调用`object`的`wait`方法进入等待状态，在需要唤醒时调用`object`的`notify`方法
  2.继续采用lock方法
  `    Lock lock = new ReentrantLock();
    Condition condition = lock.newCondition();`
  在需要等待的程序中调用 `condition.await`在需要唤醒的地方调用`newCondition`的`signal`或`signalAll`方法  
  列子
  ``` java
  public static void main(String[] args) {
    Object obj = new Object();
    Lock lock = new ReentrantLock();
    Condition condition = lock.newCondition();
    new Thread(new Runnable() {

      @Override
      public void run() {
        synchronized (obj) {
          System.out.println("包子数量");
          try {
            obj.wait();
          } catch (InterruptedException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
          }
          System.out.println("吃包子");
        }
        // lock.lock();
        // try
        // {
        // try {
        // System.out.println("要5个包子");
        // condition.await();
        // } catch (InterruptedException e) {
        // // TODO Auto-generated catch block
        // e.printStackTrace();
        // }
        // condition.signal();
        // System.out.println("付钱吃包子");
        // }
        // finally{lock.unlock();}
    
      }
    
    }, "客户").start();
    new Thread(new Runnable() {
      @Override
      public void run() {
        // lock.lock();
        // // TODO Auto-generated method stub
        // try
        // {
        // try {
        // Thread.sleep(500);
        // } catch (InterruptedException e) {
        // // TODO Auto-generated catch block
        // e.printStackTrace();
        // }
        // System.out.println("包子做好了");
        // condition.signal();
        // }
        // finally{lock.unlock();}
           try {
            Thread.sleep(5000);
        } catch (InterruptedException e) {
          // TODO Auto-generated catch block
          e.printStackTrace();
        }
        synchronized(obj)   //一定要用锁对象来唤醒他
        {
          System.out.println("包子好了");
          obj.notify();
        }
      }
    }, "boss").start();
  } 
  ```

  objectde wait方法中可以传递毫秒参数，当毫秒到达没有被唤醒，则自动叫醒
  `notifyall`唤醒所有线程（对象锁上的所有线程） 
  #### 线程通信  
  多个线程在处理同一个资源但是处理的动作（任务）不同  
  为什么要处理？因为多个线程并发执行，在默认情况下cpu随机切换，当我们需要多个线程来共同完成一件任务，并且 
  我们需要多个线程来完成一个任务，那么需要线程之间进行协同通信
  #### 线程池
  如果并发线程数量很多，并且执行时间很短，频繁创建就效率不高了，在java中可以用线程池来进行优化，即不再反复创建服用线程  
  线程池就是一个容器
 线程池jdk1.5之后提供 executors类用来生产线程池 
  其中static ExecutorService jew fixedthreadpool（int n Thread） 
  ExecutorService接口返回的是ExecutorService接口的实现类对象，我们可以用ExecutorService接口接受  
  使用步骤:
  1.使用线程池的工厂类Executors里面提供的静态方法newFixedThreadPool生拆一个指定线程数量 
  的线程池
  2.创建runnable接口实现run方法重写   
  3.调用ExecutorService中的submit方法，传递线程任务，开启线程，执行run方法   
  4.调用ExecutorService中的方法shutdown销毁  
  例子   


  ``` java
  public static void main(String[] args) {  
    ExecutorService se = Executors.newFixedThreadPool(2);  
   ` se.submit(new runnableimpl());   //线程池会一直开启，使用万会归还个线程所以可以继续使用`
    se.submit(new runnableimpl());  
    se.submit(new runnableimpl());  
  }
  ```


​     
  ### Lambda表达式
  面向对象强调必须通过对象的心事来做事情，而函数式思想则尽量忽略面向对象的复杂语法--强调做什么而不是什么形式
  lambda标准格式有三部分组成
  1.一些参数2.一个箭头3.一段代码
  （参数列表）->{一些重写方法}例如排序题  

  ``` java
  Arrays.sort(arr,
      (Person p1,Person p2)->{
        return p1.age-p2.age;
      }
    )
  ```

  正常要new Comparator从写campare排序方法
  lambda表达式省略规则，要代码只有一行return {}和;都可以省略要省略都省略  
 注意：使用lambda语法是必须要有接口，并且要求接口中有抽象方法，接口方法存在且唯一时才能使用。  
  ### File类
  主要用于查找、创建、删除、判断存在否文件夹
  path中windows下时\而linux下是/路径中的\\要写两个，一个转意一个
  createNewFile（）创建空文件，delete（）删除文件或者目录  
  mkdir（）创建文件夹mkdirs创建多级文件夹
  file遍历，两个list和listfiles方法便利的是构造方法中给出的目录，如果构造方法中给出的目录不存在会抛出空指针异常  
  对目录遍得到的是名称前一个是返回名称，后一个返回file对象  
  file类filter方法，过滤器有两个接口需要自己定义实现类，filenamefilter和filef  ilter
  ### io流
  顶层父类： InputStream（字节输入流）、Reader字符输入流
            OutputStream 字节输出流  Writer 字符输出流

  字节输入流的使用步骤  
  1.创建FileOutputStream对象 
  2.会根据构造方法中传递的文件，创建一个空文件  
  3.会把该对象指向创建好的文件写入数据
  write方法写入数据
  再用close方法关闭流

  ## 网络编程  
  c/s结构客户端和服务结构，B/S浏览器和服务器结构
  网络通信协议：Tcp/Ip协议和UDP协议
  ![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/tcpip%E5%8D%8F%E8%AE%AE.png)
  UDP协议:无连接通信协议，即在传输数据时，数据的发送端和接收端不建立逻辑链接，资源消耗较小，通信效率较高，用于音频视频，但是用UDP协议传输数据时由于  
  无连接行，不能保证数据的完整性（数据被限制在64kb内）
  tcp协议：面向连接协议，必须三次握手  
  1.客户端向服务器发送连接请求，等待服务器确认  
  2.服务器端给客服端响应，通知客户端接收到请求  
  3.客户端再次向服务器发送信息确认，确认链接
 ![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/%E4%B8%89%E6%AC%A1%E6%8F%A1%E6%89%8B.png)  
  用于文件上传，网页浏览等等
  ### 网络编程三要素  
  协议、IP、端口号
  端口：是一个逻辑端口，无法直接看到，可以使用一些软件查看，取值范围在0-65535之间  1024之前的端口号不能使用，一般被系统分配给已知的软件了  
  端口号不能重复
  mysql：3306 oracle：1521  tomcat：8080
  ### TCP通信  
  java中提供了两个类实现TCP通信，Socket类和ServerSocket类  
  Socket类：创建socket对象，向服务端发送连接请求，服务端响应请求（通信过程采用IO流对象，一般使用字节流对象）
  服务端必须明确两个问题：1.多个客户端同时与服务器交互时，在服务器上有个方法，叫accept客户端可以获取到请求的客户端对象 
  2. 第一个客户端与服务器交互，就需要使用多个IO流对象  
    服务器没有IO流，可以获取到请求的客户端对象Socket使用每个客户端socket中提供的Io流和客户端进行交互 
    server.accpet（）可以获取到请求的对像
    客戶端实现步骤： 
    1.创建一个客户端对象`Socket`，构造方法绑定为ip地址和端口号  
    2.使用Socket对象中的getOutputStream方法获取网络字节输出流OutputStream
    3.使用网络字节输出流Outputstream对象中的write方法给服务器发送数据  
    4.使用socket对象中的方法getInputStream获取网络字节输入流InputStream对象  
    5.使用网络字节输入流对象的read方法，读取服务器回写的数据  
    6.释放资源  
    注意事项：
    1.客户端和服务器端进行交互，必须使用socket中提供的网络流不能使用自己创建的流对象  
    2当我们创建客户端对象socket的时候，就会去请求服务器和服务器经过3粗握手建连接通路只是后如果服务器没有启动就会抛出异常  

  服务器端实现步骤：  
  1.创建服务器serversocket对象和系统要制定的端口号  
  2.使用serversocket对象中的方法accept，获取到请求的客户端对象socket  
  3.使用socket对象红的getinputStream方法获取网络字节输入流对象  
  4.使用网络字节输入流对象中的read方法，读取客户端发送的信息  
  5.使用socket对象中的方法getOutputstream获取网络字节输出流
  6.使用网络字节输出流对象方法中的write方法给客户端回复  
  7.释放资源  
  TCP通信的文件上传案例  
  原理：客户端读取本地的文件，那文件上传到服务器，服务器再把上传的文件保存到服务器的硬盘上  
  1.客户端使用本地的字节输入流，读取上传的文件  
  2.客户端使用网络字节输出流，把读取到的文件上传到服务器  
  3.服务器使用网络字节输入流读取客户端上传的文件  
  4.服务器使用本地字节输出流，把读取到的文件，保存到服务器的硬盘上  
  5.服务器使用网络字节输出流，给客户端回写一个“上传成功”
  6.客户端使用网络字节输入流，读取服务器回写的数据  
  7释放资源  
  注意：客户端和服务器和本地硬盘进行读写，需要使用自己创建的字节流对象  
  客户端和u武器之间进行读写，必须使用socket中提供的紫萼流对象  
  文件上传的原理，就是文件的复制 （客户端）
  明确：数据源  和目的地
        ![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20210717205330.png)
  实现步骤 ：
  1.创建本地字节输入流fileInputstream，构造方法绑定数据源  
  2.创建客户端socket对象，构造方法绑定ip地址和端口号  
  3.使用socket的getOutputstream，获取网络字节输出流对象  
  4.使用本地的字节输入流对象的read方法读取本地的文件  
  5.使用网络字节输出流中的write方法，读取到的文件上传  
  6.使用socket中的getinputstream，获取网络字节输入流  
  7.使用网络字节输入流的方法read读取服务器的数据  
  8.释放资源  

  服务端  
  文件上传原理 ：
  明确：数据源，服务器目的地  
  实现步骤 ：
  1.创建一个服务器serversocket对象和系统指定的端口号  
  2.使用serversocket对象的accpet方法，获取请求的客户端socket对象  
  3.使用socket对象中的方法getinputstream，获取到网络字节输入流inputstream对象  
  4.判断文件夹是否存在，不存在创建  
  5.创建一个本地字节输出流对象构造方法绑定输出目的地  
  6.使用网络字节输入流Input stream对象中的read方法读取客户端文件
  7.使用本地字节输出流fileoutputstream中的write方法，把读取到的文件保存到服务器的硬盘上  
  8.使用socket对象中的getoutputstream方法获取网络字节输出流对象  
  9.使用网络字节输出流对象的outputstream对象中的方法write，给客户端回写上传成功  
  10.释放资源  
  如若多个客户端同时访问需要用多线程来进行实现
  有一个客户端请求就开启一个线程完成文件上传new一个线程即可。

  BS服务器：服务器要给客户端回写一个信息，回写以恶html页面  
  我们需要读取index。html文件，就必须得知道这个文件的地址  
  而这个地址就是请求信息的第一行，可以使用BufferedReader中的方法readLine读取一行 InputStream is = socket。getInputStream（）；
  new BufferedReader（new InputStreamReader（is））；把网络字节输入流转为字符缓冲输入流  
  可以使用String类的方法split切割字符串，获取中间的部分  arr[l] 使用Stringsubstring方法获取html文件的路径
  服务器创建本地的字节输入流根据获取到的文件路径，读取html文件  
  服务器端使用网络字节输出流把读取到的文件，写道客户端（浏览器）显示
  ``` java 
  public class htmlServe {
    public static void main(String[] args) throws IOException {
        ServerSocket serve = new ServerSocket(8080);
        while (true) {
            Socket socket = serve.accept();
            System.out.println(111);
            new Thread(new Runnable() {
                @Override
                public void run() {
                    try {
                        InputStream is = socket.getInputStream();
                        BufferedReader br = new BufferedReader(new InputStreamReader(is));
                        String line = br.readLine();
                        System.out.println(line);
                        String[] arr = line.split(" ");
                        String htmlpath = arr[1].substring(1);
                        FileInputStream fis = new FileInputStream(htmlpath);
                        OutputStream os = socket.getOutputStream();
                        //http协议固定写法
                        os.write("HTTP/1.1 200 OK\r\n".getBytes(StandardCharsets.UTF_8));
                        os.write("Content-Type:text/html\r\n".getBytes(StandardCharsets.UTF_8));
                        os.write("\r\n".getBytes(StandardCharsets.UTF_8));
                        int len = 0;
                        byte[] bytes = new byte[1024];
                        while ((len=fis.read(bytes))!=-1) {
                            os.write(bytes,0,len);
                        }
                        fis.close();
                        socket.close();
                    }catch (IOException e){
                        System.out.println(e);
                    }
                }
            });
        }
    }

    } 
  ```

  ## 函数式接口  
  函数式接口在java中指：有且只有一个抽象接口  
  函数式接口，适用于函数式编程场景的接口。而java中的函数式编程体现就是Lambda，有意函数式接口就是可以适用于Lambda的接口，只有确保   
  ***接口中有且仅有一个抽象方法***，Java中的Lambda才能顺利进行推导  
  Lambda表达式可以被当作匿名内部类的语法糖  
  格式：只要保证接口中有且只有一个抽象方法即可
  ### Lambda表达式延迟执行的
 由于Lambda表达式延迟执行，所以满足条件时才执行相关方法
  ### Supplier接口  
  生产型接口，指定泛型是什么类型，get方法就会生产什么类型的数据名字叫什么就可以用Lambda优化什么
  ``` java
  private static String getstring( Supplier<String>sup){
        return sup.get();
    }

    public static void main(String[] args) {
        System.out.println(getstring(()-> "sssss"));
    }
  ```

### Consumer接口（消费型接口）
  使用accept方法吧置顶泛型的数据消费
 andThen 方法把两个consumer类型的对象组合在一起在进行同时消费还是要用accept方法返回 
 ### Predicate接口对某种类型的数据进行判断，从而得到一个Boolean值
  ``` java
  public static boolean check(String s, Predicate<String> pre){
        return pre.test(s);
    }

    public static void main(String[] args) {
        String s = "aasssssss";
        System.out.println(check(s, s1->s1.length()>111));
    }
  ```
  and方法`pre.test(s)&&pre.text(s)`==`pre.and(pre2).test(s)`
  同理还有 or方法和negate方法也就是或和非
  ### Function接口抽象发发为apply方法，用来根据一个类型的数据的到另一个类型的数据，前者称为前置条件，后者成为后置条件  
  使用 
  ``` java
  public static  void change(String s , Function<String,Integer> fun){
        int i = fun.apply(s);
        System.out.println(i);
    }

    public static void main(String[] args) {
        String s = "123456";
        change(s,(s1)-> Integer.parseInt(s1));
    }
  ```
  同样function接口中也有默认方法andThen，用来组合。
  ### Stream流 
  集合数据的过滤例如
  ``` java
  public static void main(String[] args) {
        List<String> l = new ArrayList<>();
        l.add("Messi");
        l.add("Xavi");
        l.add("Namyer");
        l.add("Rondla");
        l.add("Mubapa");
        l.add("mudiniao");
        //stream中有个方法叫做filter可以进行判断类似与javascript中的filter
        l.stream().filter(name->name.startsWith("M")).filter(name->name.length()<7).forEach(name->
                System.out.println(name.getClass().equals(new String().getClass())));//类型检测

    }
  ```
  流式思想：拼接流式模型
  ![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/%E6%B5%81%E5%BC%8F%E6%80%9D%E6%83%B3%E4%B8%BE%E4%BE%8B.png)
  ![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/%E6%B5%81%E5%BC%8F%E6%80%9D%E6%83%B3%E7%A4%BA%E6%84%8F%E5%9B%BE.png) 

  这里的filter、map都不是立即执行因为用到了map只有到cout后才执行
  注意**java中的stream并不会存储元素而是按照需要进行计算，其中流的数据来源可以是集合数组等。。。。
  与Collection中不同stream操作还有两个特征，
  1.Pipelining 中间的操作都会返回流对象本身，这样有利于链式编程，可以对操作进行优化例如延迟执行或者短路  
  2.内部迭代，以前对集合遍历都是通过迭代器或者增强for循环的方式，显示的在集合外部进行迭代这样叫做外部迭代，  
  而Stream流提供了内部迭代方式，流可以直接调用遍历的方式 
  当使用流时，有三个步骤，
  1.获取数据源  
  2.数据转换  
  3.执行想要的结果  并且每次转换Stream对象不改变，返回一个新的Stream对象，这就有利于链式编程

  jdk9.1后所有集合都可以通过默认Stream方法获取流对象可以将一个集合转换为一个流 （map不能直接这样用）必须是单列集合
  ``` java
  Stream<String> s = l.stream();
        Set<String> s1 = new HashSet<>();
        Stream<String> s2 = s1.stream();
        Map<String,String> m = new HashMap<>();
        Stream<String>s3 = m.keySet().stream();
        Collection<String> l2 = m.values();
        Stream<String> s4 = l2.stream();
        Set<Map.Entry<String,String>> en = m.entrySet();
        Stream<Map.Entry<String,String>> s5 = en.stream();
  ```
  #### Stream常用方法  
  延迟方法：返回值任然是Stream是支持链式调用  
  终结方法：返回值不再是Stream接口自身的类型方法，及不再支持StringBuilder那样的链式调用包括forEach和cout
  ##### forEach
  forEach方法中传递的是Consumer接口所以可以用Lambda表达式优化是终结方法返回的不是Stream对象
  ##### filter返回的是predicate接口判断对象如果结果为true那么stream对象会留用如果为false那么就会删掉
  注意***Stream流类似与流水线，第一个流调用完毕方法并且赋值到其他管道流上那么所有的是数据就会转流到下个Stream对象上，而这是第一个Stream流就会关闭  
  所以第一个流不能再此使用了
  ##### map 方法如果需要将流中的元素映射到另一个流中可以使用map方法
  其中map方法中传递的参数是Function接口 
  ``` java
  Stream<String> s = Stream.of("1","2","3","4");
        s.map(s1->Integer.parseInt(s1)).forEach(intt-> System.out.println(intt));
  ```
  ##### count 
  相当于集合中的size统计Stream中流元素的个数，终结方法，返回值是long类型的整数，所以不能再调用任何Stream中的方法了
  ##### limit 方法可以对流进行截取  
  是一个延迟方法所以还是可以继续调用Stream中的方法，只是对流中元素截取，返回新的流
  `stream.limit(3)`意思是只要前三个
  ##### skip 
  跳过六种的前几个元素，返回一个新的截取流作用基本与limi相似
  ##### concat 
  静态方法：可以将两个流合并为一个流

  ### 方法引用  （只是对Lambda的再次简化）
  对Lambda表达式的简化我们实际传递进去的代码是一种解决方案，所以如果我们在Lambda表达式中所指定的方法，已经有了相同方案  
  那么是没有必要重复逻辑的 
  ``` java
  public  static  void printString (String s,Printable p){
        p.print(s);
    }

    public static void main(String[] args) {
        printString("hellow",s-> System.out.println(s));
    }
  ```
  Lambda表达式的目的，打印参数传递的字符串，把参数s传递给了cout对象，调用out对象中的方法println对字符串进行输出  
  注意  ：
  1.system.out对象已经存在  
  2.println方法也是存在的  
  所以我们可以优化方法，使用system.out方法   
  #### `::`双冒号为引用运算符
  他所在的表达式被称为方法引用，如果Lambda表达式的函数方案已经存在于某个方法的实现中，那么则可以通过双冒号来引用该方法作为Lambda的代替者
  注意：*** Lambda表达式中传递的参数一定是方法引用中的哪个方法可以接受的类型，否则会抛出异常  
  #### 通过对象名引用成员方法
  对象名存在，成员方法也存在，那么就可以使用对象名来引用成员方法 ，对象存在方法存在既可以优化Lambda表达式
 `printStr(obj::printUpper)`
  #### 通过类名引用静态方法  
  类存在，静态成员方法存在，即可以继续使用
  ` int i= method(222,Math::abs)`
  #### 通过super来调用父类的成员方法   
  `method(super::sayhellow);`
  #### 通过this来调用子类的成员方法    
  `method(this::sayhellow);`
  #### 类的构造器引用
  由于构造器名称与类名称完全一直，所以可以类的名称::new 的格式表示
  #### 数组构造器引用首先必须满足是函数接口，其次才可以简化Lambda表达式
  ``` java
  //        int arr = createArray(10,length -> new int[length]).length;
        //方法引用优化Lambda表达式
        int arr = createArray(8,int[]::new).length;
  ```


  # Java Web 
  内容：
  1.Junit单元测试  2.反射  3.注解  
  ## Junit单元测试  
  测试分类 ：黑盒测试和白盒测试
  黑盒测试：不用关注过程，只需要看输入输出是否一致,不需要写代码  
  白盒测试：不光看输入输出，还要关注程序执行的具体过程  
  ![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/%E9%BB%91%E7%99%BD%E7%9B%92%E6%B5%8B%E8%AF%95.png)  
  Junit属于白盒测试的一种  
  Junit使用：
  步骤：
  1.定义一个测试类名+Test  
  2.定义测试方法，可以独立运行 
    *建议方法名+test 例如 testadd（）
    *建议无返回值，建议空参  
  3.给方法加注解@Test（加入注解）
  4.导入Junit的依赖环境  
  ``` java
  @Test
    public  void  testAdd(){
        Assert.assertEquals(3,new Calculator().add(2,3));
    }
  ```
   * 红色代表成功绿色代表失败 注意要用断言方法Assert（期望的，实际的）而不是输出 
    对于重复操作，通过注解before和after来完成  
    before初始化方法：所有测试方法之前都执行这个方法
    after释放资源方法：在所有测试方法执行完后都会自动执行该方法
    无论上述方法是否出错，这两个方法一定执行  
  ``` java
  @Before
    public  void init (){
        System.out.println("用于资源申请");
    }
    /* 测试方法 */
    @After
    public  void close(){
        System.out.println("用于资源释放");
    }
    @Test
    public  void  testAdd(){
        Assert.assertEquals(3,new Calculator().add(2,3));
    }
    @Test
    public  void testSub(){
        Assert.assertEquals(3,new Calculator().sub(5,2));
    }
  ```
  ## 反射：框架设计的灵魂  
   * 框架：半成品软件。可以在框架的基础上进行软件开发，简化编码  
     主要用于框架 
   ### 概念 
  将类的各个组成部分封装为其他对象
  source源代码阶段还在硬盘上，，将字节码文件加载进内存通过类加载器将class的字节码文件加入内存，在内存中会用对象描述字节码文件 
  Class类（描述自解码文件）其中由三部分重要东西（成员变量，构造方法，成员方法） 
  功能：获取成员变量，获取构造方法，获取成员方法，获取类名
  将成员变量封装为Field对象，将构造方法封装为Constraints对象  ，成员方法封装为Method，每个都通过数组来描述所有的变量或者方法
  ，后面再通过类对象的行为赖创建所需要的对象，所有对象都是通过类对象来创建的。其中将各种变量封装成其他对象，这就是反射机制 
  new的对象属于运行时阶段Runtime对象属于第三阶段 
  反射的好处：
  1.在程序运行过程中，操作这些对象  
  2.内获取成员方法：（列入定义字符串，那么会将字符串对象字节码文件加载入内存，内存中有class对象 ，将所有方法封装为对象，将在数组中的方法展示出来即可）
  3.解耦，降低程序的耦合度，增加扩展性   
	
  ### Field
  getFIelds获取所有public修饰的成员变量  
  操作get或者set
  ``` java
  Class person = Person.class;
//        Field[] fields = person.getFields();
        Field a = person.getField("s");
        Person p = new Person();
         Object va = a.get(p);
         a.set(p,"ssssw");
        System.out.println(p+" "+va);
  ```
  getfiled（对象名字） getDeclareFields（）获取所有成员变量
  反射面前没有私有公用，都可一访问修改（很重要）在需要访问不是public的需要忽略访问权限修饰符的安全检查  
  的。`setAccessible（true ）`
  setAccessible（true）不管是反射的那几个对象都拥有几个方法
    ### 构造方法  
  根据传递的参数判断根据不同参数的class对象进行判别
  （构造方法就是用来创建对象的）创建对象：用构造器 newInstance
  ``` java
  Class person = Person.class;
        Constructor con = person.getConstructor(String.class);
        Constructor con1 = person.getConstructor();
        System.out.println(con);
        System.out.println("---------------------------->");
        System.out.println(con1);
        var p = con.newInstance("zhangsan");
        System.out.println(con1.newInstance());
        System.out.println(p);
  ```
  若用空参数方法构造创建对象，操作可以进行简化可以使用Class对象的newInstance不需要在通过Class类的getConstruct方法获取构造器方法了
  ### 获取成员方法  
  不带Declared只能获取公共的，带的可以通过setAccessible访问私有的
  #### invoke
  获取成员方法的目的也是为了执行，所以invoke方法可以执行方法  
  `invoke（Objet obj，Object ...args）`
  ``` java
  Method method = person.getMethod("eat");
        method.invoke(new Person());
        Method method1 = person.getMethod("eat",String.class);
        method1.invoke(new Person(),"饭");
  ```
  #### getName
  可以获取方法名称，返回字符串的方法名称 

  #### Properties 类  
  Properties 类位于 java.util.Properties ，是Java 语言的配置文件所使用的类， Xxx.properties 为Java 语言常见的配置文件，如数据库的配置 jdbc.properties,  
  系统参数配置 system.properties。 这里，讲解一下Properties 类的具体使用。以key=value 的 键值对的形式进行存储值。 key值不能重复。JVM 中可以获取Properties, 
  来打印输出 JVM 所了解的属性值。
用list() 方法，打印到控制台。

  ``` java
  @Test
	public void printTest(){
		Properties properties=System.getProperties();
		properties.list(System.out);
	}
```

  实现：
  1.配置文件 
  2.反射  
  步骤：
  1.将需要创建的全类名和需要执行的方法定义在配置文件中  
  2.在程序中加载读取配置文件 
  3.使用反射技术来加载类文件进入内存  
  4.创建对象  
  5.执行方法
  框架的基本思路 
  ``` java
  //加载配置文件
        //1.创建Properties对象
        Properties pro = new Properties();//Properties是map的一个子类，所以是一个双链集合
        //加载配置文件，转换为一个集合
        //1.2.1获取class目录下的配置文件
        ClassLoader classloader = IndexReflect.class.getClassLoader();
         var io = classloader.getResourceAsStream("pro.properties");
        pro.load(io);

        //2.获取配置文件中定义的数据
        String className = pro.getProperty("classNamess");
        String methodName = pro.getProperty("methodNamess");
        // 3.加载改类进内存
        Class cls = Class.forName(className);
        //4.创建对象
        var obj = cls.newInstance();
        Method method = cls.getMethod(methodName);
        method.invoke(obj);
  ```
  ### 反射中获取class类对象的三种方式
  1.在源代码阶段，如果还没有进内存需要手动加载进内存生成字节码对象需要通过Class.forName("传全类名")该方法会将字节码文件加入内存并返回一个class  （用于配置文件，读取文件加载类）  
  2.当已经加载进内存了，已经有了这个对象，那么在加载进内存后会有一个类名，可以通过类名的属性获取class类对象  类.class  （多用于参数传递）  
  3.通过对象的getclass的方法获取class对象 （多用于对象获取字节码的方式）  
  结论：同一个字节码文件（*.class）在一次程序运行过程中，只会被加载一次，不论通过哪一种方式获取的class对象始终是同一个


  ### class对象  
  调用构造方法的newInstance来创建对象
  ` Factory factory = new Factory();
Object obj = factory.newInstance();`
 如今被getDeclaredConstructor().newInstance()代替
  大部分是获取功能   
  1.获取成员变量们    getFields和getField  获取成员变量们 getDeclareFields（）获取所有的  
  2.获取构造方法们    getconstructor获取单个加s返回数组的  getDeckareFields获取所有的   
  3.获取成员方法们    getMethod获取单个加s获取所有的

  ## 注解  
  概念：
  类似于注释，用文字去描述程序。给程序员看的而注解是说明程序的，是给计算机看的。  
  源数据，一种代码级别的说明，jdk1.5之后的新特性，与类、接口、枚举是在用一个层次。他可以声明包、类、字段、方法、局部变量、参数的前面  
  用来对这些元素进行说明和注释  
  作用分类：
  编写文档：通过代码的标识的元数据doc文档（api文档）  
  代码分析：通过代码里标识的元数据对代码进行分析（使用反射） 
  编译检查：通过代码里标识的元数据让编译器能够实现基本的编译检查   
  使用方式 ：@注解名称    
 ### JDK内置注解  
  @Override：检测被该注解标注的方法是否是
  @Deeprecated：将该注解标注的内容，已过时  
  @SuppressWarnings：压制警告的 使用该注解需要传递参数一般是all（字符串类型）
### 自定义注解    
  #### 编译命令javac反编译命令javap  
  格式： 
  #### 元注解  
  #### public @interface 注解名称{}  
  本质：extends java.lang.anntation.Annontion
就是一个继承了annontion类的接口  
  #### 属性  
  接口中定义的内容即成员方法  
  要求：实行的返回值类型  
  1.基本数据类型  
  2.String
  3.枚举  
  4.注解  
  5.以上类型的数组
  不能自定义类
  2.定义了属性，使用时需要给属性赋值
  1.在注解中可以用defalute来设置默认注解属性   
  2.如果只有一个属性需要复制，并且属性的名称是value，则value可以生省略，定义值即可   
  3.数组赋值时用大括号包裹，如果数组只有一个值则打括号可以省略 

  ### 元注解  
  来描述注解的注解  
  jdk定义好的  
  *@Target：描述注解能够作用的位置 (TYPE表示作用于类上,Method表示作用域方法上,FIELD作用于成员变量上)   
  *Retention：描述注解被保留的阶段  (被保留的阶段)(对应于到底是保留到source,class,runtime三个阶段，一般自定义注解只作用
  于runtime，class时当前描述的注解会保留到class字节码文件中，并被jvm读取)  

  *@Doucument：描述注解是否被抽取到api文档中  
  *@Inherited：描述注解是否被子类继承  （如果加入回子类会自动继承）

通过注解来生成框架模型  
  不需要通过Properties通过加载进内存获取字符流，可以通过注解的方式进行配置   
  首先配置自定注解  
  1.获取class字节码文件
  2.拿到字节码文件上方的注解，通过class对象的getAnnotation方法拿到指定的注解对象，同时该方法会在内存中生成该注解类的子类的实现对象  
  3.调用对象的抽象方法获取返回值  
  4.通过classforName方法将该类加载到内存
  5.通过反射的构造方法下的newInstance生成新的该类对象  
  6.通过getmethod方法获取该方法
  7.通过method类中的invoke（）方法将对象放入后实现
  代码案例  
  ``` java
  @Pro(className = "ReflectText.Student",methodName = "sleep")
public class annotation {
    public static void main(String[] args) throws Exception {
        Class<annotation> clss = annotation.class;
        Pro pp = clss.getAnnotation(Pro.class);//获取该类上定义的注解类型PRO该语句其实就是在内存中生成了注解接口的子类实现对象
        //调用注解对象中定义的抽象方法，获取返回值
        String className = pp.className();
        String methodName = pp.methodName();
        Class cls = Class.forName(className);
        Object obj = cls.getDeclaredConstructor().newInstance();
        Method method = cls.getMethod(methodName);
        method.invoke(obj);
    }
}
```
## mysql
	my.ini配置  
	`[client]
# 设置mysql客户端默认字符集
default-character-set=utf8
[mysqld]
#设置3306端口
port = 3306
# 设置mysql的安装目录 这块换成自己解压的路径
basedir=D:\\mysql\\mysql-5.7.13-winx64
# 允许最大连接数
max_connections=200
# 服务端使用的字符集默认为8比特编码的latin1字符集
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB`
安装详情见网上 
	原因：在my.ini中加入skip-grant-tables在mysql8.0中已失效。Mysql 8.X的方法是在命令行中使用`mysqld --console --skip-grant-tables --shared-memory`启动服务器然后root就可以免密登录了（需要开2个CMD窗口）。
	该窗口使用mysql -uroot -p回车登录即可,`UPDATE mysql.user SET authentication_string='' WHERE user='root' and host='localhost';`再次登录就可以无密码登录
启动mysql服务  `net start mysql`
	sql登录 `mysql -uroot root-p`
       mysql更改密码`alter user 'root'@'localhost' identified by '1234567';`
        离开:`quit`
mysql语句:quit离开命令
操纵别的主机:-hip -uroot -proot或者--hostip --user-root --password-密码
mysql安装目录结构:    
bin放的2进制可执行文件   
date放的记录信息    
include 放的c的头文件  
share放的错误信息       
my.ini放的配置文件   
frm文件放的数据表的文件
sql structured query lanuguage  
定义了所以操作所有关系型数据库的规则每一种数据库操作方式不一定一样,存在方言情况
	
sql通用语句:  
show datebase;
数据库并不区分大小写 
注释内容 --必须加空格  #可以不加空格多行注释/**/   
### sql分类
  1.DDL数据定义语言,用来定义数据库对象:数据库,表,列等 create,drop,alter等  
  2.DML数据操作语言,用来对数据库中表的数据进行增删改查,关键字insert,delet,update    
  3.DQL数据库查询语言,用来查询数据库表中的记录,关键字:select,where等  
  4.DCL数据库控制语言,用来定义数据库访问权限的安全级别,即创建用户关键字,CRANT,REVOKE  
![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/mysql%E5%85%B3%E7%B3%BB%E5%9B%BE.png)
	
DateBase:
information:描述mysql信息的,并不是真正的表,是视图  
mysql:核心数据库,存放的表  
performance:提升性能  
test:一张表都没有,空的数据库  
查看某个数据库的创建 show create database   
#### create   
创建数据库  create database 名称;也可以判断if not exist在创建  
同时创建的也可以不是utf8的 用 creat database db3 character set gbk;来创建gbk的
#### 查询  
  查询所有数据库 show database;  
#### 修改 
  修改数据库字符集 alter database 数据库名称 charater set 字符集;  
#### 删除
  drop database 数据库名称; 用if exists判断是否存在存在再删出  
使用数据库 查询当前使用数据库的名称  select database()  
#### 使用数据库 
  use 数据库名称;  

### DDL操作表  
  查询表名称  show tables;  
  查询表的结构  desc 表名;  
  复制表,create table stu like student; 创建一个像谁的表   
创建:create 表名();括号内写的是列明  
    `create table student(
     id int,   
     name varchar,
     age int,
     score double(4,1),
     birthdat date,
     insert_time  timestamp
	)`
#### sql的数据类型  
1.int类型 表示整数  
2.小数类型 float单精度,double类型双精度例如  
score double(5,2)(表示总共5为,小数后面保留2为有效数字)   
3.date日期类型只包含年月日  
 yyyy-MM-dd  
4.datetime 包含年月日时分秒  
yyyy-MM-dd-HH:mm:ss  
5.时间戳类型timestamp  类型与datetime一致如果不给这个字段赋值,或者为空,默认为当前系统时间自动赋值   
6.varchar:字符串  name varchar(20) 表示最大20个字符  
7.BLOB类型 字节为单位存放大型东西  
8.CLOB  
9.BINARY(M)存放二进制东西M为支持的字节长度  
7-9一般很少用大型文件一般存在磁盘上将路径存入数据库通过io流拿出即可
#### 删除表  
drop table if exists 表明;  
#### 修改表  
1.修改表名  
`alter table 表名 rename to 新表名`  
2.修改表的字符集  
show create table 名称;   
alter table 表名 character set 字符集名称;  
3.添加一列   
alter table 表名 add 列名  数据类型  ;  
4.修改列名称  类型  
`alter table 表名 change 列名 新列名 类型;`即改名字又该又该类型  
`alter table stu modify 表名  类型名` 只改类型   
5.删除列  
`alter table stu drop 列名;`

### DML
1.添加数据  
`insert into 表名 （列明1，列明2，列明3）values （值1，值2，值3）`
需要查询时可以  
`select * from stu`
注意：列名和值要一一对应，若表名后面不跟列明则表示所有数据，出数字类型外其他都要加引号   
2.删除数据   
`delete from 表名[where 条件]`（当条件满足时从表中删除数据） 
注意：如果没有条件就删除整个表的所有记录   
也可用truncate table stu; 删除表，然后再创建一个空表相当于 drop table 和create table的综合
3.修改数据  
`update 表名 set 列明1 =值 1 [where 条件]` 
注意事项：如果不加任何条件，会将表中所有记录全部修改  

### DQL 查  
DQL查询语句  
1.排序查询  
* 排序语法  
	`order by 排序字段1，排序字段2 排序方式1，排序方式2`  
	 注意：如果不写排序方式默认为升序序列  ASE升序默认 DESC降序  
      排序字段的先后表明了排序的优先顺序，优先级越高约在前面
	`SELECT * FROM stu ORDER BY id,age DESC  ;`
	

2.聚合查询  
将一列数据作为整体，进行纵向计算  
1.count 计算个数  `selet count（ifNULL(列名,0)）from 表名`  如果不为0
2.max计算最大值  `selet max（ifNULL(列名,0)）from 表名`
3.min计算最小值  
4sum计算和  
5avge 平均值  
所有聚合函数回排除null值 所以两种解决方法 1.可以加上 if语句将null替换城0  2.不计算非空列
	
3.分组查询   
`select 组 或者聚合函数 from 表名 group by 分组字段`  group by相当于分组可以再前面加where 条件或者用having都可以 
#### where和having区别  
where在分组之前，如果不满足条件不参与分组 
having 在分组之后限定，如果不满足条件不会被查询  
where不能用于判断聚合函数，而having可以用来判断聚合函数 

列子`SELECT id,AVG(age) FROM stu GROUP BY id;`
注意：分组之后查询的字段：分组字段，或者聚合函数 
4.分页查询 
语法：limit 开始的索引，每页查询的条数；  
公式：开始的索引 = （当前页码 - 1 ）*每页显示的条数
`SELECT * FROM stu LIMIT 6,3;`
注意：分页操作是方言，是mysql的一个方言，limit只能再mysql用，并不能再其他上用

5.基础查询
select * from 表名；查全表  
综合查询  select+（字段名多个字段）+from+（表名，可以多个表以逗号分隔）+where+条件+group by（分组字段）+having+分组之后的条件限定+order by（排序方式）+limit（分页限定）  
1.多个字段查询你  
`SELECT NAME,age FROM stu;`--查名字和年龄
	
2.去重    
在字段前加入 distinct 来取宠 
`SELECT NAME,age FROM stu;`
如果有多组去重，必须保持两个列的结果全部一样才可以达到
3.计算列  
 可以把两个列直接相加生成新的列 与聚合函数不太一样  
`SELECT NAME,MATH,ENGLIST,MATH+ENGLIST FROM STU;`
4.起别名   
AS + 别名 
 `SELECT NAME,MATH,ENGLIST,MATH+ENGLIST 总分 FROM STU;`
`SELECT NAME,MATH,ENGLIST,MATH+ENGLIST FROM STU;`

6.条件查询  
where子句后面跟条件
sql等于就是= ，不等号可以用<>来表示
注意null不能用等号，需要用is null
运算符：between...and   `SELECT * FROM stu WHERE age BETWEEN 20 AND 30 ORDER BY age;`年龄20-30查询
       in  只要列表又就可以，类似于or `SELECT * FROM stu WHERE age IN(22,25,30);`
       like 模糊查询 （比如姓马的） 
       like占位符_下划线：单个任意字符  
       %百分号：多个任意字符
        `SELECT * FROM stu WHERE age LIKE "3_";`查询30岁以上的
	`SELECT * FROM stu WHERE NAME LIKE "___";`查询名字三个字的
	%马%可以查到所有包含马的


###约束
概念：对表中的数据进行限定，保证数据的正确性、有效性、完整性
分类：  
    主键约束：primary key，   
     注意：含义非空并且唯一，并且一张表只能有一个字段是主键，主键就是一张表中记录的唯一标识（一般都是id）
      在创建表时添加  
      创建完添加  `ALTER TABLE iphone MODIFY phone_number VARCHAR(13) PRIMARY KEY;`
      删除主键 `alter table 表名 drop primary key;`
    自动增长：如果某一列时数值类型的，使用auto_increment 可以来完成值的自动增长 ，一般配合int类型的主键来用 
    必须在主键会根据上一条记录再自增  
    删除自动增长`alter table 表名 modify 列名 类型`因为主键无法这样删除所以相当于删了自动增长
	
    非空约束：not null，
    在创建表时候，可加not null
    再创建后添加`ALTER TABLE stu MODIFY NAME VARBINARY(32) NOT NULL;`   
    删除约束`ALTER TABLE stu MODIFY NAME VARBINARY(32) ;`   
    
    唯一约束：unique，  null还是可以多个     
    创建表时，添加唯一约束创建时删除，    
    删除唯一约束 不能用 modify只能用drop index`ALTER TABLE iphone DROP INDEX phone_number; `   
    创建后添加唯一约束 `ALTER TABLE iphone MODIFY phone_number VARCHAR(13) UNIQUE;`  
    
    外键约束：foreign key（多表应用）
    添加表时候可以添加外键  
    注意外键必须被关联到主键的列，如果不是会报错
    `create table（
    ...
        外键列
        constraint 外键名称 foreign （外键列名） references 主要名称
    ）;`
     删除外键名称：`alter table 表名 drop foreign key 外键名称`
     创建后添加`ALTER TABLE stu ADD CONSTRAINT 外键名字（随意起） FOREIGN KEY (主建列名) REFERENCES 关联表（列名）;`    
     ##### 外键的级联操作 
        其中如果出现一对无穷表示一对多关系  
     普通改法：：外键绑定后不可以直接改数据，应为又可能关联表并没有值，所以需要设置为null再从null改为需要的值
     级联更新：添加外键并且设置级联更新    
     先删除`ALTER TABLE 表名 DROP FOREIGN KEY 外键名;`
     创建外键是添加级联更新： `ALTER TABLE 表名 ADD CONSTRAINT stu_iphone（外键名） FOREIGN KEY (id（列名）) REFERENCES iphone（级联表名）(id（级联列名）) ON UPDATE CASCADE; `
     同理也可以设置级联删除： 只需再后面加上 on delete cascade    
     级联更新：on update cascade
### 多表关系  
#### 数据库设计  
   1.多表之间的关系  
    一对一关系如 人和身份证  
     解决方法：再任何一方添加外键即可，可以在任意一方添加外键指向另一方的主键即可，并且要保证unique唯一，一般一对一也可以和表，不用再管这写其他的
   2.一对多或者多对一  （解决再多的一方建立外键，指向一的一方的主键）
    例如部门和员工，一个部门有多个员工，一个员工只能对应一个部门  
   3.多对多关系  比如学生和课程 一个学生可以选择多门课程，反之亦然   
    解决方案    
      新建一个表获取双方的主键，多对多的关系一定要借助中间表，至少包含两个字段，分别指向两张表的主键，这两个字段作为第三张表的外键  
   2.数据库设计的范式
	
	
###范式设计数据库   
 概念：设计数据库时需要遵守的规则，各种范式呈递次规范（要满足后面的范式首席得满足前面的范式），越高的范式数据冗余越小，目前有六种范式 第一、二、三 范式、
 巴斯克范式  第四、第五  
  第一范式：每一列都是不可分割的原子项  
  第二范式：再一的基础上非码属性必须完全依赖于码  
     概念：a---->b如果通过 a属性的值，可以唯一确定b属性的值，则称b依赖于a  
      例如身份证号可确定一个人 ，则说人依赖于身份证号  
      属性组：a和b同时组成一个属性，则认为这个属性叫做属性组
      完全函数依赖
	 a-----b 如果a时一个属性组，则b属性值的确定要依赖a属性组中所有的属性值则称b完全依赖于a  
      例如学号和课程名称 可以确定一个分数则说 分数完全依赖于学号和课程名称  
      传递依赖  
      a--->b ,b---->c则说明c传递依赖于a，也称为a被c传递依赖  
      码：如果在一张表上，一个属性或者属性组，被其他所有属性完全依赖，则称这个属性为该表的码  
      主属性：码属性组中的所有属性   
      非主属性：出码属性组的属性  
  第三范式：再第二范式的基础上，任何非主属性不依赖于其他非主属性  
	
	
### 数据库的备份及还原
备份：命令行方式或者图形画界面  
命令行：mysqldump -u用户名 -p 密码 》 保存的路径  
	
       还原：登录，创建，使用执行文件。 source文件路径

### 多表查询    	
查询语法  
    sleect 列名 列表   from 表名列表  where
    笛卡尔集 逗号查询可出现组合情况  
    多表查询分类：  
   #### 1.内敛查询    
    隐式内连查询：用where消除无用数据 
    `select * from emp,dept where emp.id=dept.id;`
        `SELECT emp.name,salary,dept.name FROM emp,dept WHERE emp.id=dept.id;`  
    同理可以用起别名的方法  
    
    `SELECT 
    t1.name,salary,t2.name
    FROM 
    emp t1 ,dept t2
    WHERE
    t1.id = t2.id;` 
       
    显式内连接： 语法  
    `select 字段列表 from 表名1 ineer ioin 表名2  on 条件`  
    
    ` SELECT  t1.id, t2.name FROM emp t1 INNER JOIN dept t2 ON t1.id = t2.id;`
    内连接查询总结： 
      1.从奶协表查询数据  
      2.条件是什么  
      3.查询哪些字段


	
	
   #### 2.外连接查询    
	1.左外链接查询的是左表所有数据以及其交集部分   
	 语法：
	`select 字段列表 from 表1 left[outer] join 表2 on 条件`
	2.右外链接   
	    右外链接同理，查询右表所有记，将left 换成right即可  left左边是左表
   #### 3.子查询   
        查询中嵌套查询，并且称嵌套的查询为子查询    
        例如查询工资最高的人，这时候要先查最高是多少，再判断谁是这个   
    ` SELECT NAME FROM emp WHERE salary=(SELECT MAX(salary) FROM emp);`   
       不同种情况    
    1.子查询结果是单行单列      
        * 子查询可以作为条件，使用运算符进行判断  例如使用in这种集合来判断   
    
    2.子查询结果是多行的单列的   
         子查询的结果有两个可以用 in等运算符包含
    
    3.子查询的结果时多行多列
     *查询工资大于1900的所有员工名字俱乐部，和工资  
        将一个表作为虚拟秒（）用来查询
    `SELECT t1.name,t2.name,salary FROM dept t1,(SELECT * FROM emp WHERE salary>1900) t2 WHERE t1.id = t2.id;`
### 事物     

1.事物的基本介绍    
 概念： 如果一个包含多个步骤的业务操作，被事务管理，那么这些操作要么同时成功或者同时失败
 操作： 1.开启事物  start transaction;    
	2.回滚  rollback;   
	3.提交  commit;     
	4.mysql数据库中事物默认自动提交  
	 *一层dml增删改语句会自动进行提交  
	 事物提交两种方式  
	   自动提交：mysql中任何dml语句都会引起事物的提交  
	   手动提交：修改事物的默认提交方式  
	   select @@autocommit； 1代表自动提交0代表手动提交  
	   修改默认的提交方式  set @@autocommit =0 这时候就变成了手动提交，即不写update语句就不会生效  
         oravle数据库时手动提交的，即无法自动提交
2.事物的四大特征  
   1.原子性：事物是原子性的
   2.持久性：当事务提交或回滚后，数据库会持久化的保存数据  
   3.隔离性：多个事务之间相互独立  
   4.一致性：实务操作前后，数据总量不变  例如张三李四有20张三给李四10块他俩的总量还是不变的
3.事物的隔离级别    
    概念：多个事物之间隔离的，相互独立的。但如果多个事物操作同一批数据，则会引发一些问题，设置不同的隔离级别可以解决这些问题 。
    存在问题：  
        脏读：一个事务读取到另一个事务中没有提交的数据  
        不可重复读（虚读）在同一个事物中读取到的数据不一样  比如a开事物转账 不提交 ，b第一次查没变化，再a提交后再查发生了变化  
        幻读：一个事物操作数据表所有记录，另一个事物添加了一条数据，则第一个事物查询不到自己的修改  
    隔离级别：
       隔离级别从小大大安全性越来越高，但效率越来越低
       read uncommit ：读未提交  
	*产生的问题：（若设置隔离级别为这个）三个问题都有可能发生  
       read commit ：读已提交    oracle数据库  当对方提交后就可一看到更改的数据
       * 产生的问题不可重复读，欢读  
       repeatable read ：可重复读  mysql数据库就是这样只有当自己也提交后才能看到别的事物更改的情况
	*产生的问题：幻读  
       serializable 串行化  锁表的动作，类似于pv操作，当前再用时其他不能用，只有当释放资源后其他才能用
        *可以解决所有问题  
      数据库查询隔离级别：  select @@tx_isolation 8.0版本已经弃用了 新的为`SELECT  @@transaction_isolation;`
      数据库设置隔离级别： set global transaction isolation level 所需级别;
### DCL	
管理用户授权   
 1.管理用户   
 添加用户  
`create user ’用户名‘@”主机名 indentified by 密码`  
例如  
`
CREATE USER 'lyc'@'localhost' IDENTIFIED BY '1234567';
CREATE USER 'public'@'%' IDENTIFIED BY '1234567';`
其中'%'表示主机通配符任何主机都可以，网络方面可以填写ip地址
 删除用户     
	
drop user '用户名'@'主机名字'；
 修改用户密码   
update user set password = password('密码') where user ="用户名";  
或者  
set password for "用户名"@"主机名" = password（“密码”）；
	
查询用户    
 首先的切换到mysql数据库  
`use mysql;`  
*查询user表 `select * from user`
 2.对用户授权   
查询权限   
show gants for '用户名'@'主机名';  
授予权限  
grant 权限列表 on 数据库名.表名 to "用户名"@'主机名'
例子`GRANT SELECT,INSERT,UPDATE,CREATE,DELETE ON db1.account TO 'lyc'@'localhost';`授予lyc查询插入更新    
创建删除db1数据库中account表的权限  
如果想赋予所有权限  
`grant all on *.* to 名字@主机名`
撤销权限  
revoke 权限列表 on 数据库.表名 from '用户名'@'主机名'
	
	
## JDBC  
###  1.jdbc基本概念      
概念  ：java DataBase Connectivity java 用java操作数据库 
等于是用统一的一套java代码可以操作所用的数据型关系 
本质:其实时官方sun公司定义的一套操作所有关系型数据库的规则,即接口,各个数据库厂商去实现这套接口,提供数据库驱动jar包,我们可以  
使用这套接口(jdbc)编程,真正执行的时驱动jar包中的实现类   
![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/jdbc%E6%A6%82%E5%BF%B5.png)    
	

###  2.快速入门    
* 步骤:
	1.导入驱动jar包     
	** 复制到目录下  
   右键 add as libaray
	2.注册驱动  
	3.获取数据库链接对象 connection对象  
	4.定义sql语句  
	5.获取执行sql语句的对象 Statement  
	6.执行sql,接受返回结果   
	7.处理结果  
	8.释放资源
	
	
	
###  3.对jdbc中各个接口和类的详解  
1.DriverManager :驱动管理对象   
用于管理一组jdbc驱动程序的基本服务   
功能:注册驱动,获取数据库连接,将他加载进内存,因为存在静态代码块所以可以自动执行,也可以直接new DriverManager类调用registerDriver方法来注册
其中registerDrivcer需要一个Driver类的参数,mysql5之后的驱动jar包可以省略
DriverManager有getconnection方法可以连接数据库"jdbc:mysql://localhost:3306/db1"   如果本机地址是域名可不写
	
	
2.Connection:数据库连接对象  
功能：  1.获取执行sql的对象
        createstatement（）方法返回一个statement类的对象
        preparestatement（string sql）
	2.管理事物   
         *开启事务：setAutocommit（boolean autoCommit）调用该方法设置参数为false开启事务
	 *回滚事物 rollback（）
	 *提交事务 commit方法提交事物
	
	
3.Statement:执行sql对象  
  用于执行静态（里面参数给定值）sql语句并返回其生成结果的对象，而perparestatement是动态sql语句
	*1.boolean execute（string sql） 可以执行任意的sql语句 ture如果第一个结果是一个resultset对象，false如果是更新计数或没成功  
	*2. int executeUpadte(String sql) 执行DML和DDl  返回值是受影响的行数，可以通过返回值判断Dml语句是否成功>0成功
	*如果执行dml语句是没有返回的
	
	
	
	
	
	
4.ResultSet:结果集对象  resultset本身就是封装查询结果的情况
	*1.executeQuery（String sql）执行Dql语句（select）语句，返回的是结果集对象    
	*游标概念返回的结果集对象有游标默认指向0层数据再第一层需要用next方法向下移动一行
	*getXxx获取数据类型（xxx表示类型）其中get方法还需要参数参数是获取那一列  
	    1.int类型表示列的编号从1开始  
	    2.string类型表示列名
      DQL查询代码
	``` java
  public static void main(String[] args) {
        Connection ctn = null;
        Statement sttm = null;
        ResultSet res = null;
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");//加载类进内存执行方法
            ctn = DriverManager.getConnection("jdbc:mysql://localhost:3306/db1", "root", "1234567");
            sttm = ctn.createStatement();
            String sql = "select * from emp ORDER BY id ";//排序查询sql表
            res = sttm.executeQuery(sql);
            while (res.next()){
                int id =res.getInt("id");
                String name = res.getString("name");
                String sex = res.getString("sex");
                int salary = res.getInt("salary");
                System.out.println(id+"  "+name+"  "+sex+"  "+salary);
            }
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        } catch (SQLException throwables) {
            throwables.printStackTrace();
        }finally {
            try {
                ctn.close();
                sttm.close();
                res.close();
            } catch (SQLException throwables) {
                throwables.printStackTrace();
            }
        }
    } 
 ```
    一般这种可以封装为泛型类然后继承object类，用方法来引入增加可复用性
	ResultSetMetaData rsmt=rs.getMetaData();

得到结果集(rs)的结构信息，比如字段数、字段名等。

使用rs.getMetaData().getTableName(1))就可以返回表名


rs.getMetaData().getColumnCount()可以获得列数
#### jdbc工具类  
1.抽取注册驱动 
2.抽取一个方法链接   
3.抽取方法释放资源

获取当前路径下的文件方式 --->classLoader可以加载字节码文件进内存，同时也可以获取src文件下的路径 
``` java   
  ClassLoader classLoader = util.class.getClassLoader();
            URL resource = classLoader.getResource("jdbc.properties");//统一资源定位符
            String path = resource.getPath();           
	    url = pro.getProperty("url");
            System.out.println(resource);
            user = pro.getProperty("user");
            password = pro.getProperty("password");
            driver = pro.getProperty("driver");
  
```
classloader类中有getResource方法返回URL对象，通过url对象的getpath方法可以进行绝对定位   
其中pro对象的put方法可以将值作为map数组存放如pro对象，而getproperty方法可以根据键找值
	
#### 登录  
再jdbc判断登录密码时要进行字符串拼接其中 username = '"+username+"'注意两端的单引号
	
	
5.PreparedStatement:statement对象的子类 功能更强大是statement的子接口
 1.SQL注入问题，拼接sql时有sql关键字参与拼接会造成问题     
1.输入用户随便，输入密码学一个恒等式，可以导致这个这个登录成功，会影响使用  
2.预编译sql：参数使用？作为占位符   
步骤：再定义sql时候参数使用sql的参数用？作为占位符
      connection中需要调用getpreparedstatement方法需要传递sql参数  
      给？赋值：方法setXxx（参数1，参数2）其中参数1是？的位置，参数二是参数的值  
      而再执行sql时候preparedstatement是不需要传递sql语句的
案列
	``` java
  public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("请输入账号");
        String s = scanner.nextLine();
        Scanner scn = new Scanner(System.in);
        System.out.println("请输入密码");
        String s1 = scn.nextLine();
        boolean log = new login().log(s,s1);
        if(log)
            System.out.println("登陆成功");
        else
            System.out.println("登陆失败");

    }


    /**
     * 登录
     */
    public boolean log(String username,String password){
        if(username==null||password==null){
            return false;
        }
        Connection con = null;
        PreparedStatement pre = null;
        ResultSet res  = null;
        try {
            con = util.getConnection();
            String sql = "select * from login where username = ?and password = ?";
            pre = con.prepareStatement(sql);
            pre.setString(1,username);
            pre.setString(2,password);
            res = pre.executeQuery();
            return res.next();
        } catch (SQLException throwables) {
            throwables.printStackTrace();
        }
        finally {
            util.close(res,pre,con);
        }
        return false;
    }
  ```
	

### jdbc控制事务
  事务是一个包含多个步骤的业务操作，如果被事务管理则多个事务要么成功要么失败   
  操作：
	1.开启事务  setAUtoCommit（boolean autoCommit）调用该方法设置参数为false开启事务   
	2.提交事务  commit（）  
	3.回滚事务 rollback（）  
       *在操作开始的时候开启事务，再结束时候提交事务，再catch中回滚事务
	
###数据库连接池  DataSource接口
  DataSource接口：基本实现生成标准的Connection对象  
   连接池实现生成自动参与连接池的connection对象，分布式事务实现，生成可用于分布式事务的Connection对象，并且几乎总是参与连接池
   就是容器存放数据库连接的容器  
 *当系统初始化后，容器被创建，容器中会申请一些连接对象，当用户来访问数据库时，从容器中获取连接对象，用户访问完后会归还容器   
 好处：节约资源，用户访问高效  
 方法：connection对象下的getconnection方法返回一个数据库连接池  
 C3P0：数据库连接池  
Druid：数据库连接池技术，由阿里巴巴提供  
以上两个均实现了DataSource接口
连接池需要做的事：getConnection和归还链接，并且如果对象从连接池中获取，那么调用close方法将不会关闭而是归还，不要忘记导入数据库驱动jar
1.导入jar包  
2.定义配置文件    

``` java
  driverClassName = com.mysql.cj.jdbc.Driver
url = jdbc:mysql://localhost:3306/db1
username = root
password = 1234567
initialSize = 5
maxActive = 10
maxWait = 3000
```  
	  
3.加载配置文件  
4.获取数据库连接池对象通过工厂函数`DruidDataSourceFactory`类的`createDataSource`静态方法获取
	
2.定义工具类   
提供方法  
1.通过数据库连接池获取链接   
2.提供静态代码块加载配置文件，初始化连接池对象  
3.获取连接池的方法   
工具类列子应用    

	
``` java
        Connection con = poolutils.getconnection();
        String sql = "INSERT INTO account VALUES(NULL,?,?)";
        PreparedStatement pstm = null;
        ResultSet res = null;
        try {
            pstm = con.prepareStatement(sql);
            pstm.setString(1,"刘六");
            pstm.setDouble(2,1992);
            int count = pstm.executeUpdate();
            if(count>0){
                System.out.println("添加成功");
                String sql1 = "SELECT NAME,balance FROM account WHERE NAME = ? GROUP BY NAME,balance";
                pstm = con.prepareStatement(sql1);
                pstm.setString(1,"刘六");
                res = pstm.executeQuery();
                while(res.next()){
                    System.out.println(res.getString("name")+"  "+res.getDouble("balance"));
                }
            }else System.out.println("添加失败");
        } catch (SQLException throwables) {
            throwables.printStackTrace();
        }finally {
            poolutils.close(pstm,con,res);
        }
    }
  ```
	
	
	
	
	
	

### Spring JDBC：JDBC Template
1.通过spring封装的jdbc实现基本操作  
导入jar包    
`JdbcTemplate tem = new JdbcTemplate(datasource对象)`
也就是要返回一个数据库连接池  
调用jdbctemplate的方法完成CRUD操作  
*update（）方法执行DML语句增删改  
*queryForMap（）查询结果将结果集封装为map集合  注意结果集只能是1   
*queryForList()查询结果集封装为list集合  将map集合装入list中  
*query（）将结果封装为JavaBean对象  需要传入rowmapper对象，改接口可以自己实现也可以用别人的  
`new RowMapper<E>(){}`   
官方的只需要 传入一个`new beanPropertyRowMapper<E>(E.class)`需要传入泛型和泛型的字节码文件  
同时再自己定义类时候一定要用包装类不要直接用基本类，因为基本类不接受null而包装类可以
*queryForObject()：查询结果封装为对象用于查询聚合函数的  需要用传入返回值类型的字节码文件
	
	


### XML  
#### 可扩展性：标签都是自定义的  
#### 功能
#### html与XMl  
 先开始与html竞争后面转向properties竞争
 *w3c万  
文档声明<?xml 属性列表 ?>
属性列表：版本号 version  
         编码方式：encoding 对于浏览器解码方式 本地是什么就是什么
	 是否独立 standalone "yes"or"no" 是否依赖其他文件  
	 指令：可结合css做这方面的应用 xml-stylesheet  
	 规则：名称不能包含空格必须要有一个跟标签，属性必须用引号引起来，并且xml的标签区分大小写  
	 id属性值是唯一的  
	 约束 ：说明文档，规定xml文档的书写规则  
dtd和schema：约束文档  （+表示一次或者多次*表示0此或者多次）  
dtd文档：通过<!element>约束标签
 内部文档dtd：写在xml内部  
 <!DOCTYPE students{
  约束内容  
  <!ELEMENT> stundets(student+)>
  <!ELEMENT student(name,age,sex)>
  <!ATTLIST student number ID #REQUIRED>
}>
 外部：将约束规则卸载外都  
 外部分为两种本地和网络：<!DOCTYPE 跟标签名称 system "dtd文件的位置">  
 网络上的:<!Doctype 跟标签 public "dtd文件名字" “dtd文件的位置URL>
Schema:
引入文档：1. 先要写跟标签引入xsi前缀  
	 2. 引入xsd文件命名空间  
	 3. 为每一个xsd约束声明一个前缀，作为标识其前缀是因为有可能引用多个文档   
解析：操作xml文档，将文档中的数据读取到内存中  
      写入：将内存中的数据保存
解析xml的方式  
1.DOM将标记语言文档加载进内存，形成一颗dom树所以可以同过document.getelementByid（）这种   
同时可以对节点进行crud。但有一定缺点，dom一次加载进内存形成的dom树可能比源文件大一万倍   
2.sax思想：逐行读取，基于事件驱动  
优点：在内存中基本只有一行，占内存小    
缺点：无法写人，读取一行就释放一行，所以不能增删改   
xml的解析器   
    1.JAXP sun公司提供的解析器，支持dom和sax的思想，但性能很低   
    2.DOM4J 基于dom思想实现的   
    3.Jsoup 基于java的html的解析器  
    4.PULL Android内部操作系统解析器，基于sax的   
	  
Jsoup入门：可用来做爬虫 
parse的重载可以放文件或者string甚至是url
	*步骤
	1.导入jar包  
	2.获取DOcument对象  
	3.获取对应的标签Element对象   
       解析就是加载文档进内存获取dom对象    
document对象：
element对象：元素对象   
node对象：节点对象  
	
XPath 再xml中查找的语言  
//s  查找s下所有元素  
	
### web服务器  
服务器：安装了服务器软件的计算机  
服务器软件：接受用户的请求，处理请求，做出响应  
web服务器软件：接受用户的请求，处理请求，做出响应  
常见的java相关的web服务软件   
webLogic：oracle公司，大型的JavaEE服务器，支持所有的JavaEE规范，收费的   
webSphere：IBM公司的，大型的JavaEE服务器，支持所有的JavaEE规范，收费的  
JBOss：JBOSS公司的大型javaEE服务器   
Tomcat：APache基金组织的，中小型JavaEE服务i其，仅仅支持少量的JavaEE规范


#### Tomcat  
bin目录：二进制的可执行文件   
config：配置文件    
lib：依赖jar包  
logs：日志文件，通过日志调控  
temp：临时文件  
webapps：存放web项目的  
  startup.bat批处理文件
简单部署：将项目打成一个war包再将war包部署到webapps下  
也可以用虚拟目录  
虚拟路径是项目的路径可以从配置地方设置虚拟目录
再serve文件下配置  再host标签体下配置  
<context docBase ="文件目录" path="/虚拟路径">  
或者再conf下的CataLina\locahost创建任意名称的xml文件  
文件中编写<Context docBase = ”路径“ >虚拟路径就是文件名称   
#### 静态项目与动态项目  
	静态页面就是设计者把页面上所有东西都设定好、做死了，然后放上去，不管是谁在任何时候看到的页面内容都是一样的，一成不变  
	动态页面的内容一般都是依靠服务器端的程序来生成的，不同人、不同时候访问页面，显示的内容都可能不同。网页设计者在写好服务器端  
	的页面程序后，不需要手工控制，  
	页面内容会按照页面程序的安排自动更改变换。
目录结构：  
java动态项目的目录结构  
目录的根目录  
    web-Inf目录  
     ----web.xml：web的核心配置文件  
     ----ckasses目录：放置字节码文件的目录  
     ----lib目录防止依赖的jar包

### servlet:概念运行在服务端的小程序   
本身就是一个接口，  
动态资源：逻辑性---代码来体现    
比如判断请求者是谁（没有主方法的java类，由tomcat执行，所以servlet就是对于于此的接口）  
servlet就是一个接口定义额java类被浏览器访问的规则
本身就是java定义的一个抽象接口  
#### 快速入门  ：
1.创建javaee项目  
2.定义一个类，实现servlet接口  
3.实现接口方法  
4.配置再web.xml中进行配置
``` XML
  <!--    配置servlet-->
    <servlet>
        <servlet-name>demo01</servlet-name>
        <servlet-class>com.example.servlet.servletdemo01<servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>demo01</servlet-name>
        <url-pattern>/demo01</url-pattern>
    </servlet-mapping>
```   
注意由于Tomcat10中的Servlet-api依赖包与Maven导入的Servlet4.0.1不兼容，所以只能取一个   
要么降级tomacat，要么将servlet依赖改为Timcat中的自带依赖，从库那里改正，删除maven的依赖  
#### servlet原理
servlet没有调用自己执行的原因：  
1.首先在服务器中定义了一个类，实现了一些方法  
2.又在webxml中配置了servlet文件，两个都在服务器中  
3.通过ip可以扎到注意，通过虚拟目录找到项目，又通过path找到资源，找有没有url-pattion与路径相符，再通过name找到名字，再通过名字找到全类名  
tomcat将全类名对应的字节码文件加载如内存，并且创建了对象，创建class。newInstance对象闯进新的对象，调用service方法，所以servlet的执行依赖于容器  
这个容器就是服务器  
		
		
---
![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/servlet%E5%AE%9E%E7%8E%B0%E5%8E%9F%E7%90%86.png)

#### Servlet的生命周期  
init方法：初始化方法，再servlet被创建时候执行，只会执行一次  
 * 原则上应该是第一次访问时候创建，也可以配置执行servlet的创建时机  
  再webxml中配置  
  <load-on-startup>当启动时后加载（当值为负数时，标识第一次访问被创建，为正就会在服务器启动时候创建）  
  init 方法只能执行一次说明，在内存中这个对象是单例的，只有一个，所以多个用户访问时候可能存在线程安全问题	
  解决方法：尽量不要再servlet中定义任何成员变量，即使定义了成员变量不要对其修改值
service方法:再每一次被访问是，执行，可执行多次  
destroy:再服务器关闭时候执行，也只执行一次    

#### 注解配置servlet  
在3.0之后支持注解配置  
@Webservlet  
value一般标识最重要的属性，当只有一个属性时候value又可以不写，所以直接@Webservlet（资源路径）
servlet的体系结构：  
  servket--接口  
     ||   
  子GenericServlet--抽象类   
     ||  
  孙HttpServlet --抽象类  

genericServlet是一个抽象类，对其他servlet中的方法进行空实现，预留了service接口   
而httpservlet是主要用与现阶段不用判断service中的get或post方法 只需要覆盖重写dopost和doget方法   
主要对http协议的封装   

Servket相关配置  
  1.urlpattern: Servlet访问路径  
   路径定义规则："/xxx","/xxx/xxx","*.do"正则表达式任意匹配    
	  
### HTTP  
hyper text transfer protocol  超文本传输协议  
分为客户端和服务器端，规定了请求和响应的格式及组成规则   
特点：基于tcp/ip协议的高级协议，需要三次握手来确保通常    
      默认端口号是80，及不需要再写端口号  
      基于请求响应的模型，及响应请求一一对应   
      无状态的：每次请求之间相互独立，不能相互交互   
	  
请求的格式：   
    1.请求行     
	*请求方式 请求url 请求协议/版本  
	  get /url HTTP/1.1  
	  http有7中请求方式
	 *get
	  请求参数再请求行出进行拼接   
	  请求的url长度有限制
	  不如post安全
	 *post  
	  请求参数在请求体中  
	  请求的url长度无限制  
	  相对于get安全
	
    2.请求头     
	1.*常见的请求头：user-agent浏览器告诉服务器浏览器的版本信息   
         可以在服务器中获取该头信息，解决浏览器的兼容性问题  
	2.accept可解释的相应格式  
	3.connection keepalive保持活跃   
	4.Referer告诉服务器当前请求来自于哪里   
	  作用：防盗和统计
	  
	  
    3.请求空行   就是空行用于分割post请求的请求头和请求体  
    4.请求体    

	  
	  
#### request对象   
1.tomcat服务器会根据请求url中的资源路径，创建对应的ServketDemo对象   
2.tomcat服务器会创建requset和response对象     
3.tomcat将request和response对象传递给service方法，并且调用service 方法   
5服务器在给浏览器做出相应之前，会从response对象中拿设置响应的消息   
	  
request继承的体系结构   
	  
servketReqest接口   
	 |   
	 |  
	 |   
httprequest --接口  
	 |   
	 |  
	 |  
由服务器实现上述接口   
	  
request功能：  
   1.获取请求消息数据   
	  *get /url  http/1.1    
	  获取请求方式 string 类型的getMethod  
	  获取虚拟目录：string类型的getcontextpath  （获取路径）  
	  获取servlet路径 、demo01  getservletPath   
	  获取get请求参数  getQueryString   
	  获取uri和url   getRequestURI 同理换成L即可  
	  获取http协议版本号  getProtocol   
	  获取客户ip地址  getremoteAddr
   2.获取请求头数据     
	  getHeader通过请求头的名称获取请求头的值   
	  getheadername获取与所有请求头的名称
   3.获取请求体数据  
	  获取字符流数据   
	  request.getReader（）是以字节流形式返回读取字节流即可  
   4.其他功能   
	  *获取请求参数  
	  1.getParameter（string name）根据参数名称获取参数值   
	  2.getParameterValues（string name）根据参数名获取参数值的数组   
	  3.Enumeration<string> getParameterNames（）获取所有参数名称    
	  4.getParameterMap（）获取所有参数的map集合   
``` java
    Map<String, String[]> map = request.getParameterMap();
 Set<Map.Entry<String, String[]>> en = map.entrySet();
 for (Iterator<Map.Entry<String, String[]>> iterator = en.iterator(); iterator.hasNext(); ) {
     Map.Entry<String, String[]> next =  iterator.next();
     System.out.println(next.getKey()+"------"+ Arrays.toString(next.getValue()));
     }
```
	  
	  *中文乱码问题当出现乱码时候树妖设置流的字符集将设字符集设置为utf-8通过setcharacterEncoding（）
 
	  *请求转发   
	  定义：理解为在服务器内部的资源跳转方式  
	  1.步骤通过request对象回去请求转发器对象 RequestDispatcher  通过getRequestDispatcher（string path）  
	  `request.getRequestDispatcher("/requestdemo1").forward(request,response);` 不需要加虚拟路径   
	  特点：  
	   1.浏览器地址不发生任何变化   
	   2.只能转发到当前服务器内部资源中  
	   3.转发只是一次请求   
	  
	  
	  *共享数据    
	  *域对象：一个有作用范围的对象，可以在范围内共享数据  
	  *request域：一次请求的域，一般用于请求转发的多个资源中共享数据  
	   方法： setAttribute（string name object obj）存储数据与vuex类似   
	  ---  

![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/%E5%85%B1%E4%BA%AB%E6%95%B0%E6%8D%AEsetattrubite%E5%8E%9F%E7%90%86.png)
	  object getattitude(string name)通过键获取值  
	  removeattribute(string name)通过键移除键值对
	  
	  *获取servletContext
          getServletContext（）  
	  
#### 登录逻辑   
![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/%E7%99%BB%E5%BD%95%E9%80%BB%E8%BE%91.png)
	
#### BeanUtils  
*用于封装javaBean的  
* javaBean就是标准的java类     
方法  
setProperty  
getProperty    
populate（object obj，map map）将map集合的键值对信息，封装到对应的JavaBean对象中也就是obj对象中
要求：1.必须有空构造  
      2.必须被public修饰   
      3.成员变量必须被private修饰   
      4.有setter和getter   
功能：封装数据  
属性：setter和getter方法截取后的产物 传递的其实是getter截取后的属性值，实际上时调用set方法   
	  
#### http响应消息   
响应消息：   
与请求对应   
	1.相应行    
	 格式组成：对应的协议及版本，响应的状态码   
	 响应状态码：就是服务器告诉客户端浏览器本次请求和相应的一个状态，都是3位数字  
	   1xx：服务器接收客户端消息但没有接受完 
	   2xx：请求成功   
	   3xx：重定向。代表的状态码位302也是资源跳转的一种方式比如a无法完成浏览器请求，告诉浏览器找c，这就是重定向过程  
	   图片数据缓存到本地，服务器告诉浏览器访问缓存代码位304。  
	   4xx：代表发客户端出现错误，路径写错，404 ,405没有正确的doxxx方法   
	   5xx：服务端错误  服务器出现异常例如报异常  
	2.响应头   
	  头名称：值  
	  常见的响应头：Content-type：服务器告诉客户端本次响应体数据格式及编码格式   
	               Content-disposition：服务器告诉客户端以什么格式打开响应体数据   
	  in-line:默认值，在当前页面打开   
	  attachement；filename-xxx：以附件形式打开响应体
	3.响应空格   
	4.响应体  
	  
#### Respons对象  
  功能设置响应消息  
     设置响应行  
     格式：HTTP/1.1 200
	 设置状态码：setStatus（int sc）；
     设置响应头  
	  setHeader（string name，string value）  
     设置响应体：  
	 1.获取输出流  
	 2.使用输出流，将数据输出到客户端浏览器  
	  获取输出流 ProintWriter getWriter（）  
	        在这里response获取的流不需要刷新，因为在完成一次相应后被销毁流会被关闭
	            ServletOutputStream getOutputStream（）    
	  使用输出流，将数据输出到客户端浏览器
  #### 重定向  
       两种方法  
	1.直接设置响应头和状态码  
  `response.setStatus(302);
   response.setHeader("location","/day4/responsedemo02");`    
	2.采用response的sendRedirect方法  
       特点：与转发不同转发地址栏路径不变，而重定向与其相反  
	  总结如下：地址栏改变   
	           可以访问其他服务器的资源  
	           是两次请求过程，不能用request共享
 #### 路径写法：相对路径和绝对路径
   绝对路径：通过绝对路径可以确定唯一资源  
   相对路径：找到访问当前资源和目标资源当前   
	  
#### 获取字符输出流   
response.getWriter()  
     字符集乱码问题，浏览器默认gbk或者gb2312，所以服务器在中文情况下获取出来的流对象是tomcat返回出来的  
  是iso编码，无法用gbk解码   
     `//获取流对象前先设置默认编码
        //response.setCharacterEncoding("utf-8");
        //告诉浏览器服务器发送的消息体数据的编码
        response.setHeader("content-type","text/html;charast=utf-8");
        //或者用response直接设hicontent-type  
        //获取流之前设置编码格式
        response.setContentType("text/html;charast=utf-8");
        PrintWriter pw = response.getWriter();
        pw.write("<h1>你好 response<h1>");`  
#### 获取字节输出流   
     response.getOutputStream()  
     一般来输出图片来进行。
   验证码输出：防止恶意表单注册
#### servletcontext获取  
  两种方式request获取，或者httpservlet获取   
  可以获取mimetype和realpath即响应头文件类型和真实路径  
	   response.setContentType("text/html;charast=utf-8");修改编码方式  
``` java 
    String filename = request.getParameter("filename");
        System.out.println(filename);
        //使用流将文件进内存
        String realPath = this.getServletContext().getRealPath("/image/" + filename);
        System.out.println(realPath);
        FileInputStream fil = new FileInputStream(realPath+".png");
        ServletOutputStream outputStream = response.getOutputStream();
        String mimeType = this.getServletContext().getMimeType(filename+".png");
        response.setContentType(mimeType);
        System.out.println(mimeType);
        response.setHeader("content-disposition","attachment;filename="+filename);
        byte[] buff = new byte[1024];
        int len = 0;
        while ((len = fil.read(buff))!=-1){
            outputStream.write(buff,0,len);
        }
        fil.close();
```  
 下载时候的中文名称问题可以通过修改编码等方式解决  
	 先获取user-agent请求头，使用工具类编码文件名即可   
	  
	  
	  
### 会话技术   
#### cookie   
	 会话： 客户端和浏览器之间进行通信，多次请求和多次响应   
	 一次会话：浏览器第一次给服务器资源发送请求，会话建立，直到有一方断开为止   
	 功能：在一次会话过程中多次请求间，共享数据：因为每次请求和响应都是独立的，为了解决不同请求之间通信问题，需要会话技术。  
	 客户端绘画技术：cookie   response.addcookie将new出来的cookie对象作为响应，同理reques.getcookie拿到cookie数组
	 服务端：session     
  cookie实现原理  
	 将响应头设置为set-cookiehttp响应头规定如果收到set-cookie投，会将cookie信息保存到浏览器上，第二次请求时会将数据带过去    
	 数据会被放到请求的消息头里，使用cookie消息头带过去（浏览器自动做），服务器可以通过request对象获取请求头相关信息（所有的都是在一次会话中进行的）   
  发送多个cookie也是可以的   
	  
#### cookie存在时间    
	1.默认情况关闭后及被销毁      
	2.持久化存储   
	  setMaxAge（int seconds）
	  1.正数：将cookie写到硬盘文件持续正数秒后删除      
	  2.负数：默认值  
	  3.0：删除cookie    
 cookie存储中文数据   
	 tomcat8之前不能直接存储中文，后面可以直接存储  
	 8之前需要转码，一般采用url编码  
 cookie范围  
	 假设在一个tomcat服务器中，部署了多个项目，cookie是否能共享？  
	 默认情况无法共享，setPath（string path）可以设置这个范围。如果没设置就是当前的虚拟目录
要注意导入的包，maven的包和tomcat不兼容   
 cookie特点和作用   
	1.cookie存储数据在客户端浏览器   
	2.浏览器对于单个cookie的大小有限制（4kb），以及对于同一个赢下的总cookie数量也有限制（20个）  
作用： 一般用于存取少量不太敏感的数据   
      在不登陆情况下对客户端身份进行识别

	  
### jsp java server pages  
    java服务器端页面，既可以定义html标签也可以写java代码  
    作用：简化书写   
	  
  原理：1服务器解析请求消息，找是否有index.jsp，找到了会将index.jsp转化位java，编译java生成字节码文件，有字节码文件提供访问  
  一个java类要想被外部访问只能是servlet，所以jsp本质也是servlet（重要 ）  
	  
  jsp脚本：声明java代码的方式
	  <% java代码 %>：转化成servlet后就在service方法中（可以写service方法的实现方法）   
	  <%! java代码%>:转化成servlet后就是成员变量或者成员方法   
          <%= java代码%>：输出语句会把写的java代码输出到页面上   
		  
 jsp:指令：作用配置jsp页面，导入资源文件  
     格式 ： <%@ 指令名称 属性名1=属性值1 属性名2=属性值2%>  
     分类   
     page：配置jsp页面      
	  contentType:等同于response.setContentType（）  
	  设置响应体的mime类型以及字符集   
          设置当前jsp页面的编码，（只能是高级的ide）   
	 pageEncoding设置编码格式   
	 buffer设置缓冲区大小  
	 import导包
     include：页面包含的导入页面的资源   
     taglib：导入资源 导入标签库
     errorPage = 错误后的跳转页面	  
     若标注了isErrorpage则可以使用exception对象
		  
		  	  
		  
		  
		  
		  
 jsp内置对象：及转换成servlet的情况下有servlet的内置对象，不用定义例如：out对象字符输出流    
  *pageContext    真实类型   PageContext     当前页面共享数据    
  *request        真实类型   HttpServletRequest  一次请求访问多个资源   
  *session        真实类型   HttpSession     一次会话的多个请求   
  *application    真实类型   ServletContext   所有用户键共享数据
  *page           真实类型   object           当前页面（servlet）对象   
  *out            真实类型   JspWriter        输出对象，输出到页面上  
  *config         真实类型   ServletConfig    servlet的配置对象   
  *exception      真实类型   Throwable        异常
		  
  out对象和response.getoutputstream获取的对象的区别  
   都有字符输出流且都有缓冲区，但tomcat总会先找response的缓冲区数据，在找out缓冲区数据   
  		  
		  
		  
		  
		  
		  
### session  
   概念：服务器端会话技术，在一次会话的多次请求间共享数据，，将数据保存在服务器的对象中 httpSession（也是域对象）   
   获取方式：
   `HttpSession session = request.getSession();
        session.setAttribute("msg","hellow");`  
  跟cookie一致，都是一次会话技术   
 原理：服务器如何确保在一次会话范围内多次获取的session是一个对象    
   session是依赖于cookie的，第一次获取session没有cookie，会在内存中创建一个新的session对象，将对象的id用map绑定后，  
   response设置cookie投携带jsessionid，第二次请求时会携带cookie，同过cookie找内存中有无满足携带信息的session，来确保  
   session是一个对象。   
		  
####  细节：当客户端关闭，服务器不关闭，两次获取session是否位同一个   
     默认不是，可以通过cookie的方法让cookie存放在硬盘上通过setMaxage来完成相同。   
	 new Cookie("JSESSIONID",session.getId)  
	
     2.客户端不关闭，服务器关闭后，两次获取的session是同一个码？    
      对象不是同一个，但是session的数据不能丢失  
	*session的钝化  
     *在服务器启动之前，将session对象系列化到硬盘上    
       *session的活化   
     *在服务器启动后，将session文件转化为内存中的session对象     
     通过以上两部来保证服务器的session不会丢失，可以通过tomcat实现，work文件存放转化成sevlet的jsp文件及session文件  
     session 失效时间  
  默认失效时间：30分钟 可以在web.xml文件中配置   
  也可以通过调用invalidate方法完成释放     

#### 特点   
		 
 1.session用于存储一次会话的多次请求数据，存在服务器     
 2.session可以存储任意类型，任意大小  
 3.与cookie区别，session在服务器端，大小没有限制，session相比cookie更安全   
		  
		  
		  
### MVC开发模式    
   1.jsp演变历史：早期只有servlet，只能使用response输出标签数据，较为麻烦，，后来有了jsp简化了Servlet的开发
   后来jsp过度使用，既写java又写html，有写js所以提出了MVC模式，再后来web开发借鉴MVC开发模式，使得程序设计更加合理   
   MVC：1.M：模型    业务操作，处理业务逻辑  javaBean   
          V：视图    jsp  
	  C：Controller，控制器 分发  获取用户输入，调用模型，将数据交给视图层   
 ![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/MVC%E6%A8%A1%E5%9E%8B%E6%9E%B6%E6%9E%84.png)
 架构模式   
 优点：耦合性低维护方便，利于分工，重用性比较高，生命周期成本低   
 缺点：没有明确定义，需要精心设置，结构复杂，不适用于小型项目   
#### El表达式   
 概述：Expression Language表达式语言   
 作用：简化jsp中，java的编写  
 语法${表达式}  
 注意事项：默认支持EL表达式，当在page中配置isELIgnored为true时，忽略所有EL表达式，当然也可以忽略单个  
 在语法前加\即可  
EL表达式的使用方式：运算和获取值   
 运算符：除法也可以用div取余也可以用mod，特别注意空运算符就是empty  
 空运算符：用于判断字符串集合数组对象是否为null${empty List}如果list为空返回true   
 el表达式只能从jsp的域对象中获取值   
 语法：${域对象.域名}   
 域名：pageScope  从pageContext获取    
      requestScope 从request 获取   
      sessionScope 从 session中获取   
      applicationscope 从 application（ServletContext）  
     如果没获取到返回空字符串不会出现null    
键名：表示从最小的域中查找是否有是否有该键的只，找到为止   即request域小于session 域所以先request   
获取对象 ${requsetScope.u.属性}   
		  
list获取   $<list.list.1>   
		  
### JSTL  
 概念：jsp标准库，有Apache组织提供的开源的免费的jsp标签   
 常用的JSTL if  choose  foreach     、
 if就是v-if   choose类似switch   
		  
		  
### 三层架构  
  软件设计架构，将软件分为三个层面
  1.界面层  用户看得到的界面，用户可以通过界面上的组件和服务器交互  
  2.业务逻辑层   service   
  3.数据访问层  dao     
![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/%E4%B8%89%E5%B1%82%E6%9E%B6%E6%9E%84.png) 
		  
		  
### Filter  
web中的过滤器：当访问服务器资源时，过滤器可以将请求拦截，完成一些特殊的功能    
继承servlet类下的Filter类，重写doFilter方法即可，配置urlpatten，webfilter（“拦截路径 ”）    
如若放行：调用filterchain对象的doFilter（）方法   
web.xml配置方法    
``` <filter>
        <filter-name>demo1</filter-name>
        <filter-class>com.example.filter</filter-class>
    </filter>
    <filter-mapping>
        <filter-name>demo1</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>
```  
    两种配置方式  
   对于Filter中，init周期用于加载资源而destory周期用于释放资源  
   过滤器执行流程  
   执行过滤器  
   执行放行后的资源  
   回来执行过略放行代码下边的代码  
   拦截路径配置：  
   1.具体路径资源  只有访问某个资源时才执行相关操作  
   2.目录拦截  访问目录资源下全部拦截   
   3.后缀名拦截 *.jsp访问所有后缀名为jsp时候执行  
   4.拦截所有资源  访问所有资源都执行   
   拦截方式：
   注解配置：dispatcherTypes属性可以定义资源被访问的方式   
   request：直接请求  forward：转发访问的资源  include 包含访问资源  error：错误跳转资源  async：异步访问资源   
   过滤器先后顺序问题：1.注解配置：按类名进行字符串比较规则来比较，谁小谁先执行  而web.xml是谁先配置谁先执行，谁在前面谁先执行   
   代理模式：增强对象功能典型代表动态代理  
   动态代理概念：真实对象：被代理对象  
   代理模式：代理对象代理真实对象，达到增强真实对象的功能  
   实现方式： 
   静态代理：.class文件描述代理模式   
   动态代理：在内存中形成代理类    
   实现步骤：大力对象和真实对象实现相同的接口  
   代理对象 =  Proxy.newIntstance  
   三个参数：1.类加载器2接口数组，真实对象3.处理器 new InvocationHanler（）  
  其中  new InvocationHandler中有invoke方法，该方法通过反射加载进内存，所有代理对象的方法均会触发该方法   
getDeclaringClass方法返回类内部的类    
method:代理对象调用的方法封装的对象   
proxy：代理对象   
args：代理对象调用的方法时传入的参数  
代理对象通过拿到真实对象的method方法传入参数在invoke方法中调用传入method的invoke方法来执行，本身并不具备执行方法能力    
代理对象增强方式：  
增强参数列表    	  
增强方法体   
增强返回值    
``` java  
        Salecomputer com = new computer();
        Salecomputer prox_com = (Salecomputer) Proxy.newProxyInstance(com.getClass().getClassLoader(), com.getClass().getInterfaces(), new InvocationHandler() {
            @Override
            public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
                if (method.getName().equals("sale")) {
                    double money = (double) args[0];
                    money = money * 0.85;
                    Object obj = method.invoke(com, money);
                    return obj;
                }
                return null;
            }
        });
        String sale = prox_com.sale(8000);
        System.out.println(sale);
``` 	 
		  
过滤案例  
``` java
    private List<String> l = new ArrayList<>();
    public void init(FilterConfig config) throws ServletException {
        System.out.println("初始化");
        try {
            ServletContext servletContext = config.getServletContext();
            String realPath = servletContext.getRealPath("/WEB-INF/b.txt");
            BufferedReader br = new BufferedReader(new FileReader(realPath));
            String line = null;
            while ((line=br.readLine())!=null){
                l.add(line);
            }
            br.close();
            System.out.println(l);
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
   @Override
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain) throws ServletException, IOException {
        ServletRequest prox_req = (ServletRequest) Proxy.newProxyInstance(request.getClass().getClassLoader(), request.getClass().getInterfaces(), new InvocationHandler() {
            @Override
            public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
                if(method.getName().equals("getParameter")){
                    String s = (String) method.invoke(request, args);
                    if(s!=null){
                        for (String str : l) {
                            if(s.contains(str)){
                                s=s.replaceAll(str,"***");
                            }
                        }
                    }
                    return  s;
                }
                return method.invoke(request,args);
            }
        });
        chain.doFilter(prox_req,response);
    }
```

    ### Lister：监听器  
        事件监听机制
        事件：一件事情  
        事件源：事件发生的地方  
        监听器：一个对象   
        注册监听：将事件、事件源、监听器绑定在一起。当时事件源上发生磨个时间后，执行监听器代码   
        ServletContextListener：
            监听ServletContext对象创建，该对象在服务器启动后自动创建  
            *void contextDestroyed（servletcontextevent sce）对象销毁调用    
            *同理也有创建时调用的方法  
		 ### JSON：
          概念Ljavascript object notation js对象表示法  
          JSON多用于存储和交换文本信息的语法  
          语法数据在名称/值章：json数据是由键值对构成  
          值得取值的类型：  
           1.数字  
           2.字符串  
           3.逻辑值  
           4.数组用[]表示    
           5.对象用花括号表示    
           6.null    
      ** JSON数据和java的转换  
          java对象转换json，最麻烦的无非键值名拼  
          解析器：jsonlib官方提供的接口  springmvc内置的jackson解析器   
          使用步骤  
            1.导入jackson的相关jar包  
            2.创建jackson核心对象 ObjectMapper  
            3.调用Objectmapper的相关方法
          objectmapper方法 
            writeValue（参数1，参数2）其中参数一有多种重载：File，writer outputstream  
            writeValueAsString 直接转换为json字符串  
            当writeValue参数1为文件时候，将json字符串写入某个文件  
            list转json就是数组格式  
            @JsonIgnore：排除属性忽略某属性     
            @JsonFormat（partten=“yyyy-mm-dd）
  ### redis  
  非关系型数据库（NoSql）,redis,hbase,magodb  
  无表，存的就是ksy：value，存在内存中  
  1.数据无关系  
  2.数据存储在内存中   
  原因操作关系型数据库十分耗时
  
	### jedis  
  基本操作和redis基本一致
  字符串哪里可以设时间消失   
 setex（key,seconds,value）   
### jedis  
创建连接池对象   
调用getResource 获取jedis对象  
创建配置对象   new JedisPoolConfig（）对象右set方法maxtotal最大连接数，maxidle最大空闲连接    
``` java
            pro.load(rs);
            JedisPoolConfig jpc = new JedisPoolConfig();
            jpc.setMaxIdle(Integer.parseInt(pro.getProperty("maxIdle")));
            jpc.setMaxTotal(Integer.parseInt(pro.getProperty("maxTotal")));
            jp = new JedisPool(jpc,pro.getProperty("host"), Integer.parseInt(pro.getProperty("port")));
```
### Maven  
	  项目管理工具，包含项目对象模型POM，一组标准集合，一个项目生命周期，一个依赖管理系统，和用来运行定义在生命周期阶段   
    中插件目标的逻辑    
    解决的问题：jar包引入过多，解决bug，项目测试，和方便打包   
    maven的依赖管理：传统工程jar包在项目中，而maven不会再项目中，统一放在jar包仓库中，通过jar包坐标来找到jar包    
    总结就是maven工程对jar包的管理过程    
    一键构建：普通项目要经历编译，测试，运行，打包，安装，部署而maven只需要一个命令   
    pom.xml放置的jar包的坐标     
    #### maven仓库   
          中央仓库、本地仓库、私服
         在maven安装目录中找到settings.xml文件中找到用户目录在.m2文件夹下的repository下创建仓库   
          默认在系统盘找本地仓库jar包就放在这里，再联网后通过中央仓库直接下载jar包   
          一般会再创建远程仓库（私服）确保电脑与私服再同一个网段，可以很方便的获取jar包，一部分本地一部分中央仓库  
          当然可以通过`<localRepository>/path/to/local/repo</localRepository>`来修改本地仓库的配置路径    
    #### maven标准目录结构   
          核心代码部分   
          配置文件部分   
          测试代码部分  
          测试配置文件部分    
          标准目录结构   
            src/main/java核心代码  
            src/main/resource 配置文件  
            src/test/java 测试代码  
            src/test/resource  测试文件   
            src/main/webapp 页面资源 js，css，图片   
     #### maven常用命令   
          mvn clean 删除target目录  清楚编译信息   
          mvn compile 编译后会在右target目录   其中class里面放的是字节码文件  是将main下的核心代码进行编译  
          mvn test 测试  
          mvn package  打包对test和核心代码都进行编译    再pom中可以设置打包类型     
          mvn install 打包后将包放在本地仓库    
     #### maven生命周期   
          清理生命周期   
          默认生命周期  后面的会自动执行前面的   
          站点生命周期   
![image](https://github.com/lieycheng987/JAVA-/blob/master/picture/maven%E6%A8%A1%E5%9E%8B%E5%9B%BE.png)    
            
          项目对象模型：项目自身信息   
		  项目运行所依赖的jar信息   
		  项目运行环境信息jdk、tomcat   
		  
