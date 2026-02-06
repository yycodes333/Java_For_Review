### 2.3 this使用



- **区分变量**：在类的方法中，`this.成员变量` 用于区分局部变量和成员变量。
- **调用构造方法**：若想要调用本类其他构造方法，就必须在无参/有参构造方法中调用，且位于首行。
- **格式**：`this()` 或 `this(参数1,参数2,...)`。
- **互斥**：一个类中构造方法不可相互死循环调用。



```Java
public class Test {
    public static void main(String[] args) {
       
        new temp(2);

         
         
    }
    

}
class temp {
    private int a = 10;

   public temp(int a){
       this();
       this.a = a;
       System.out.println(a);
   }
   public temp(){
       System.out.println("成功调用无参构造");
       
   }

}
```

