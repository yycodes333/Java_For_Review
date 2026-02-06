### 2.6 super



1.调用父类***==非私有==***成员变量和成员方法。

2.调用父类构造方法：在子类构造方法***==首行==***。

3.子类必须调用父类构造方法，默认调用父类无参构造方法，

​	若是父类有参构造方法，必须在构造方法中首行`super(参数1，...)`。



```java
public class Test {
    public static void main(String[] args) {
       
        new temp(2);

         
         
    }
    

}
class temp extends temp_father{
    private int a = 10;

   public temp(int a){
       this();
       this.a = a;
       System.out.println(a);
   }
   public temp(){
        super(1);
        System.out.println(super.x);
       System.out.println("成功调用无参构造");
       
   }

}
class temp_father {
    // public temp_father(){
    //     System.out.println("成功调用父类无参构造");
    // }
    public int x = 10;
    public temp_father(int a){
        System.out.println("成功调用父类有参构造");
    }
}
```

