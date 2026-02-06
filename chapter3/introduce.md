

- **背景**：代码运行时可能出现文件找不到、网络断开等问题。

- **解决问题**：防止程序因错误直接崩溃，提供补救机会。

- **语法**：`try-catch-finally`, `throw`, `throws`。

- **异常体系**

  - **Error**: 系统级错误 (如 `OutOfMemoryError`)，无法捕获。



```shell
- **Exception**:

  **Checked Exception (编译时异常)**: 必须 try-catch 或 throws (如 `IOException`)。

  **Runtime Exception (运行时异常)**: 逻辑错误 (如 `NullPointerException`, `IndexOutOfBoundsException`)
```



