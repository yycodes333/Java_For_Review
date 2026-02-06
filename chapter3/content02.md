

-  getMessage() 
-  String toString() 
-  void printStackTrce()



```java
package Demo;

public class Test {
    public static void main(String[] args) {
        try{
            People p = new People(-12);
        }
        catch (Exception e) {
            System.out.println("捕获异常：" + e.getMessage());
        }
        finally {
            System.out.println("无论是否异常都执行");
        }
    }


}
//自定义异常
class TempException extends Exception {

    public TempException()
    {
        super();
    }
    public TempException(String mes)
    {
        super(mes);
    }

}

class People {

    public People(int age) throws TempException
    {
        if(age < 0){
            throw new TempException("输入年龄不符合要求");
        }
        else {
            System.out.println("输入年龄合理");
        }
    }
}
```

