​		禁止直接 `new Thread()`，应使用线程池管理资源。

- **线程池（ExecutorService）**：统一管理线程、复用线程、避免频繁创建销毁  

  

  ```java
  ExecutorService pool = Executors.newFixedThreadPool(4);
  pool.submit(() -> System.out.println(Thread.currentThread().getName()));
  pool.shutdown();
  ```

- **Callable + Future（有返回值）*

  

  ```java
  Future<Integer> f = pool.submit(() -> 1 + 2);
  System.out.println(f.get());
  ```

  

- **volatile**：保证可见性（不保证复合操作原子性）

    

- **AtomicInteger**：原子自增等无锁操作（比 synchronized 更轻量）





