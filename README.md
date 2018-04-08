# Javascript Style Guide

## 目录

1.  [References](#references)

## 变量声明

* [1.1] 使用`const`来声明只读常量；避免使用`var`

  > 确保常量不被重新赋值

  ```javascript
  // bad
  var a = 1
  var b = 2

  // good
  const a = 1
  const b = 1
  ```

* [1.2] 使用`let`来声明变量；避免需要`var`

  > `let`声明的变量仅在块级作用域内有效

  ```javascript
  // bad
  var count = 1
  if (true) {
    count += 1
  }

  // good
  let count = 1
  if (true) {
    count += 1
  }
  ```

## 注释

* [1.3] 短代码注释保持和代码在同一行，长代码注释在代码块上一行注释

```js
// bad
  GET_WX_APPID: '420601',
  // 600805-微信分享活动-猜比赛-选择竞猜选项
  CHOSE_WX_ACTIVITY: '600805',
  // 600806-微信分享活动-猜比赛-参与用户列表
  GET_WX_ACTIVITY_USERS: '600806',

// good
  GET_DRAWS_FISH_BALL: '600409', // 查询用户可抽奖鱼丸数
  GET_DRAWS_TIMES: '600412', // 获取用户剩余兑换次数【京东E卡/红包彩金】

// good
  GET_WX_APPID: '420601',

  // 600805-微信分享活动-猜比赛-选择竞猜选项
  CHOSE_WX_ACTIVITY: '600805',

  // 600806-微信分享活动-猜比赛-参与用户列表
  GET_WX_ACTIVITY_USERS: '600806',
```

* [1.4] Component 命名应该有意义

  > 方便阅读和检索

  ```js
  // bad
  class Node extends Component

  // good
  class DrawList extends Component
  ```

## 对象

* [1.5] 使用方法缩写

```js
// bad
const atom = {
  value: 1,
  addValue: function(value) {
    return atom.value + value
  },
}

// good
const atom = {
  value: 1,
  addValue(value) {
    return atom.value + value
  },
}
```

* [1.6] 使用属性缩写

```js
const lukeSkywalker = 'Luke Skywalker'

// bad
const obj = { lukeSkywalker: lukeSkywalker }

// good
const obj = { lukeSkywalker }
```

## 函数

* [1.7] 设置参数默认值

```js
// really bad
function handleThings(opts) {
  // No! We shouldn’t mutate function arguments.
  // Double bad: if opts is falsy it'll be set to an object which may
  // be what you want but it can introduce subtle bugs.
  opts = opts || {}
  // ...
}

// still bad
function handleThings(opts) {
  if (opts === void 0) {
    opts = {}
  }
  // ...
}

// good
function handleThings(opts = {}) {
  // ...
}
```

* [1.8] 将默认参数放在后面

```js
// bad
function handleThings(opts = {}, name) {
  // ...
}

// good
function handleThings(name, opts = {}) {
  // ...
}
```

* [1.9] 禁止修改参数

```js
// bad
function f1(a) {
  a = 1
  // ...
}

function f2(a) {
  if (!a) {
    a = 1
  }
  // ...
}

// good
function f3(a) {
  const b = a || 1
  // ...
}

function f4(a = 1) {
  // ...
}
```

* [1.10] 参数过长时使用对象传参

```js
// bad
function f1(a, b, c, d) {
  // ...
}

// good
function f2({ a, b, c, d }) {
  // ...
}
```

## 比较运算符

* [1.11] 使用 `===` 和 `!==` 代替 `==` 和 `!=`

* [1.12] falsy 值的使用
  > 布尔值直接使用缩写，字符串则与`''`进行比较，数值则与`0`进行比较

```js
// bad
if (isValid === true) { // ... }

// good
if (isValid) { // ... }

// bad
if (name) { // ... }

// good
if (name !== '') { // ... }

// bad
if (collection.length) { // ... }

// good
if (collection.length > 0) { // ... }
```

* [1.12] 避免使用不必要的三元符

```js
// bad
const foo = a ? a : b
const bar = c ? true : false
const baz = c ? false : true

// good
const foo = a || b
const bar = !!c
const baz = !c
```

## 命名协议

* [1.13] 避免使用单字符命名

```js
// bad
function q() { // ... }

// good
function query() { // ... }
```

* [1.14] 使用驼峰法命名

```js
// bad
const OBJEcttsssss = {}
const this_is_my_object = {}
function c() {}

// good
const thisIsMyObject = {}
function thisIsMyFunction() {}
```

* [1.14] 如果属性/方法是一个布尔型，使用 `isVal()` 或者 `hasVal()`

```js
// bad
if (!dragon.age()) {
  return false
}

if (boy) {
  return 'He is a boy'
}

// good
if (!dragon.hasAge()) {
  return false
}

if (isBoy) {
  return 'He is a boy'
}
```

**[🚀 回到顶部](#目录)**
