# 基础题

### 练习一：Map接口的特点

1.  请简述Map 的特点。

```
-   Map每个元素由键与值两部分组成

-   Map键不能重复,每个键对应一个值

-   键和值可以为null
```



### 练习二：Entry键值对对象

1.  说出Entry键值对对象遍历Map集合的原理。

```java
Map中存放的是两种对象，一种称为key(键)，一种称为value(值)，它们在在Map中是一一对应关系，这一对对象又称做Map
中的一个Entry(项)。Entry将键值对的对应关系封装成了对象。即键值对对象，这样我们在遍历Map集合时，就可以从每一个键值对（Entry）对象中获取对应的键与对应的值。
```



### 练习三：Map接口中的常用方法

1.  请使用Map集合的方法完成添加元素，根据键删除，以及根据键获取值操作。

```java
public class MapTest01**{  
**public static void** main(String[] args) {  
// 1.创建HashMap  
HashMap\<String, String\> hm = **new** HashMap\<String, String\>();  

// 2.使用put添加元素  
hm.put(**"黄晓明"**, **"Baby"**);  
hm.put(**"邓超"**, **"孙俪"**);  
hm.put(**"李晨"**, **"范冰冰"**);  
hm.put(**"大黑牛"**, **"范冰冰"**);  

// 3.使用put修改元素  
String v1 = hm.put(**"李晨"**, **"白百合"**);  

// 4.使用get获取元素  
String string = hm.get(**"大黑牛"**);  

// 5.使用remove删除元素  
String v2 = hm.remove(**"大黑牛"**);  
System.**out**.println(v2);  

// 6.打印集合中的元素  
System.**out**.println(hm);  
}  
}
```



### 练习四：Map接口中的方法

1.  往一个Map集合中添加若干元素。获取Map中的所有value，并使用增强for和迭代器遍历输出每个value。

```java
public class** MapTest02 {  
**public static void** main(String[] args) {  
// 1.创建HashMap  
HashMap\<String, String\> hm = **new** HashMap\<String, String\>();  

// 2.使用put添加元素  
hm.put(**"黄晓明"**, **"Baby"**);  
hm.put(**"邓超"**, **"孙俪"**);  
hm.put(**"李晨"**, **"范冰冰"**);  
hm.put(**"大黑牛"**, **"范冰冰"**);  

// 3.使用Map的values方法获取到所有的value  
Collection\<String\> values = hm.values();  

// 4.使用增强for获取每个value  
**for** (String value : values) {  
System.**out**.println(value);  
}  

System.**out**.println(**"----------------"**);  
// 5.使用迭代器获取每个value  
Iterator\<String\> itr = values.iterator();  
**while** (itr.hasNext()) {  
System.**out**.println(itr.next());  
}  
}  
}
```



### 练习五：HashMap存储键是自定义对象值是String

1.  请使用Map集合存储自定义数据类型Car做键，对应的价格做值。并使用keySet和entrySet两种方式遍历Map集合。

