



​	**synchronized**: 隐式锁，自动释放。可修饰方法或代码块。

​	**Lock (ReentrantLock)**: 显式锁，必须手动 `lock()` 和 `unlock()`。

相比 `synchronized`，`Lock` 提供了更灵活的锁操作（手动上锁、解锁）

因为在锁时候要保证竞争同一把锁，在自定义类和匿名内部类这里有一捏捏的注意点，于是把这两种写法都给出

- **独占性**：当线程A通过 `lock.lock()` 获取锁后，它独占了该资源。

- **阻塞/等待**：线程B若执行到 `lock.lock()`，发现锁已被A持有，则会进入阻塞状态，直到线程A调用 `lock.unlock()` 释放锁。

    

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




        Thread temp1 = new MyThread();
        Thread temp2 = new MyThread();
        temp1.setPriority(10);
        temp1.setName("线程1");
        temp2.setName("线程2");
        //锁可以不允许2的概率发生，只有先进行1，如果设置了守护那么2就不会陆续结束而是直接结束
        temp2.setDaemon(true);

        temp1.start();
        temp2.start();

    }
}


public class MyThread extends Thread{
    //static！ 确保竞争一个锁
    static Lock lock = new ReentrantLock();
    private int count = 0;
    public void run()
    {
        while (true)
        {
            lock.lock();

            try {
                if(count == 100)
                    break;
                else {
                    //2.2 sleep()睡眠
                    Thread.sleep(100);
                    count++;
                    System.out.println("目前"+Thread.currentThread().getName()+"count:"+count);
                }
            }
            catch (Exception e)
            {

            }

            finally {
                lock.unlock();
            }

        }

    }
}

```

