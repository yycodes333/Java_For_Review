### 5.1 List



- ArrayList,

- LinkedList

    

**特点**：==有序==、==可重复==、==有索引== 。

**遍历**：普通for（可改）、增强for（不可改）、迭代器（可删除）。

**ArrayList**: 底层是**数组**。***<u>查询快</u>***，***<u>增删慢</u>***（需**移动元素**）。

**LinkedList**: 底层是**双向链表**。***<u>查询慢</u>***，***<u>增删快</u>***（**首尾操作**）。

#### 1.API（针对**ArrayList**）

|                 方法声明                  |                           功能描述                           |
| :---------------------------------------: | :----------------------------------------------------------: |
|         ==boolean add(Object o)==         |                     向集合中添加一个元素                     |
|       boolean addAll(Collection c)        |            将指定集合c中的所有元素添加到本集合中             |
|             ==void clear()==              |                     删除集合中的所有元素                     |
|       ==boolean remove(Object o)==        |                     删除集合中指定的元素                     |
|      boolean removeAll(Collection c)      |             删除当前集合中包含集合c中的所有元素              |
|         ==Object get(int index)==         |                  返回集合index索引处的元素                   |
|       ==Object remove(int index)==        |                    删除index索引处的元素                     |
|   Object set(int index, Object element)   |   将index索引处元素替换成element对象，并将替换后的元素返回   |
|           int indexOf(Object o)           |            返回对象o在List中第一次出现的位置索引             |
|         int lastIndexOf(Object o)         |           返回对象o在List中最后一次出现的位置索引            |
| List subList (int fromIndex, int toIndex) | 返回从索引fromIndex(包括)到toIndex(不包括)处所有元素集合组成的子集合 |



#### 2.遍历  



- 涉及 3种遍历方法  

- ***增强for无法修改其中元素问题***   ***迭代器删除注意事项***   

- 补充工具类使用匿名内部类和Lambda简化自定义排序





```Java
package Demo;

import java.io.IOException;
import java.util.*;

public class Test {
    public static void main(String[] args) {

        ArrayList<Integer> temp = new ArrayList<>();

        temp.add(5);
        temp.add(2);
        temp.add(1);
        temp.add(4);

        //第一种遍历 ->for循环（ 可以修改列表中的元素）
        System.out.println("使用for循环遍历列表");
        for(int i = 0; i < temp.size(); i++) {
            System.out.println(temp.get(i));
        }
        System.out.println("使用增强for循环遍历列表");
      
        //第二种遍历 ->增强for循环（不可以修改列表中元素）
        for(int i:temp){  //由于 ArrayList<Integer> temp = new ArrayList<>();我这里使用了泛型，那么取得temp中的是Integer类型 ，然后因为自动拆箱可以这么写
            System.out.println(i);
            //如果没有自动拆箱： object i =  temp，然后采用向下转型解决该问题
        }

        //第三种遍历 ->Itrator 迭代器 （删除列表中元素需要使用迭代器删除）
        System.out.println("使用迭代器遍历列表");
        Iterator<Integer> it = temp.iterator();
        while(it.hasNext()) {
            int i = it.next();//同样采用了自动拆箱
            System.out.println(i);
        }
        

        
        //插入一种排序 使用匿名内部类
        Collections.sort(temp, new Comparator<Integer>() {
            @Override//翻译：覆盖，要求：非必要，仅书写一般要求
            public int compare(Integer o1, Integer o2) {
                return o1-o2;
            }
        });

        //这里再次遍历看结果
        System.out.println("输出排序完的结果");
        Iterator<Integer> it2 = temp.iterator();
        while(it2.hasNext()) {
            int i = it2.next();//同样采用了自动拆箱
            System.out.println(i);
        }
        //同样采用Lambda 进行优化
        System.out.println("输出经过Lambda排序完的结果");

        Collections.sort(temp,

                (Integer o1, Integer o2) ->{
                    return o2-o1;
                }
        );
        Iterator<Integer> it3 = temp.iterator();
        while(it3.hasNext()) {
            int i = it3.next();//同样采用了自动拆箱
            System.out.println(i);
        }


        //这里说明 Itetator 迭代器删除问题
        System.out.println("这里进行迭代器删除操作");
        Iterator<Integer> it4 = temp.iterator();
        while(it4.hasNext()) {
            int i = it4.next();
            if(i == 5) {
                it4.remove();
            }
        }
        System.out.println("给出删除后的列表");
        Iterator<Integer> it5 = temp.iterator();
        while(it5.hasNext()) {
            int i = it5.next();
            System.out.println(i);
        }


        System.out.println("这里讲解增强for循环不能修改列表元素");
        for(int i: temp) {
            if(i==4) {
                i=3;
            }
        }
        System.out.println("给出for修改后的元素,发现并没有将4修改成3");

        for(int i: temp) {
            System.out.println(i);
        }

    }
}
```

