### 9.1 API常用



```java
package Demo02;

import java.util.concurrent.locks.Lock;
import java.util.concurrent.locks.ReentrantLock;

public class Text02 {
    public static void main(String[] args){
    /*
       任务:
    * 1.创建多线程
    * 2.多线程常用API
        2.1 getName/Setname->Thread类中
        2.2 sleep()睡眠
        2.3 CurrentThread()  获取此线程
        2.4 set/getPriority()  1 <  5 < 10(最优先)  概率性发生，并非绝对
        2.5 Daemon()守护  当非守护的线程都结束时候，守护线程会陆续结束
       	2.6	对于yield（）礼让， join() 插入不常用 ，了解即可
      说明：
      属性配置类方法（如设置名称、优先级、守护线程）需在start()前调用；
      行为类方法（如休眠、礼让、插入）需在start()后调用；获取信息的方法无时间限制。

    * */



        //1.创建
        Thread temp1 = new Thread(() -> {


            //2.1 setName() +   2.3 CurrentThread()
            Thread.currentThread().setName("线程1");
            for (int i = 0; i < 10; i++) {

                //2.2 getName() +  2.3 CurrentThread()
                System.out.println(Thread.currentThread().getName() +" " + i);

            }

        });

        Thread temp2 = new Thread(() -> {
            //2.1 setName() +   2.3 CurrentThread()
            Thread.currentThread().setName("线程2");
            for (int i = 0; i < 50; i++) {
                //2.2 getName() +  2.3 CurrentThread()

                System.out.println(Thread.currentThread().getName() +" " + i);
            }

        });

        //2.4 set/getPriority()  1 <  5 < 10(最优先)
        temp1.setPriority(10);
        //2.5 Daemon()守护  即当其他线程完成时候，此线程没必要继续进行，会陆续关闭
        temp2.setDaemon(true);

        //多线程的开启
        temp1.start();
        temp2.start();
        //  main线程
        for (int i = 0; i < 100; i++) {
            System.out.println(Thread.currentThread().getName()+" " + i);
        }



    }
}
```

