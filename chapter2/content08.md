

1.***==抽象方法的类必须是抽象类，但是抽象类也可以有普通方法==***。

2.***==子类继承抽象类，必须重写所有抽象方法，除非子类也是抽象类==***。



```java
public class Test {
    public static void main(String[] args) {
       
        new temp().func1();
        new temp().func2();

         
         
    }
    

}
class temp extends temp_father{
    

   public temp(){
       
        
       System.out.println("成功调用无参构造");
       
   }
   public void func1(){
       System.out.println("成功重写抽象方法");
   }

}
abstract class temp_father {
   
   
    public abstract void func1();
    public void func2(){
        System.out.println("拥有抽象方法中非抽象方法");
    }
}
```

