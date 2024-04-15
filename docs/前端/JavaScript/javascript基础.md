#  JavaScript 数据类型



**值类型(基本类型)**：字符串（String）、数字(Number)、布尔(Boolean)、空（Null）、未定义（Undefined）、Symbol。

**引用数据类型（对象类型）**：对象(Object)、数组(Array)、函数(Function)，还有两个特殊的对象：正则（RegExp）和日期（Date）。

<img src="https://fastly.jsdelivr.net/gh/Konnor-Jade/image-host/img/202404151424484.png" alt="img" style="zoom:67%;" />

# [var let const 的区别](https://www.runoob.com/js/js-let-const.html)

在 JavaScript 中，`var`, `let`, 和 `const` 是用来声明变量的关键字，它们有几个关键的区别影响着变量的作用域、提升行为（hoisting），以及变量是否可以被重新赋值。

### var

- **作用域**：`var` 声明的变量有函数作用域，这意味着在函数内部声明的变量可以在整个函数内部访问，而在函数外部声明的变量则是全局的。
- **提升**：`var` 声明的变量会被提升至其作用域的顶部，但只有声明部分被提升，初始化部分不会。这意味着变量可以在声明之前被访问，但此时变量的值为 `undefined`。
- **重复声明**：在同一作用域内可以重复声明同一个变量。

```javascript
console.log(x); // 输出: undefined
var x = 5;
console.log(x); // 输出: 5
```

### let

- **作用域**：`let` 提供块级作用域，这意味着 `let` 声明的变量仅在它声明的代码块内部可见。
- **提升**：虽然 `let` 声明的变量也会提升到它们的作用域顶部，但它们不像 `var` 那样在声明之前就可以访问。在代码执行到声明之前的区域，该变量处于 "暂时性死区"（Temporal Dead Zone，TDZ），试图访问会抛出错误。
- **重复声明**：在同一作用域内不能重复声明同一个变量。

```javascript
// console.log(y); // Uncaught ReferenceError: Cannot access 'y' before initialization
let y = 10;
console.log(y); // 输出: 10
```

### const

- **作用域**：与 `let` 相同，`const` 也提供块级作用域。
- **提升**：`const` 的行为与 `let` 相似，包括 "暂时性死区" 的概念。
- **重复声明**：在同一作用域内不能重复声明。
- **重新赋值**：`const` 声明的变量必须在声明时初始化，且之后不能被重新赋值（但如果它是一个对象，对象的属性可以被修改）。

```javascript
const z = 20;
// z = 30; // TypeError: Assignment to constant variable.
console.log(z); // 输出: 20
```

## Hoisting（变量提升）

Hoisting 是 JavaScript 的默认行为，它会将所有的变量声明（注意是声明而不是初始化）和函数声明提升到当前作用域的顶部。对于 `var` 声明的变量，这意味着无论它们实际在代码中的位置如何，都被视为在函数或全局作用域的顶部声明的。然而，对于 `let` 和 `const`，尽管提升发生，但它们在声明语句之前都处于不可访问的状态，这是所谓的 "暂时性死区"。



# undefined 和 null 的区别

在 JavaScript 中，`undefined` 和 `null` 都代表缺少值，但它们在用途和意义上有重要的区别。

### undefined

- **含义**：`undefined` 表示变量已被声明但尚未被赋值。它是变量的默认初始值。
- **常见场景**：
  - 声明变量后未初始化时，变量的默认值是 `undefined`。
  - 函数没有明确返回值时，默认返回 `undefined`。
  - 对象属性不存在时，访问该属性会返回 `undefined`。
- **示例**：
  ```javascript
  let a;
  console.log(a); // 输出: undefined
  
  function test() {}
  console.log(test()); // 输出: undefined
  
  const obj = {};
  console.log(obj.property); // 输出: undefined
  ```

### null
- **含义**：`null` 是一个特殊的关键字，表示变量的值为“无”或“空”。它是一个只有一个值的数据类型，即 `null` 自身，用于表示没有任何对象值的存在。
- **常见场景**：
  - 当你需要手动指定变量为空或不存在对象时，可以使用 `null`。
  - 在进行数据库查询等操作时，`null` 常用于表示缺失的、未知的或不适用的数据。
- **示例**：
  
  ```javascript
  let b = null;
  console.log(b); // 输出: null
  ```

### 主要区别
- **语义**：`undefined` 通常表示系统级的、从未被赋值的状态，而 `null` 表示程序员级的、赋值了但没有对象的空值。
- **类型**：在 JavaScript 的类型系统中，`undefined` 是自己的类型，即 `undefined`，而 `null` 是一个对象。
- **检测**：你可以使用 `typeof` 运算符来检测 `undefined` 值，它会返回 `"undefined"`。对于 `null`，`typeof` 返回 `"object"`，这是历史原因造成的错误。
- **转换**：在布尔上下文中，如 `if` 语句中，`undefined` 和 `null` 都会被自动转换为 `false`。
- **等价性**：使用双等号 (`==`) 比较时，`undefined` 和 `null` 是相等的；使用三等号 (`===`) 比较时，它们是不相等的，因为它们是不同类型的值。
  ```javascript
  console.log(undefined == null);  // 输出: true
  console.log(undefined === null); // 输出: false
  ```

# JavaScript 异步编程

异步（Asynchronous, async）是与同步（Synchronous, sync）相对的概念。

在我们学习的传统单线程编程中，程序的运行是同步的（同步不意味着所有步骤同时运行，而是指步骤在一个控制流序列中按顺序执行）。而异步的概念则是不保证同步的概念，也就是说，一个异步过程的执行将不再与原有的序列有顺序关系。

