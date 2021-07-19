# JAVA- 
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
    `String s1 = "100";
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
>>>好处：集合不使用泛型，默认类型就是object类型，可存储任意类型数据  
>>>弊端：不安全，会引发异常  
>>集合对象使用泛型  
>>>好处：避免了类型转换的麻烦，存储的什么类型，取出的就是什么类型  
>>>弊端：反省是什么类型，只能存储什么类型  
#### 泛型的方法
泛型也可以用在方法上，定义在修饰符和返回值类型之间
泛型方法如下`public <E> void method1(E m)`
泛型接口 接口写法第一种使用方式：我可以指定接口实现的类型
`public interface iterfa <E>{
  public abstract void method2(E e);
}`
#### 抽象接口方法
实现方法：可以选择直接实现类或继续使用泛型
第一种实现方法`public class impl implements iterfa<String> {

  @Override
  public void method2(String s) {
    // TODO Auto-generated method stub
    System.out.println(s);
  }
`
第二种实现方法： 
`public class impl1<E> implements iterfa<E>{

  @Override
  public void method2(E e) {
    // TODO Auto-generated method stub
    System.out.println(e);
  }
  
}`
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
键值对，k必须唯一，及键唯一值可重复，键相当于坐标而值相对与数值，不同步多线程的。可以通过get（key）找v
方法：  
1.put方法把指定的键值对添加到map中 put（k，v）返回值v，若key不重复，返回null，若key重复返回被替换的v  
2.remove方法把指定的建所对应的键值对元素在map中删除，返回删除元素  
3.containskey 方法判断键值对中有无这个key，有返回true，没有返回false  
4.keysey方法 遍历map集合，把map集合中的所有key取出来放到set集合中 set<k>keyset() 该方法返回一个set<k>类  增强for循环遍历即可
5.Entry<k，v> 映射项，在map接口中有个内部接口entry,作用，党map集合一创建，在map集合中回创建一个Entry对象，用来记录键与值（键值对象，键与值的映射关系）  
  可以用他来遍历map集合，该方法把map的Entry对象取出放到set集合中Entry是map类中的静态方法，会绑定map中的所有键值对，entryset是将返回的键值对存储到set中
 ### hashmap
  hashmap中如果要用自己定义的类作为key，就必须重写equal和hashcode方法。
 ### hashtable  同步实现类（单线程）
  早期的双链集合，哈希table不能存储空，无论键和值都不能空，因为是单线程的集合所以速度很慢
## Jdk9新特性
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
  ` public static void main(String[] args) {
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
  }`
  
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
  
  
  `  public static void main(String[] args) {  
    ExecutorService se = Executors.newFixedThreadPool(2);  
   ` se.submit(new runnableimpl());   //线程池会一直开启，使用万会归还个线程所以可以继续使用`
    se.submit(new runnableimpl());  
    se.submit(new runnableimpl());  
  }`
  
  
     
  ### Lambda表达式
  面向对象强调必须通过对象的心事来做事情，而函数式思想则尽量忽略面向对象的复杂语法--强调做什么而不是什么形式
  lambda标准格式有三部分组成
  1.一些参数2.一个箭头3.一段代码
  （参数列表）->{一些重写方法}例如排序题  

  `   Arrays.sort(arr,
      (Person p1,Person p2)->{
        return p1.age-p2.age;
      }
    )`
  
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
  `public class htmlServe {
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

    }`
  
  ### 函数式接口  
  函数式接口在java中指：有且只有一个抽象接口  
  函数式接口，适用于函数式编程场景的接口。而java中的函数式编程体现就是Lambda，有意函数式接口就是可以适用于Lambda的接口，只有确保   
  接口中有且仅有一个抽象方法，Java中的Lambda才能顺利进行推导  
  Lambda表达式可以被当作匿名内部类的语法糖  
  格式：只要保证接口中有且只有一个抽象方法即可
  ### Lambda表达式延迟执行的
