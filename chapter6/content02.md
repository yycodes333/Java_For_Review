

- ​	`?`: 任意类型。

- ​	`? extends A`: A 或 A 的子类（上限）。

- ​	`? super A`: A 或 A 的父类（下限）。

    

#### 1.?  不确定传入具体类型



```java
package Demo;

import java.io.IOException;
import java.util.*;

public class Test {
    public static void main(String[] args) {

        List<String> strList = new ArrayList<>();
        strList.add("Java");
        strList.add("泛型");

        List<Integer> intList = new ArrayList<>();
        intList.add(10);
        intList.add(20);

        printList(strList); // 打印字符串列表
        printList(intList); // 打印整数列表

    }

    public static void printList(List<?> list) {
        for (Object obj : list) {
            System.out.println(obj);
        }
    }
}
```









#### 2.? extends 类



```java
package Demo;

import java.io.IOException;
import java.util.*;

public class Test {
    public static void main(String[] args) {

        List<String> strList = new ArrayList<>();
        strList.add("Java");
        strList.add("泛型");

        List<Integer> intList = new ArrayList<>();
        intList.add(10);
        intList.add(20);

        printList(strList); // 打印字符串列表
        printList(intList); // 打印整数列表

    }
				//与 ? 不一样就是extends 他表示对传入的类型不再是无界 而是extends后面类的子类才可以
   				//同样 若是? super 那就表示传入的类型只能是后边的类的父类来了
    public static void printList(List<? extends Object> list) {
        for (Object obj : list) {
            System.out.println(obj);
        }
    }
}
```



