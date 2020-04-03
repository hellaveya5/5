### 杂

可变参数：

1. 参数列表只能有一个
2. 若有多个参数，可变参数一定是要最后一个



Person类默认继承了Object类所以可以使用Object类的equals方法boolean equals(Object obj)指示其他某个对象是否与此对象“相等“。

equals方法源码：

```java
pubulic boolean equals(Object obj){
    return(this==obj)
}
```

###### 多态

弊端：无法使用子类的内容（子类的属性和方法）

Object obj = p2 =new Person ;

解决：可以使用向下转型（强转）吧obj类型转换为Person

Person p=(Person) obj;

```java
getClass()!= o.getCalss()
```

等效于

```java
obj instanceof Person
```

equals方法重写的原理

野指针的解决方法：开辟内存让指针指向。

***

```java
java.util.Date
```

表示日期和时间的类

类Date表示特定的瞬间，精确到毫秒。

时间原点：1970年1月1日 00：00：00（英国格林威治）

类Format

1. DateFormat:日期/时间格式化子类的抽象类//作用：格式化（日期变文本），和解析（反之）
2. MessageFormat
3. NumberFormat
   - 

######  异常

public Date parse(string source) throws ParseException

parse方法神功了一个异常叫ParseException

如果字符串和构造方法的模式不一样，那么程序就会抛出异常

###### ![](C:\Users\98333\AppData\Roaming\Typora\typora-user-images\image-20200328210324921.png)

***



###### Calendar类

```java
public static void calendar(){
        Calendar c = Calendar.getInstance();
        System.out.println(c);

    }
/* 
	public int get(int field);
	public void set(int field,int value);
	public abstract void add(int field,int amount);
	public Date getTime();返回一个表示这个Calendar时间值。参数：传递指定的日历字段（YEAR,MONTH...)返回对应的字段/
*/
//加两年
    c.add(Calendar.YEAR,2)
//减两个月,,
	c.add(Calendar.MONTH,-2)
    int year=c.get(Calendar.YEAR);
	c.set(Calendar.DATE,9)
    c.set(2020,8,8)//同时设置年月日。方法的重载
```



***

静态的方法可以直接用类名获得。

***

###### System类

```java
public static long currentTimeMillis();返回以毫秒为单位的当前时间
public static void arraycopy(Object src ,int srcPos,Object dest,int destPot,int Length);将数组中指定的数据拷贝到的另一个数组中
参数：src - 源数组
     srcPos - 源数组中的起始位置（起始索引） 
     dest - 目标数组
     destPos - 目标数据中的起始位置
     Length -  要复制的数组元素的数量
     
```

***

###### StringBuilder类

String类不能变但是StringBuilder也就是字符串缓冲区可以改变

提高了字符串的操作效率,可以改变长度，自动扩容

byte[] value = new byte[16]

```Java
//方法一:添加字符串。返回自身
public StringBuilder append(...)
//转化成Sting类
public StringBuilder toString()
```

可用链式编程：bu.append("kkk").append("safd").



***

String类

字符串时常量：他的值在创建后不能在改变  底层时一个被final修饰的数组。private final byte[] value

进行字符串的相加，内存中有多个字符串，占用空间多，效率低下

***

###### 包装类

*基本数据类型，使用起来非常方便，但是没有对应的操作方法来操作这些数据类型，所以我们可以使用一个类把基本类型的数据装起来在类中定义一些方法，用方法来操作这些基本数据类型，这个类叫做包装类*就像Byte类和Double类

***

###### 装箱与拆箱

从基本类型转换为包装类对象。从包装类对象转换为对应的基本类型

### Collection接口

*所有没有带索引的方法，单列集合*

```java
//add一般返回true值，一般不接受他
//remove 删除了存在的就返回true反之false
//contains若是包含该元素则true
//isEmpty集合不空则true
public boolean add(E e);
public boolean addAll(E,"","",..);
public void clear();
public boolean removed(E e);
public boolean contains(E e);
public boolean isEmpty();
public int size();
public Object[] toArray();
```

shuffle(E)打乱集合中的元素顺序

#### list接口

1. *有序的的集合*

2. *可重复元素*

3. *有索引（能for循环遍历）*

   get(int index);

   remove(int index);

   set(int index E element)

   

   

##### Vector集合

##### ArrayList集合

数组结构。

##### LinkedList集合

链表结构

#### set接口

1. *无索引*（不能用普通for循环）
2. *不重复元素*

##### Treeset集合

##### HashSet集合

1. 无序的集合
2. 哈希表结构（查询速度快）：数组+红黑树/链表

###### LinkedHashSet集合：

有序的，加多了个链表（记录存储顺序）

### iterator接口

*迭代器对集合进行编历*

使用集合中的方法iterator（）获取迭代器实现类对象，使用Iterator接口接收(多态）

```java
//coll.iterator()索引指向-1且获取迭代器实现类对象
Iterator<String> it = coll.iterator();
/*功能：输出集合中的元素
it.hasNext()判断有没有下一个元素

*/
while(it.hasNext()){
    Stirng  e = it.next();
    System.out.println(e);
}
/*it2.next()做了2件事情
1取出下一个元素
2把索引一项下一位
*/
for(Iterator<String>it2 = coll.iterator();it2.hasNext();){
    String e = it2.next();
    System.out.println(e);
}
/*增强for循环：仅用于遍历集合
for(集合/数组的数据类型 变量名：集合名/数组名)*/
for(String s:it){
    System.out.println(s)
```

***

### Map接口

*双列集合*

Map(K,V)：一个是key一个是value

key不可以重复value可以

key&value 一一对应

##### map集合遍历方式

1. 取key放set集合中，遍历set
2. 用entry对象取出来放入set，利用entry对象中的方法getKey()&getValue()获取键和值

### 集合&泛型

*集合（object类型）是一种未知数据类型的变量，当不确定数据类型时可以使用创建对象的时候在把数据类型传递过去*

集合的好处：可存储任意数据类型。坏处：是不安全容易引起异常

泛型好处：避免了类型的转换，把运行期的异常提升到了编译期。 

##### 含有泛型的接口

##### 含有泛型的方法

public <M>void metho01(M m){	

System.out.println(n);

}

### io流

```java
FileIntputStream fis = new FileInputStream(c:\\..)
FileOutputStream fos = new FileOutputStream(d:\\..)
//读取
int len = 0;
while((len=fls.read())!=-1){
    sout(len);
    //写入
    fos.write(len);
}
```

