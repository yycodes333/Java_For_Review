### 6.1 泛型类&泛型方法&泛型变量



```Java
package demo02;

class Temp<T> implements TempInterface<String> {
    T a;
    T b;

    public T show(T a, T b) {
        return a;
    }

    public static <T> void showw(T a) {
        System.err.println("showw参数数据的类型" + a.getClass());
    }

    @Override
    public String show() {
        return "Default String";
    }
}

// Renamed interface
interface TempInterface<T> {
    T show();
}

public class Test02 {
    public static void main(String[] args) {
        Temp<String> temp = new Temp<String>();
        System.out.println("打印出类show参数数据类型" + temp.show("1", "2").getClass());
        Temp.showw(3.14); // Correct static method call
    }
}
//OUTPUTS:
打印出类show参数数据类型class java.lang.String
showw参数数据的类型class java.lang.Double
```

**类的泛型是 “实例专属”，静态方法是 “类专属”，两者不共享泛型参数。静态方法若需泛型，需自己单独声明。**