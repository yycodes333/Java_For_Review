### 1.1 掌握动态、静态数组初始化



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

