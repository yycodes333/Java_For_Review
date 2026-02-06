



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
        2.2 sleep()失眠
        2.3 CurrentThread()
        2.4 set/getPriority()  1 <  5 < 10(最优先)
        2.4 yield()礼让
        2.5 join()插入
        2.6 Daemon()守护
      说明：
      属性配置类方法（如设置名称、优先级、守护线程）需在start()前调用；
      行为类方法（如休眠、礼让、插入）需在start()后调用；获取信息的方法无时间限制。

    * */
    private static final Lock lock = new ReentrantLock();

                // 线程1：temp1（先执行）
                Thread temp1 = new Thread(() -> {
                    Thread.currentThread().setName("线程1");
                    lock.lock(); // 只加1次锁（覆盖整个任务）
                    try {
                        for (int i = 0; i < 10; i++) {
                            Thread.sleep(10);
                            System.out.println(Thread.currentThread().getName() + " " + i);
                        }
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    } finally {
                        lock.unlock(); // 对应解锁1次，释放锁
                    }
                });

                // 线程2：temp2（等待temp1释放锁）
                Thread temp2 = new Thread(() -> {
                    Thread.currentThread().setName("线程2");
                    lock.lock(); // 等待temp1释放锁
                    try {
                        for (int i = 0; i < 100; i++) {
                            System.out.println(Thread.currentThread().getName() + " " + i);
                        }
                    } finally {
                       lock.unlock();
                    }
                });

                temp1.setPriority(10); // 提高优先级（增加先调度的概率）
                // 去掉守护线程，避免temp2被提前终止
                // temp2.setDaemon(true);
                temp2.setDaemon(true);
                temp1.start();
                temp2.start();

        // main线程（等待temp1释放锁）
        // main线程（等待temp1先启动并抢锁）
        try {
            Thread.sleep(10); // 延迟10ms，给temp1启动时间
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        lock.lock();
        try {
            for (int i = 0; i < 50; i++) {
                System.out.println(Thread.currentThread().getName() + " " + i);
            }
        } finally {
            lock.unlock();
        }

    }
}
```











