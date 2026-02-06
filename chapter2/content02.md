### 2.2 构造方法



- **目的**：

  ​	**1.初始化对象属性**：构造方法的主要作用是为对象的属性赋初值。

  ​	**2.保证对象初始化的完整性**：在构造方法中可以设置默认值或必要参数，从而避免对象未完全初始化的问题。

  

- **内容形式**：在 Java 中，构造方法（Constructor）是用于创建类的对象的特殊方法。当使用 new 关键字创建对象时，构造方法会自动调用，用来初始化对象的属性。





```java
public class Test {
    public static void main(String[] args) {
        System.out.println("首先调用未实例化类");
        Temp a1; // 仅声明，未实例化
        
        System.out.println("接着调用实例化类的创建");
        Temp a2 = new Temp(); // new 关键字触发构造方法
    }
}

class Temp {
    public Temp() {
        System.out.println("经过实例化对象成功调用了构造方法");
    }
}
```





过程理解：

1. 首先调用未实例化类

2. 接着调用实例化类的创建

3. 经过实例化对象成功调用了构造方法