```java
汽车类:

// 1.定义汽车类.包含名称和价格属性,重写hashCode和equals方法  
**public class** Car {  

**private** String **name**;  

**private** String **color**;  

**public** Car() {  
}  

**public** Car(String name, String color) {  
**this**.**name** = name;  
**this**.**color** = color;  
}  

**public** String getName() {  
**return name**;  
}  

**public void** setName(String name) {  
**this**.**name** = name;  
}  

**public** String getColor() {  
**return color**;  
}  

**public void** setColor(String color) {  
**this**.**color** = color;  
}  

@Override  
**public boolean** equals(Object o) {  
**if** (**this** == o) **return true**;  
**if** (!(o **instanceof** Car)) **return false**;  

Car car = (Car) o;  

**if** (**name** != **null** ? !**name**.equals(car.**name**) : car.**name** !=
**null**) **return false**;  
**return color** != **null** ? **color**.equals(car.**color**) : car.**color**
== **null**;  
}  

@Override  
**public int** hashCode() {  
**int** result = **name** != **null** ? **name**.hashCode() : 0;  
result = 31 \* result + (**color** != **null** ? **color**.hashCode() : 0);  
**return** result;  
}  
}

测试类:

**public class** MapTest03 {  
**public static void** main(String[] args) {  
// 2.创建HashMapkey保存汽车对象,value是汽车价格  
HashMap\<Car, Integer\> hm = **new** HashMap\<\>();  

// 3.添加汽车到HashMap中  
Car c1 = **new** Car(**"长安奔奔"**, **"黄色"**);  
Car c3 = **new** Car(**"奇瑞QQ"**, **"黑色"**);  
Car c2 = **new** Car(**"铃木奥拓"**, **"白色"**);  

hm.put(c1, 10000);  
hm.put(c2, 20000);  
hm.put(c3, 30000);  

// 4.使用keySet方式遍历Map  
Set\<Car\> keySet = hm.keySet();  
**for** (Car c : keySet) {  
// 根据key获取value  
Integer value = hm.get(c);  
System.**out**.println(c.getName() + **","**+ c.getPrice() + **" - "**+ value); 

}  

System.**out**.println(**"-------------"**);  

// 5.使用entrySet方式遍历Map  
Set\<Map.Entry\<Car, Integer\>\> entrySet = hm.entrySet();  
**for** (Map.Entry\<Car, Integer\> entry : entrySet) {  
Car key = entry.getKey();  
Integer value = entry.getValue();  
System.**out**.println(key.getName() + **","**+ key.getPrice() + **" - "**+
value);  
}  
}  
}
```



### 练习六：Map集合的使用（一）

1.  现在有一个map集合如下：

```java
Map\<Integer,String\> map = new HashMap\<Integer, String\>();  
map.put(1, "张三丰");  
map.put(2, "周芷若");  
map.put(3, "汪峰");  
map.put(4, "灭绝师太");
```

要求：

1.遍历集合，并将序号与对应人名打印。

2.向该map集合中插入一个编码为5姓名为李晓红的信息

3.移除该map中的编号为1的信息

4.将map集合中编号为2的姓名信息修改为"周林"

```java
public class** MapTest04 {  
**public static void** main(String[] args) {  
// 1.定义HashMap,编号作为key,姓名作为value  
Map\<Integer,String\> map = **new** HashMap\<Integer, String\>();  

// 2.使用put方法添加元素  
map.put(1, **"张三丰"**);  
map.put(2, **"周芷若"**);  
map.put(3, **"汪峰"**);  
map.put(4, **"灭绝师太"**);  

// 3.使用keySet+增强for迭代map中的元素,并打印  
Set\<Integer\> keySet = map.keySet();  
**for** (Integer key : keySet) {  
String value = map.get(key);  
System.**out**.println(key + **" -- "**+ value);  
}  

// 4.使用put向该map集合中插入一个编码为5姓名为李晓红的信息  
map.put(5, **"李晓红"**);  

// 5.使用remove移除该map中的编号为1的信息  
map.remove(1);  

// 6.使用put将map集合中编号为2的姓名信息修改为"周林"  
map.put(2, **"周林"**);  
System.**out**.println(map);  
}  
}
```



### 练习七：Map集合的使用（二）

1.  有2个数组，第一个数组内容为：[黑龙江省,浙江省,江西省,广东省,福建省]，第二个数组为：[哈尔滨,杭州,南昌,广州,福州]，将第一个数组元素作为key，第二个数组元素作为value存储到Map集合中。如{黑龙江省=哈尔滨,
    浙江省=杭州, …}。

```java
public class** MapTest05 {  
**public static void** main(String[] args) {  
// 1.定义第一个数组arr1  
String[] arr1 = {**"黑龙江省"**, **"浙江省"**, **"江西省"**, **"广东省"**,
**"福建省"**};  
// 2.定义第二个数组arr2  
String[] arr2 = {**"哈尔滨"**, **"杭州"**, **"南昌"**, **"广州"**, **"福州"**}; 


// 3.创建HashMap,key存放省,value存放市  
HashMap\<String, String\> hm = **new** HashMap\<\>();  

// 4.使用普通for循环遍历arr1  
**for** (**int** i = 0; i \< arr1.**length**; i++) {  
// 5.根据索引到arr1中获取到省  
String key = arr1[i];  
// 6.根据索引到arr2中获取到省会城市  
String value = arr2[i];  

// 7.将省和省会城市添加到HashMap中  
hm.put(key, value);  
}  
// 8.输出HashMap中的内容  
System.**out**.println(hm);  
}  
}
```

