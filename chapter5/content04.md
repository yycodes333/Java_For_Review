

#### 1.Collections 都是静态方法直接  类.方法



|                方法声明                 |                        功能描述                        |
| :-------------------------------------: | :----------------------------------------------------: |
|     static void reverse(List list)      |              反转指定List集合中元素的顺序              |
|     static void shuffle(List list)      |              随机打乱List集合中元素的顺序              |
|       static void sort(List list)       | 根据元素的自然顺序(从小到大)对List集合中的元素进行排序 |
| static void swap(List list,int i,int j) |  将指定List集合中索引为i的元素和索引为j的元素进行交换  |









#### 2.Arrays   



```Java
package Demo;

import java.io.IOException;
import java.util.*;

public class Test {
    public static void main(String[] args) {

    Integer[] arr = {5,6,8,1,2,3,7};
    //进行排序 这里因为Compare这个接口的泛型就得是包装类，所以参数数据类型不能是int  而得写 Integer
        Arrays.sort(arr,( Integer a, Integer b) -> a-b);
        for(int i: arr) //使用自动拆箱
        {
            System.out.println(i);
        }
    }
}

```

