

- HashMap

- TreeMap

    

​	**特点**：Key-Value 键值对，Key 唯一。

​	**遍历**：通常使用 `keySet()` 拿到键，再通过键找值。



#### 1.增删改查操作（API）

|                方法声明                |                           功能描述                           |
| :------------------------------------: | :----------------------------------------------------------: |
| ==void put(Object key, Object value)== |          将指定的值和键存入到集合中，并进行映射关联          |
|       ==Object get(Object key)==       | 返回指定键所映射的值;如果此映射不包含该键的映射关系，则返回null |
|              void clear()              |                     移除所有的键值对元素                     |
|        ==V remove(Object key)==        |              根据键删除对应的值，返回被删除的值              |
|               int size()               |                   返回集合中的键值对的个数                   |
|    boolean containsKey(Object key)     |        如果此映射包含指定键的映射关系，则返回 true。         |
|  boolean containsValue(Object value)   |       如果此映射将一个或多个键映射到指定值，则返回true       |
|            ==Set keySet()==            |                返回此映射中包含的键的Set集合                 |
|       ==Collection<V> values()==       |             返回此映射中包含的值的Collection集合             |



#### 2.HashMap  操作与HashSet一样



​	 **底层原理** 

- **结构**: JDK 1.7 是数组+链表；**JDK 1.8 是数组 + 链表 + 红黑树**。

- **扩容**: 初始容量 16，负载因子 0.75。当链表长度 > 8 且 数组长度 > 64 时，链表转为红黑树 (提高查询效率）。

- **去重**: 先算 `hashCode()` 确定槽位，再用 `equals()` 比较内容。



```Java
package Demo;

import java.io.IOException;
import java.util.*;

public class Test {
    public static void main(String[] args) {

      HashMap<Student,String> map = new HashMap<>();

        Student s1 = new Student(18,"张三");
        Student s2 = new Student(18,"张三");
        Student s3 = new Student(19,"王五");
        Student s4 = new Student(20,"马六");

        map.put(s1,"北");
        map.put(s2,"东");
        map.put(s3,"西");
        map.put(s4,"南");

        //这里涉及到Map的遍历，这里采用迭代器进行编写

        Set<Student> temp= map.keySet();


        Iterator<Student> it = temp.iterator();

        while(it.hasNext()){
           Student key = it.next();
           String value = map.get(key);
            System.out.println(key+":"+value);
        }

    }
}
```



**他这个去重原理是看你的键是否一样，而键的是否一样标准是我自己定义的，比如这里我的Student是键，而他的判断是否相同标准是看他的年龄和姓名同时一样才是相同的，也是根据我的标准去重.**

#### 3.TreeMap

```Java
package Demo;

import java.io.IOException;
import java.util.*;

public class Test {
    public static void main(String[] args) {

      TreeMap<Student,String> map = new TreeMap<>(new Comparator<Student>() {
          @Override
          public int compare(Student o1, Student o2) {
              int temp = o1.getName().compareTo(o2.getName());
              //这里我规定查重且比较顺序是看判断姓名，若姓名相同比较年龄；
              return temp==0? o1.getAge()- o2.getAge():temp;
          }
      });

        Student s1 = new Student(18,"张三");
        Student s2 = new Student(18,"王五");
        Student s3 = new Student(19,"王五");
        Student s4 = new Student(20,"马六");

        map.put(s1,"北");
        map.put(s2,"东");
        map.put(s3,"西");
        map.put(s4,"南");

        //这里涉及到Map的遍历，这里采用迭代器进行编写

        Set<Student> temp= map.keySet();


        Iterator<Student> it = temp.iterator();

        while(it.hasNext())
        {
           Student key = it.next();
           String value = map.get(key);
            System.out.println(key+":"+value);
        }

    }
}
```



  **同样，TreeMap查重原理和排序原理也是按照键，比如这里我的键是Student，那么我规定他的顺序是先按姓名再按年龄同时按照这样查重**

**TreeMap 排序/去重规则**：TreeMap **不使用** `hashCode/equals` 来判断重复；它完全依赖 **键** 的自然排序（`Comparable`）或构造时传入的 `Comparator`。

- 当 `compareTo()` / `compare()` 返回 **0** 时，认为是“同一个 key”（新的 value 会覆盖旧 value）。
- 因此：**比较规则必须与“逻辑相等”保持一致**，否则会出现 `equals` 不相等但 TreeMap 认为重复（或反之）的现象。