### 附录1

```java
练习一：集合框架
一、请简述集合框架。
集合按照其存储结构可以分为两大类，分别是单列集合java.util.Collection和双列集合java.util.Map。
Collection：单列集合类的根接口，用于存储一系列符合某种规则的元素，它有两个重要的子接口，分别是java.util.List和java.util.Set。其中，List的特点是元素有序、元素可重复。Set的特点是元素无序，而且不可重复。List接口的主要实现类有java.util.ArrayList和java.util.LinkedList，Set接口的主要实现类有java.util.HashSet和java.util.TreeSet。
练习二：Collection集合统计元素出现次数

练习二：Collection集合集合转数组
二、定义一个集合，并把集合(集合里面的元素是Integer)转成存有相同元素的数组，并将结果输出在控制台。（可以使用Object[]数组类型接收转换的数组）
public class CollectionTest03 {
    public static void main(String[] args) {
        //定义集合,添加数据
        ArrayList<Integer> list = new ArrayList<Integer>();
        list.add(100);
        list.add(200);
        list.add(300);
        //Object[] toArray()转换成一个Object数组
        Object[] obj =  list.toArray();
        // 遍历数组
        for (int i = 0; i < obj.length; i++) {
            System.out.println(obj[i]);
        }
    }
}


练习三：Collection集合contains()方法使用
三、定义一个方法listTest(ArrayList<String> al, String s),要求使用contains()方法判断al集合里面是否包含s。
public class CollectionTest04 {
    public static void main(String[] args) {
        //定义集合，添加数据
        ArrayList<String> list = new ArrayList<String>();
        list.add("itcast");
        list.add("itheima");
        list.add("java");
        System.out.println(listTest(list,"java"));
    }

    public static boolean listTest(ArrayList<String> al, String s) {
        //判断s是否在集合中存在,存在返回true，不存在返回false
        if (al.contains(s)) {
            return true;
        }
       return false;
    }
}


练习四：Collection集合isEmpty()方法的使用
四、定义一个方法listTest(ArrayList<String> al), 要求使用isEmpty()判断al里面是否有元素。
public class CollectionTest05 {
    public static void main(String[] args) {
        //定义集合，添加数据
        ArrayList<String> list = new ArrayList<String>();
        list.add("1");
        System.out.println(listTest(list));
    }

    public static boolean listTest(ArrayList<String> al) {
        //判断al集合是否为空,为空返回true，不为空返回false
        if(al.isEmpty()){
            return true;
        }
        return false;
    }
}
练习五：简述迭代器的实现原理
五、请简述迭代器的实现原理
当遍历集合时，首先通过调用集合的iterator()方法获得迭代器对象，然后使用hashNext()方法判断集合中是否存在下一个元素，如果存在，则调用next()方法将元素取出，否则说明已到达了集合末尾，停止遍历元素。
Iterator迭代器对象在遍历集合时，内部采用指针的方式来跟踪集合中的元素，在调用Iterator的next()方法之前，迭代器的索引位于第一个元素之前，不指向任何元素，当第一次调用迭代器的next方法后，迭代器的索引会向后移动一位，指向第一个元素并将该元素返回，当再次调用next方法时，迭代器的索引会指向第二个元素并将该元素返回，依此类推，直到hasNext方法返回false，表示到达了集合的末尾，终止对元素的遍历。




练习六：Collection集合返回首次出现索引
六、定义一个方法listTest(ArrayList<Integer> al, Integer s)，要求返回s在al里面第一次出现的索引，如果s没出现过返回-1。
public class CollectionTest06 {
    public static void main(String[] args) {
        //定义集合，添加数据
        ArrayList<Integer> list = new ArrayList<Integer>();
        list.add(1);
        list.add(2);
        list.add(3);
        list.add(4);
        list.add(5);
        System.out.println(listTest(list, 5));
    }

    public static int listTest(ArrayList<Integer> al, Integer s) {
        //遍历集合，获取元素，判断元素是否与s相等，相等返回索引
        for (int i = 0; i < al.size(); i++) {
            if (al.get(i).equals(s)) {
                return i;
            }
        }
        return -1;
    }
}

```

