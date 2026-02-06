- **List**: 用途最广，替代数组。
- **Set**: 主要用于去重。
- **Map**: 处理对应关系（如 学号->学生）。
- **工具类**: `Collections.sort()` 和 `Arrays.sort()`。

- **遍历 List/Set**：增强 for、Iterator  

- **fail-fast**：遍历时结构性修改（add/remove）可能抛 `ConcurrentModificationException`；要删除用 `Iterator.remove()`

- **遍历 Map（最推荐）**：`entrySet()`（比 `keySet()+get()` 更高效）

  ```java
  for (Map.Entry<String, Integer> e : map.entrySet()) {
      System.out.println(e.getKey() + " -> " + e.getValue());
  }
  ```

- **HashMap 关键点（了解）**：hash → 桶；冲突用链表/红黑树（树化后提升查找性能）

- **equals/hashCode 契约（必会）**：相等对象 hashCode 必须相等；放入 HashSet/HashMap 的类一定要正确重写两者

