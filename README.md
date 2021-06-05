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
全部看左（*******注意多态中不能新添加子类方法添加新的子类方法是无法访问到的，只能对父类方法覆盖重写或者是继续沿用，无法啊新添加方法）
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
![image](https://github.com/lieycheng987/JAVA-/blob/main/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20210601173852.png)  

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
![image](https://github.com/lieycheng987/JAVA-/blob/main/2.png)  
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
 ![image](https://github.com/lieycheng987/JAVA-/blob/main/throw%E7%B1%BB.png)
 throwable类：是所有错误或者异常的超类。
  exception和erro是throwable下的两个子类  
  Exception：编译器异常，进行编译时出现的问题。  
  Error：错误，相当于无法治愈的问题，必须修改源代码，程序才能继续执行。 
  处理异常thow抛出给虚拟机，try{}catch{}，能查看异常也能执行后续代码   
  异常产生过程分析：jvm检测到程序出现异常后，  
 **1.jvm会根据异常的原因创建一个对象，这个对象包含了异常的产生（内容，原因，位置）  
  `new ArrayIndexOutOfBoundsException`（"3"）  
  2. 在方法中没有异常处理逻辑如（try catch），那么JVM会把异常对象抛出给方法的调用者，若调用者也没有，就在网上调用，最终返回给JVM，jvm接受这个异常对象（原因，位置，内容）打印到控制台  
  然后中断当前执行的程序**  
  #### 异常的处理
