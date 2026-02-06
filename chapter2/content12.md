### 2.12 内部类

被定义在另一个类的内部，所以称为内部类（Nested Class）。

如果把商场看作一个外部类，商场有水果分区，蔬菜分区等等，而对于水果，又有香蕉、苹果、橙子等等，那么水果有看作为一个类，即商场类的内部类。

#### 1.成员内部类



1. 内部类单独存在无意义
2. 内部类依靠外部类

3. 内部类可直接访问外部类私有成员。

4. 外部类无法调用内部类方法/变量，需创建内部类对象访问内部成员。



```Java
package Demo;

public class Test {
    public static void main(String[] args) {
       Outer temp_outer = new Outer();
       //创建内部类
       Outer.Inner temp_inner = new Outer().new Inner();
        temp_inner.show();

    }
}
class Outer{

   int a = 2;
  public void show(){
      System.out.println("调用外部类的show方法");
      /*//采用创建对象调用内部类方法  无法直接调用内部类方法
      //new Inner().show();*/
  }
  class Inner{
       int a  = 22;
      int c = Outer.this.a;
      void show(){
          //局部变量
          int a = 222;
          //内部类直接调用外部类方法
          Outer.this.show();
          System.out.println("调用内部类show方法");
          //Outer.this 来指定外部类的成员变量
          System.out.println("外部类的a 等于 "+Outer.this.a);
          //采用this来调用成员变量
          System.out.println("内部类成员变量a  等于 "+ this.a);
          //就近原则
          System.out.println("内部类局部变量a 等于 "+a);

      }


  }


}
```



输出：



```java
	调用外部类的show方法
    调用内部类show方法
    外部类的a 等于2
    内部类成员变量a  等于 22
    内部类局部变量a 等于 222
```



#### 2.**匿名内部类**  +  Lambda简化



往往对于某些父类/接口只需要实现特定几个功能，临时使用，如果像之前需要重新写一个类，定义了很多不必要的内容，这样操作事倍功半，于是有了匿名内部类临时定义实例化来解决这类问题，用完即扔掉。



- **格式**：`new 接口/父类() { 重写方法 实现接口/继承类 }`

- **Lambda**：仅针对**函数式接口**——实现接口的匿名内部类进行简化（只有一个抽象方法的接口）。

    

  ```Java
  package Demo;
  
  public class Test {
      public static void main(String[] args) {
          //对于类实现继承关系  匿名内部类
          new temp5(){
              public void show(){
                  System.out.println("经过匿名内部类对类temp5的show方法进行了重写");
              }
          } .show();
          //对于接口实现  匿名内部类
  
          new temp1() {
              public void show_temp1() {
                  System.out.println("经过匿名内部类对对接temp1中show进行了重写");
              }
          }.show_temp1();
  
          //---------------------------------------------------------------------
          //对接口 进行 Lambda  匿名内部类简化-->只针对有一个方法的接口
  
          temp2 temp =
                  (int a, int b) -> {
                      System.out.println("经过Lambda对对接temp2中show进行了重写");
                      return a + b;
  
                  };
          System.out.println(temp.show_temp1(1, 2));
  
          //对接口 进行Lambda 进一步简化
          /*
          * 1. 若接口只有一个参数可把参数括号去掉
          * 2.若实现语句是由一行 ，可以去掉 return  ; 和{}  注意！！！这三个必须同时去掉！！！
          *
          * */
  
          temp2 tempp = (int a,int b)-> a+b;
  
  
          System.out.println("若输出结果是11那么就进行了Lambda的进一步简化   他的结果是  "+tempp.show_temp1(5,6)+"     进一步简化成功！");
      }
  }
  
  interface temp1 {
  
      void show_temp1();
  
  }
  
  interface temp2{
      public int  show_temp1(int a,int b);
  
  }
  
  
  
  class temp5{
      public void show()
      {
          System.out.println("temp没有重写");
      }
  
  }
  ```

  

  输出结果：

  

  ```shell
  经过匿名内部类对类temp5的show方法进行了重写
  
  经过匿名内部类对对接temp1中show进行了重写
  
  经过Lambda对对接temp2中show进行了重写
  3
  若输出结果是11那么就进行了Lambda的进一步简化，他的结果是 11  进一步简化成功!
  ```

  