![同步异步的区别](https://fastly.jsdelivr.net/gh/Konnor-Jade/image-host/img/202404151933804.png)

## 回调函数 (Callback Function)

**定义：**

- 回调函数是一个作为参数传递给另一个函数的函数，并在该外部函数完成某种操作后被调用。回调函数允许一段代码在完成某个任务后通知或影响另一段代码。

**用途：**

- 在 JavaScript 中，回调函数通常用于处理异步操作，如**网络请求、文件操作或定时事件**。通过回调函数，JavaScript 可以在不阻塞主线程的情况下执行这些操作，当操作完成后再执行回调以处理结果。

**示例**：
```javascript
function greeting(name) {
  alert('Hello ' + name);
}

function processUserInput(callback) {
  var name = prompt('Please enter your name.');
  callback(name);
}

processUserInput(greeting);  // 用户输入名字后，显示问候语
```
在这个例子中，`greeting` 函数作为回调传递给 `processUserInput` 函数。用户输入名字后，`greeting` 通过 `callback(name)` 被调用。

## setTimeout

**定义**：
- `setTimeout` 是一个 Web API，用于在指定的延迟后执行一段代码或函数。它不会立即执行代码，而是等待指定的毫秒数后将函数调度到 JavaScript 事件队列中。

**用途**：
- `setTimeout` 常用于延迟执行任务，如动画、延迟提示、调节事件发生的频率（节流和防抖）等。
- 它也可以用于将长时间运行的操作分解成小块，避免阻塞主线程。

**示例**：

```javascript
console.log('Start');
setTimeout(function() {
  console.log('This message is shown after 3 seconds');
}, 3000);
console.log('End');
```
在这个例子中，`setTimeout` 将一个匿名函数延迟 3000 毫秒后执行。输出将是 "Start"、"End"，然后 3 秒后显示 "This message is shown after 3 seconds"。

## 注意事项

- **非阻塞行为**：`setTimeout` 是非阻塞的，这意味着它不会等待时间到了再继续执行代码。代码的剩余部分会立即执行，当延迟时间过去后，设置的函数才会被执行。
- **最小延迟**：浏览器通常对 `setTimeout` 的最短延迟有一个下限（通常是 4ms），即使设置的延迟时间比这更短，实际延迟也可能长于所请求的延迟。

# [Promise](https://www.runoob.com/js/js-promise.html)

格式

```js
new Promise(function (resolve, reject) {
    // 要做的事情...
});

// ==================================================
new Promise(function (resolve, reject) {
    setTimeout(function () {
        console.log("First");
        resolve();
    }, 1000);
}).then(function () {
    return new Promise(function (resolve, reject) {
        setTimeout(function () {
            console.log("Second");
            resolve();
        }, 4000);
    });
}).then(function () {
    setTimeout(function () {
        console.log("Third");
    }, 3000);
});
```



## Promise 的构造函数

Promise 构造函数是 JavaScript 中用于创建 Promise 对象的内置构造函数。 

Promise 构造函数**接受一个函数作为参数**，该函数是同步的并且会被立即执行，所以我们称之为**起始函数**。起始函数包含两个参数 **resolve 和 reject**，分别表示 Promise 成功和失败的状态。

起始函数执行成功时，它应该调用 resolve 函数并传递成功的结果。当起始函数执行失败时，它应该调用 reject 函数并传递失败的原因。

Promise 构造函数返回一个 Promise 对象，该对象具有以下几个方法：

- **then**：用于处理 Promise 成功状态的回调函数。
- **catch**：用于处理 Promise 失败状态的回调函数。
- **finally**：无论 Promise 是成功还是失败，都会执行的回调函数。

下面是一个使用 Promise 构造函数创建 Promise 对象的例子：

当 Promise 被构造时，起始函数会被同步执行：

```javascript
const promise = new Promise((resolve, reject) => {
  // 异步操作
  setTimeout(() => {
    if (Math.random() < 0.5) {
      resolve('success');
    } else {
      reject('error');
    }
  }, 1000);
});
 
promise.then(result => {
  console.log(result);
}).catch(error => {
  console.log(error);
});
```

在上面的例子中，我们使用 Promise 构造函数创建了一个 Promise 对象，并使用 setTimeout 模拟了一个异步操作。如果异步操作成功，则调用 resolve 函数并传递成功的结果；如果异步操作失败，则调用 reject 函数并传递失败的原因。然后我们使用 then 方法处理 Promise 成功状态的回调函数，使用 catch 方法处理 Promise 失败状态的回调函数。

这段程序会直接输出 **error** 或 **success**。

resolve 和 reject 都是函数，其中调用 resolve 代表一切正常，reject 是出现异常时所调用的

## 实例

Promise 类有 .then() .catch() 和 .finally() 三个方法，这三个方法的参数都是一个函数，.then() 可以将参数中的函数添加到当前 Promise 的正常执行序列，.catch() 则是设定 Promise 的异常处理序列，.finally() 是在 Promise 执行的最后一定会执行的序列。 .then() 传入的函数会按顺序依次执行，有任何异常都会直接跳到 catch 序列：

```JavaScript
new Promise(function (resolve, reject) {
    console.log(1111);
    resolve(2222);
}).then(function (value) {
    console.log(value);
    return 3333;
}).then(function (value) {
    console.log(value);
    throw "An error";
}).catch(function (err) {
    console.log(err);
});
```

执行结果：

```bash
1111
2222
3333
An error
```

resolve() 中可以放置一个参数用于向下一个 then 传递一个值，then 中的函数也可以返回一个值传递给 then。但是，如果 then 中返回的是一个 Promise 对象，那么下一个 then 将相当于对这个返回的 Promise 进行操作，这一点从刚才的计时器的例子中可以看出来。

reject() 参数中一般会传递一个异常给之后的 catch 函数用于处理异常。