### 附录2

```java
练习一：List接口的特点
一、请简述List接口的特点。
	它是一个元素存取有序的集合。例如，存元素的顺序是11、22、33。那么集合中，元素的存储就是按照11、22、33的顺序完成的）。
	它是一个带有索引的集合，通过索引就可以精确的操作集合中的元素（与数组的索引是一个道理）。
	集合中可以有重复的元素，通过元素的equals方法，来比较是否为重复的元素。


练习二：LinkedList方法的使用
二、根据要求练习LinkedList方法：
（1）基本方法：add, set, get, remove, clear, size等方法；
（2）特有方法：addFirst, addLast, getFirst, getLast, removeFirst, removeLast, push, pop, clear等方法。
（1）基本方法：
public class LinkedListTest01 {
    public static void main(String[] args) {
        // 1.创建LinkedList
        LinkedList<String> arr = new LinkedList<String>();

        // 2.使用add方法添加元素
        arr.add("西门吹雪");
        arr.add("西门吹雪");
        arr.add("西门吹雪");
        arr.add("西门吹风");
        arr.add("西门吹水");

        // 3.使用add方法在指定索引添加元素
        arr.add(2, "西门吹雨");

        // 4.使用set方法修改指定位置索引
        arr.set(0, "东门");

        for (String str : arr) {
            System.out.println(str);
        }
        System.out.println("--------------");
        // 5.使用get方法获取指定索引的元素
        System.out.println(arr.get(1));

        // 6.使用size方法获取集合大小
        System.out.println(arr.size());

        // 7.使用remove方法删除指定索引的元素
        arr.remove(3);

        // 8.使用clear清空集合中的元素
        arr.clear();
        System.out.println(arr);
    }
}
（2）特有方法
public class LinkedListTest02 {
    public static void main(String[] args) {
        // 1.创建LinkedList
        LinkedList<String> linked = new LinkedList<String>();

        // 2.使用add方法添加元素
        linked.add("周杰伦");
        linked.add("周星驰");
        linked.add("周华健");
        linked.add("周润发");

        // 3.使用addFirst添加元素到集合最前面
        linked.addFirst("周传雄");

        // 4.使用addLast添加元素到集合最后面
        linked.addLast("周渝民");

        System.out.println(linked);

        // 5.使用getFirst获取集合第一个元素
        System.out.println(linked.getFirst());

        // 6.使用getLast获取集合最后一个元素
        System.out.println(linked.getLast());

        // 7.使用removeLast删除集合第一个元素
        String first = linked.removeFirst();
        System.out.println(first);

        // 8.使用removeLast删除集合最后一个元素
        String last = linked.removeLast();
        System.out.println(last);
        System.out.println(linked);


        // 9.使用pop弹出第一个元素
        String p = linked.pop();
        System.out.println(p);

        // 10.使用push在集合开头插入元素
        linked.push("周立波");
        System.out.println(linked);

        // 11.使用clear清空集合
        linked.clear();
        System.out.println(linked);
    }
}
练习三：List集合元素替换
三、向list集合添加姓名{张三,李四,王五,二丫,钱六,孙七},将二丫替换为王小丫。
public class ListTest01 {
    public static void main(String[] args) {
        //1.创建List集合对象
        List<String> list = new ArrayList<>();
        //2.存入数据
        list.add("张三");
        list.add("李四");
        list.add("王五");
        list.add("二丫");
        list.add("钱六");
        list.add("孙七");
        //3.遍历集合，找到"二丫",便将其替换为"王小丫"
        //利用普通for循环遍历List集合
        for(int i = 0;i<list.size();i++) {
            //获取当前元素
            String thisName = list.get(i);
            //如果当前元素是"二丫"
            if("二丫".equals(thisName)) {
                //将其改为"王小丫"
                list.set(i, "王小丫");
            }
        }
        System.out.println(list);
    }
}


四、给定以下代码，请定义方法listTest()统计集合中指定元素出现的次数，如"a": 2,"b": 2,"c" :1, "xxx":0。
		Collection<String> list = new ArrayList<>();
			list.add("a");
			list.add("a");
			list.add("b");
			list.add("b");
			list.add("c");
			System.out.println("a:"+listTest(list, "a"));	
			System.out.println("b:"+listTest(list, "b"));	
			System.out.println("c:"+listTest(list, "c"));
			System.out.println("xxx:"+listTest(list, "xxx"));		
public class CollectionTest01{
    public static void main(String[] args) {
        Collection<String> list = new ArrayList<>();
        list.add("a");
        list.add("a");
        list.add("b");
        list.add("b");
        list.add("c");
        System.out.println("a:"+listTest(list, "a"));
        System.out.println("b:"+listTest(list, "b"));
        System.out.println("c:"+listTest(list, "c"));
        System.out.println("xxx:"+listTest(list, "xxx"));
    }

    //定义方法统计集合中指定元素出现的次数
    public static int listTest(Collection<String> list,String s){
        //定义计数器，初始化为0
        int count = 0;
        //增强for遍历集合
        for (String string : list) {
            //判断传入方法的字符与遍历集合的是否一致
            if (s.equals(string)) {
                //如果一致，加1
                count++;
            }
        }
        return count;
    }
}
练习五：Collection集合数组转集合
五、定义一个方法，要求此方法把int数组转成存有相同元素的集合(集合里面的元素是Integer)，并返回。()
public class CollectionTest02 {
    public static void main(String[] args) {
        //定义int数组
        int[] arr = {1,2,3,4,5};
        ArrayList<Integer> list = listTest(arr);
        System.out.println(list);
    }

    public static ArrayList<Integer> listTest(int[] arr) {
        //定义集合
        ArrayList<Integer> list = new ArrayList<Integer>();
        //遍历数组，把元素依次添加到集合当中
        for (int a : arr) {
            list.add(a);
        }
        return list;
    }
}
```

