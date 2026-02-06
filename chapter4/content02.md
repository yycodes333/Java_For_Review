### 4.2 StringBuffer & StringBuilder

​	可变字符串

Buffer线程安全 (synchronized)，效率低

Builder线程不安全，效率高 (推荐单线程使用)

|                    方法声明                     |                        功能描述                        |
| :---------------------------------------------: | :----------------------------------------------------: |
|                 StringBuffer()                  |      创建初始容量为16，不含任何内容的字符串缓冲区      |
|           StringBuffer(int capacity)            |   创建初始容量为capacity，不含任何内容的字符串缓冲区   |
|             StringBuffer(String s)              |   创建初始容量为s.length()+16，内容为s的字符串缓冲区   |
|                  int length()                   |              获取缓冲区中字符串内容的长度              |
|                 int capacity()                  |               获取字符串缓冲区的当前容量               |
|           StringBuffer append(char c)           |            **添加**参数到StringBuffer对象中            |
|   StringBuffer insert(int offset,String str)    |         在字符串的offset位置**插入**字符串str          |
|      StringBuffer deleteCharAt(int index)       |              **移除**此序列指定位置的字符              |
|     StringBuffer delete(int start,int end)      |    删除StringBuffer对象中指定范围的字符或字符串序列    |
| StringBuffer replace(int start,intend,String s) |     在StringBuffer对象中替换指定的字符或字符串序列     |
|       void setCharAt(int index, char ch)        |             修改指定位置index处的字符序列              |
|                String toString()                |            返回StringBuffer缓冲区中的字符串            |
|             StringBuffer reverse()              |                 **反转**内容反转字符串                 |
|           String substring(int start)           |     获取缓冲区中字符串从索引start(含)至末尾的子串      |
|       String substring(int start,int end)       | 获取缓冲区中字符串从索引start(含)至索引end(不含)的子串 |
|                String toString()                |          **转回String**：获取缓冲区中的字符串          |



与String区别：



- **可变性 (Mutability)**:

  - **String**: 是不可变对象（Immutable），一旦创建，其值不能被改变。
  - **StringBuffer**: 是可变对象（Mutable），可以直接修改字符串内容，不产生新对象。

- **线程安全 (Thread Safety)**:

  - **String**: 是线程安全的，因为它是不可变的。
  - **StringBuffer**: 是线程安全的，其方法使用 `synchronized` 修饰，适合多线程环境。

- **性能 (Performance)**:

  - **String**: 在频繁进行字符串拼接（如在循环中）时，性能较差，会生成大量临时对象。

  - **StringBuffer**: 在频繁修改字符串内容时，性能远高于 String。