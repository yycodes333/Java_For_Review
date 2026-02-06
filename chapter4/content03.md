### 4.3 System Runtime Math Random

​	数学与随机数



```Java
public class Test {
    public static void main(String[] args) {
       //System内的方法是static直接  类.方法即可
        System.currentTimeMillis();
        System.exit(0);
        //Runtime
        Runtime t = Runtime.getRuntime();
        try {
            t.exec("notepad.exe");// 打开记事本
        } catch (IOException e) {
            throw new RuntimeException(e);
        }

        //Math 内的方法是static直接  类.方法即可
        Math.abs(23);// 绝对值
        //Random 
        Random r = new Random();//这里不写固定参数 可以使得每刻时间戳不一样，每次运行结果tt不一样  若写了13等固定数据的话  每次生成tt是一个数据
      int tt =  r.nextInt(100);//生成100以内整数的随机一个数
    }
}
```

