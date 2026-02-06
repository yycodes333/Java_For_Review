### 5.2 Set   



- HashSet

-  TreeSet

     

**特点**：***<u>无序</u>***、***<u>去重</u>***。

**去重原理**：

​	**HashSet**: 依赖 `hashCode()` 和 `equals()`。

​	**TreeSet**: 依赖 `Comparable` 接口或 `Comparator` 比较器。



- 所具备的添加元素等操作与List类似
- 讲解HashSet（仅去重，输出结果与输入顺序比匹配）

#### 1.HashCode去重操作演示

```Java
package Demo;

import java.io.IOException;
import java.util.*;

public class Test {
    public static void main(String[] args) {

        HashSet<Student> temp  = new HashSet<>();
        Student s1 = new Student(18,"张三");
        Student s2 = new Student(18,"张三");
        Student s3 = new Student(19,"王五");
        Student s4 = new Student(20,"马六");

        temp.add(s1);
        temp.add(s2);
        temp.add(s3);
        temp.add(s4);

        Iterator<Student> it = temp.iterator();
        while (it.hasNext()){
            Student tt = it.next();
            System.out.println(tt);
        }
    }
}
```



```Java
package Demo;

import java.util.Objects;

public class Student {

    private int age;
    private String name;

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public Student(int age, String name) {
        this.age = age;
        this.name = name;
    }

/*    //此处自定义排序顺序 首先仅仅比较名字

    public int hashCode(){
        return Objects.hash(name);
    }

    public boolean equals(Student s){

        if(this == s) return true;

        return this.name.equals(s.name);

    }*/


        //此处自定义排序顺序 当名字和年龄都相同才能去重

    public int hashCode(){
        return Objects.hash(age,name);
    }

    public boolean equals(Object obj){

        if(this == obj) return true;

      if(!(obj instanceof Student))return false;

      Student s = (Student) obj;

      return this.age==s.age && this.name.equals(s.getName());


    }
    public String toString()
    {
        return "姓名:"+this.getName()+"    年龄:"+String.valueOf(this.getAge());
    }


}
```



#### 2.TreeSet  与HashSet不同的是既去重又排序



```Java
package Demo;

import java.io.IOException;
import java.util.*;

public class Test {
    public static void main(String[] args) {
        //也可以采取用Lambda
        TreeSet<Student> temp = new TreeSet<>(new Comparator<Student>() {
            //这里采取先比较年龄再比较姓名
            public int compare(Student o1, Student o2) {
                return o1.getAge()== o2.getAge() ? o1.getName().compareTo(o2.getName())
                                 : o1.getAge()-o2.getAge();
            }
        });
        Student s1 = new Student(18,"张三");
        Student s2 = new Student(18,"阿Q");
        Student s3 = new Student(19,"王五");
        Student s4 = new Student(20,"马六");

        temp.add(s1);
        temp.add(s2);
        temp.add(s3);
        temp.add(s4);


        Iterator<Student> it = temp.iterator();
        while (it.hasNext()) {
            Student tt = it.next();
            System.out.println(tt);
        }


    }
}
```

