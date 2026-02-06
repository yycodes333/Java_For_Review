

​	不可变字符串

内部是 `final byte[]` (JDK9+) 或 `char[]` (JDK8及以前)。每次修改都会创建新对象，效率低。

|                        方法声明                         |                           功能描述                           |
| :-----------------------------------------------------: | :----------------------------------------------------------: |
|                    ==int length()==                     |     **返回**当前**字符串的长度**，即字符串中字符的个数。     |
|                 ==int indexOf(int ch)==                 |        返回指定字符ch在字符串中第一次出现位置的索引。        |
|                 int lastIndexOf(int ch)                 |       返回指定字符ch在字符串中最后一次出现位置的索引。       |
|                 int indexOf(String str)                 | **返回**指定**子字符串**str在字符串**第一次出现**位置**的索引**。 |
|               int lastIndexOf(String str)               |   返回指定子字符串str在此字符串中最后一次出现位置的索引。    |
|               ==char charAt(int index)==                | **返回指定索引处的字符**: 返回字符串中index位置上的字符，其中index的取值范围0~(字符串长度-1)。 |
|             boolean endsWith(Stringsuffix)              |             判断此字符串是否以指定的字符串结尾。             |
|             ==boolean equals(Object obj)==              |       **比较**obj与当前字符串对象的**内容是否相同**。        |
|          boolean equalslgnoreCase(String str)           | 以**忽略大小写**的方式**比较**str与当前字符串对象的内容是否相同。 |
|              ==int compareTo(String str)==              | 按对应字符的Unicode编码比较str与当前字符串对象的大小。若当前字符串对象比str大，返回正整数;若比str小，返回负整数;若相等则返回0。 |
|           int compareTolgnoreCase(Stringstr)            | 按对应字符的Unicode编码以忽略大小写的方式比较str与当前字符串对象的大小。若当前字符串对象比str大，返回正整数;若比str小，返回负整数;若相等则返回0。 |
|                    boolean isEmpty()                    | 判断字符串长度是否为0，如果为0则返回true，反之则返回flase。  |
|            boolean startsWith(Stringprefix)             |          判断此字符串是否以指定的字符串prefix开始。          |
|          ==boolean contains(CharSequencecs)==           |           判断此字符串中是否包含指定的字符序列cs。           |
|                ==String toLowerCase()==                 |   使用默认语言环境的规则将String中的所有字符都转换为小写。   |
|                ==String toUpperCase()==                 |   使用默认语言环境的规则将String中的所有字符都转换为大写。   |
|              static String valueOf(int i)               |       **其他类型转为String**：将int变量i转换成字符串。       |
|                  char[] toCharArray()                   |                将此字符串转换为一个字符数组。                |
| String replace(CharSequenceoldstr, CharSequence newstr) | 使用newstr**替换**原**字符串**中的oldstr，返回一个新的字符串。 |
|                String concat(String str)                |               将str连接到当前字符串对象之后。                |
|            ==String[] split(String regex)==             |  根据参数regex将原来的字符串**分割**为若干个子**字符串**。   |
|            String substring(int beginIndex)             | 返回一个新字符串，它包含从指定的beginIndex处开始，直到此字符串末尾的所有字符。 |
|      String substring(int beginIndex,int endIndex)      | **截取子串，含头不含尾**：返回一个新字符串，它包含从指定的beginIndex处开始，直到索引 lendIndex-1处的所有字符。 |
|                    ==String trim()==                    |              **去除**了原字符串**首尾的空格**。              |