### 附录3

```javascript
练习二：hashCode和equals方法
二、请简述HashSet去除重复元素的原理。
	调用被添加元素的hashCode()，和HashSet中已有元素的hashCode比较是否相同
	如果不相同，直接存储
	如果相同，调用equals方法比较是否相同
	不相同，直接存储元素
	相同，认为是同一元素.不存储


练习三：数据结构
三、简述常见的数据结构中元素的存取特点。
	栈：stack，又称堆栈，对元素的存取特点是：先进后出。即，存进去的元素，要在后它后面的元素依次取出后，才能取出该元素。
	队列：queue，简称队，对元素的存取特点是：先进先出。即，存进去的元素，要在后它前面的元素依次取出后，才能取出该元素。
	数组:Array，是有序的元素序列，对元素的存取特点是：
1、查找元素快：通过索引，可以快速访问指定位置的元素
2、增删元素慢
（1）指定索引位置增加元素：需要创建一个新数组，将指定新元素存储在指定索			引位置，再把原数组元素根据索引，复制到新数组对应索引的位置。
（2）指定索引位置删除元素：需要创建一个新数组，把原数组元素根据索引，复			制到新数组对应索引的位置，原数组中指定索引位置元素不复制到新数组中。
	链表:linked list，对元素的存取有如下的特点：
1、多个结点之间，通过地址进行连接。例如，多个人手拉手，每个人使用自己的		右手拉住下个人的左手，依次类推，这样多个人就连在一起了。
2、查找元素慢：想查找某个元素，需要通过连接的节点，依次向后查找指定元素。
3、增删元素快：
增加元素：只需要修改连接下个元素的地址即可。
删除元素：只需要修改连接下个元素的地址即可。


练习六：HashSet存储自定义类型
六、定义人类，包含姓名和年龄属性。创建4个人存储到HashSet中，姓名和年龄相同的人看做同一人不存储。
Person类:
// 1.定义Person类.包好姓名年龄属性,重写hashCode()和equals()方法
public class Person {
    private String name;
    private int age;

    public Person() {
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (!(o instanceof Person)) return false;

        Person person = (Person) o;

        if (age != person.age) return false;
        return name != null ? name.equals(person.name) : person.name == null;
    }

    @Override
    public int hashCode() {
        int result = name != null ? name.hashCode() : 0;
        result = 31 * result + age;
        return result;
    }

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}
测试类
public class HashSetTest01 {
    public static void main(String[] args) {
        // 2.创建HashSet用于存储Person类型
        HashSet<Person> hashSet = new HashSet<Person>();

        // 3.添加多个Person到HashSet中
        hashSet.add(new Person("王昭君", 21));
        hashSet.add(new Person("西施", 21));
        hashSet.add(new Person("杨玉环", 20));
        hashSet.add(new Person("貂蝉", 19));
        hashSet.add(new Person("杨玉环", 20));
        hashSet.add(new Person("貂蝉", 19));

        // 4.遍历获取HashSet中的内容
        for (Person p : hashSet) {
            System.out.println(p);
        }
    }
}

```

