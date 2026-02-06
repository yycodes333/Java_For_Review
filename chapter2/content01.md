```java
public class ArrayDemo {
    public static void main(String[] args) {
        // 静态初始化数组：直接指定内容
        int[] arr1 = {1, 2, 3, 4, 5};
        
        // 动态初始化数组：指定长度
        int[] arr2 = new int[5];
        
        int count = 0;
        // 增强for循环遍历 arr1
        for (int i : arr1) {
            arr2[count++] = i; // 赋值
            System.out.println(i);
        }
        
        // 遍历 arr2
        for (int i : arr2) {
            System.out.println(i);
        }
    }
}
```



|   访问范围   | private私有 | default默认 | protected受保护 | public公共 |
| :----------: | :---------: | :---------: | :-------------: | :--------: |
|   同一类中   |      √      |      √      |        √        |     √      |
| 同一包中的类 |             |      √      |        √        |     √      |
| 不同包的子类 |             |             |        √        |     √      |
|   全局范围   |             |             |                 |     √      |



```java
public class Test {
    public static void main(String[] args) {
        test t = new test();
        System.out.println("a的结果"+t.a);
        System.out.println("b的结果"+t.b);
        System.out.println("c的结果"+t.c);
        //报错，因为d是private
        //System.out.println(t.d);


    }

}
class test {
    //定义变量a,b,c,d，并赋值1,2,3,4
    public int a = 1;
    protected int b = 2;
    int c  = 3;
    private int d = 4;

}
```

