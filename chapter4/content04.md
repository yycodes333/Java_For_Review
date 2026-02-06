### 4.4 包装类

1.自动装箱 自动拆箱

**装箱**: `int` -> `Integer` (自动调用 `Integer.valueOf(i)`)。

**拆箱**: `Integer` -> `int`(自动调用 `intValue()`)。

**缓存池**: `Integer` 缓存了 **-128 到 到 127** 的对象。



```java
public class Test {
    public static void main(String[] args) {
        //自动装箱 将int -> 转换成Integer
      Integer a = 5;
        //自动拆箱 将Integer -> int
      int b = a;
    }
}
```

2.基本数据类型(以 int 类举例  )转换成 String类型  

```java
int a = 10;
String s = String.valueOf(a);
System.out.println( "s 经过String.valueOf接受了整数a ，那么成功转换成了String了吗？ "+s instanceof String);
```

3.String类型转换成基本数据类型（以double举例）

```java
 String a = "12.3";
Double b = Double.valueOf(a);
System.out.println( b);
```