### 附录4

```java
练习一：异常的体系
问题：
1.	请描述异常的继承体系
2.	请描述你对错误(Error)的理解
3.	请描述你对异常(Expection的理解)
4.	请描述你对运行时异常(RuntimeException)的理解

答：

1.	异常继承体系为：异常的根类是 java.lang.Throwable，其下有两个子类：
java.lang.Error 与 java.util.Exception 。而Exception又分为编译时期异常：checked异常，与运行时期异常：runtime异常。 
2.	Error:表示不可修复的恶性的错误，只能通过修改代码规避错误的产生，通常是系统级别的，所以很严重。
3.	Exception:表示可修复的良性（相对于错误）的异常，异常产生后程序员可以并且应该通过代码的方式纠正，使程序继续运行，是必须要处理的。
4.	运行时期异常:runtime异常。在运行时期,检查异常.在编译时期,运行异常不会编译器检测(不报错)。

练习二：throw与throws的区别
问题：
1. 请描述throw的使用位置,作用是什么?
2. 请描述throws的使用位置,作用是什么?

答：
1.	throw关键字通常用在方法体中，并且抛出一个异常对象。程序在执行到throw语句时立即停止，它后面的语句都不执行。
2.	throws关键字通常被应用在声明方法时，用来指定可能抛出的异常。多个异常可以使用逗号隔开。当在主函数中调用该方法时，如果发生异常，就会将异常对象抛给方法调用处。

练习三：异常的处理方式
问题：
      1. 异常处理方式有几种,分别是什么?
      2. 详细阐述每种方式对异常是如何处理的
答：
1.	异常的处理方式有两种,分别是使用throws和try...catch...finally
2.	throws用在方法的声明上后接异常类名,是把异常抛给调用者进行处理
3.	try...catch...finally是捕获异常,自己处理,处理完毕后面的程序可以继续运行
a)	try代码块中是可能出现异常的代码
b)	catch代码块,是遇到异常,对异常进行处理的代码
c)	finally代码块是无论是否发生异常,都必须执行的代码,用于释放资源.


练习四：常见异常，及产生原因
问题：请列举常见异常，并说明产生原因。

答：
NullPointerException:空指针异常。
	当应用试图在要求使用对象的地方使用了null时，抛出该异常。譬如：调用null对象的实例方法、访问null对象的属性、计算null对象的长度等等。
ArrayIndexOutOfBoundsException:数组索引越界异常。
当对数组的索引值为负数或大于等于数组大小时抛出此异常。
ArithmeticException:算术运算异常。
	程序中出现了除以零这样的运算就会出这样的异常，对这种异常，大家就要好好检查一下自己程序中涉及到数学运算的地方，公式是不是有不妥了。
NumberFormatException:数字格式异常。
	当试图将一个String转换为指定的数字类型，而该字符串确不满足数字类型要求的格式时，抛出该异常。

注意：答案不唯一，合理即可。


练习五：看代码，分析结果
问题：根据给出的相应代码，分析可能产生的结果。

1.举例：
public static void main(String[]args){

 String str=null;
System.out.println(str.length());

}

答：变量str的值为null，调用方法时，报空指针异常NullPointerException



2.举例：
public static void main(String[]args){
int arr[]={1,2};
System.out.println(arr[2]);
}

答：索引值2大于等于数组arr的长度时，报数组索引越界异常ArrayIndexOutOfBoundsException



3.举例：
public static void main(String[]args){

System.out.println(1/0);
}

答：整数0做了分母，报算术运算异常ArithmeticException:/by zero



4.举例：
public static void main(String[]args){

System.out.println(Integer.parseInt("itcast"));

}

答：
把字符串“itcast”转换为Integer类型时，当然会报数字格式化异常啦NumberFormatException


5.举例：
public static void main(String[] args) {
    SimpleDateFormat format = new SimpleDateFormat("yyyy-mm-dd");
    
    try {
        Date date = format.parse("2018-04-03");
        System.out.println("程序正常");
        
    } catch (ParseException e) {
        System.out.println("程序异常");
    }
}


答：
	打印结果“程序正常”.try代码块中并没有产生异常，catch代码块中的代码不会执行。date为2018年1月3日00点04分00秒。



练习六：自定义异常类
问题：
请使用代码实现
每一个学生(Student)都有学号,姓名和分数,分数永远不能为负数
如果老师给学生赋值一个负数,抛出一个自定异常

答：
/*
 1.定义异常类NoScoreException,继承RuntimeException
a)提供空参和有参构造方法
 */

public class NoScoreException extends RuntimeException {
//  空参构造
public NoScoreException() {
super();
 }
// 有参构造
public NoScoreException(String message) {
super(message);
 }
}

/*
  2.定义学生类(Student)
 a)属性:name,score
 b)提供空参构造
 c)提供有参构造;
  i.使用setXxx方法给名称和score赋值
 d)提供setter和getter方法
  i.在setScore(int score)方法中
   1.首先判断,如果score为负数,就抛出NoScoreException,异常信息为:分数不能为负数:xxx.
   2.然后在给成员score赋值.
 */

public class Student {
private String name;
private int score;
// 空参构造
public Student() {
super();
 }
// c)提供有参构造;
// i.使用setXxx方法给名称和score赋值
public Student(String name,int score){
  setName(name);
  setScore(score);
 }
// d)提供setter和getter方法

public String getName() {
return name;
 }

public void setName(String name) {
this.name = name;
 }

public int getScore() {
return score;
 }
// i.在setScore(int score)方法中
public void setScore(int score) {
// 1.首先判断,如果score为负数,就抛出NoScoreException,异常信息为:分数不能为负数:xxx.
if(score <0){
throw new NoScoreException(":分数不能为负数:"+score);
  }
// 2.然后在给成员score赋值.
this.score = score;
 }
}


/*
3.定义测试类Test9
 a)提供main方法,在main方法中
  i.使用满参构造方法创建Student对象,分数传入一个负数,运行程序
  ii.由于一旦遇到异常,后面的代码的将不在执行,所以需要注释掉上面的代码
  iii.使用空参构造创建Student对象
  iv.调用setScore(int score)方法,传入一个正数,运行程序
  v.调用setScore(int score)方法,传入一个负数,运行程序
 */

public class Test9 {
public static void main(String[] args) {
//  i.使用满参构造方法创建Student对象,分数传入一个负数,运行程序
//  Student s = new Student("景甜", -10);
//  ii.由于一旦遇到异常,后面的代码的将不在执行,所以需要注释掉上面的代码

//  iii.使用空参构造创建Student对象
Student s = new Student();
//  iv.调用setScore(int score)方法,传入一个正数,运行程序
s.setScore(100);
//  v.调用setScore(int score)方法,传入一个负数,运行程序
s.setScore(-5);
 }
}

```

