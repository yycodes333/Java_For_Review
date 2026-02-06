

- **背景**：CPU 性能过剩，单线程程序效率低。
- **解决问题**：让程序同时执行多个任务（并发），抢占 CPU 资源。
- **语法**：`Thread`, `Runnable`, `Lock`。

- **线程生命周期**

​	新建 (New) -> 就绪 (Runnable) -> 运行 (Running) -> 阻塞 (Blocked/Waiting) -> 死亡 (Terminated)