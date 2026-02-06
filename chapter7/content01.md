

**InputStream**



|                   方法                   | 描述                                                         |                           示例代码                           |
| :--------------------------------------: | :----------------------------------------------------------- | :----------------------------------------------------------: |
|              ==int read()==              | ==读取一个字节的数据==，返回值为 0 到 255 之间的整数。如果到达流的末尾，返回 -1。 |               `int data = inputStream.read();`               |
|            int read(byte[] b)            | 从输入流中读取字节，并将其存储在字节数组 `b` 中，返回实际读取的字节数。如果到达流的末尾，返回 -1。 | `byte[] buffer = new byte[1024]; int bytesRead = inputStream.read(buffer);` |
| ==int read(byte[] b, int off, int len)== | 从输入流中读取最多 ==len个字节==，并将它们存储在字节数组 `b` 的 `off` 偏移位置，返回实际读取的字节数。如果到达流的末尾，返回 -1。 | `byte[] buffer = new byte[1024]; int bytesRead = inputStream.read(buffer, 0, buffer.length);` |
|           ==int available()==            | 返回可以读取的字节数（不阻塞）。                             |       `int availableBytes = inputStream.available();`        |
|             ==void close()==             | 关闭输入流并释放与该流相关的所有资源。                       |                    `inputStream.close();`                    |
|              `void reset()`              | 将流重新定位到上次标记的位置，如果没有标记或标记失效，抛出 `IOException`。 |                    `inputStream.reset();`                    |



**OutputStream**



|                    方法                    | 描述                                                         |                           示例代码                           |
| :----------------------------------------: | ------------------------------------------------------------ | :----------------------------------------------------------: |
|             void write(int b)              | 将指定的字节写入输出流，`b` 的低 8 位将被写入流中。          |                  `outputStream.write(255);`                  |
|           `void write(byte[] b)`           | 将字节数组 `b` 中的所有字节写入输出流。                      | `byte[] data = "Hello".getBytes(); outputStream.write(data);` |
| ==void write(byte[] b, int off, int len)== | 将字节数组 `b` 中从偏移量 `off` 开始的 `len` 个字节写入输出流。 | `byte[] data = "Hello".getBytes(); outputStream.write(data, 0, data.length);` |
|               `void flush()`               | 刷新输出流并强制写出所有缓冲的数据，确保数据被立即写入目标输出。 |                   `outputStream.flush();`                    |
|              ==void close()==              | 关闭输出流并释放与该流相关的所有资源。关闭后不能再写入。     |                   `outputStream.close();`                    |



