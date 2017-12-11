# Javascript Style Guide

## 目录

1. [References](#references)

## References

* [1.1] 使用`const`来声明只读常量；避免使用`var`

  > 确保常量不被重新赋值

  ```javascript
  // bad
  var a = 1;
  var b = 2;

  // good
  const a = 1;
  const b = 1;
  ```

- [1.2] 使用`let`来声明变量；避免需要`var`

  > `let`声明的变量仅在块级作用域内有效

  ```javascript
  // bad
  var count = 1;
  if (true) {
    count += 1;
  }

  // good
  let count = 1;
  if (true) {
    count += 1;
  }
  ```

**[🚀 回到顶部](#目录)**
