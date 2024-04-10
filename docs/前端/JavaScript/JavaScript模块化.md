## JavaScript 模块化

在 JavaScript 的世界中，模块化是一种将大的代码库分解成可维护的小块的技术。模块化可以让代码更容易理解、测试和维护。JavaScript 有两种主流的模块化标准：CommonJS 和 ES6 模块。

## CommonJS

CommonJS 是服务器端模块的标准，Node.js 采用了这种方式。它的主要特点是允许模块同步加载，适用于服务器端，因为服务器上文件通常已经存在，读取文件（即加载模块）的操作可以同步进行，几乎不会有延迟。

**使用 CommonJS 的例子**:

### 导出模块：

CommonJS 使用 `module.exports` 对象导出模块。你可以导出一个对象、函数、或者任何其他值。当导出一个模块时，你实际上是将 `module.exports` 指向了你想导出的值。

```javascript
// math.js
module.exports = {
  add: function(a, b) {
    return a + b;
  },
  subtract: function(a, b) {
    return a - b;
  }
};

或者

// math.js
function add(a, b) {
  return a + b;
}

function subtract(a, b) {
  return a - b;
}

module.exports = { add, subtract };


或者 逐个设置导出的属性或者方法

// math.js
exports.add = function(a, b) {
  return a + b;
};

exports.subtract = function(a, b) {
  return a - b;
};
```

### 导入模块：

使用 `require()` 函数导入模块。`require()` 函数接受一个模块路径作为参数，并返回该模块的 `module.exports` 对象。

```javascript
// app.js
const math = require('./math.js');

console.log(math.add(2, 3)); // 5
console.log(math.subtract(5, 2)); // 3
```

## ES6 Modules

ES6 模块化是 ECMAScript 2015 (也就是 ES6) 引入的，旨在浏览器和服务器共用。与 CommonJS 不同，ES6 模块设计用于静态分析和异步加载。

**使用 ES6 模块的例子**:

### 导出模块：:

- 命名导出：可以导出多个值，并且必须使用相同的名称导入它们。

```javascript
// math.js
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;
```

- 默认导出：每个模块只能有一个默认导出，导入时可以使用任意名称。

```javascript
// calculator.js
export default class Calculator {
  add(a, b) {
    return a + b;
  }

  subtract(a, b) {
    return a - b;
  }
}
```

### 导入模块：

- 导入命名导出：

```javascript
// app.js
import { add, subtract } from './math.js';

console.log(add(2, 3)); // 5
console.log(subtract(5, 2)); // 3
```

- 导入默认导出：

```javascript
// app.js
import Calculator from './calculator.js';

const calc = new Calculator();
console.log(calc.add(5, 3)); // 输出: 8
console.log(calc.subtract(10, 5)); // 输出: 5
```

- 混合导入：

如果一个模块同时使用了默认导出和命名导出，你可以这样导入：

```javascript
// app.js
import Calculator, { add } from './calculator.js';

console.log(add(5, 3)); // 使用命名导出
const calc = new Calculator(); // 使用默认导出
console.log(calc.subtract(10, 5)); // 输出: 5
```

## CommonJS 与 ES6 模块的主要区别

- **加载机制**：CommonJS 模块是运行时加载，ES6 模块是编译时输出接口。
- **语法**：CommonJS 使用 `require()` 导入模块、`module.exports` 导出模块；ES6 模块使用 `import` 和 `export` 语句。
- **模块解析**：CommonJS 模块的 `this` 指向当前模块，ES6 模块的 `this` 指向 `undefined`。
- **异步加载**：CommonJS 本质上不支持异步加载模块，而 ES6 模块可以与 `import()` 语法结合使用，实现动态导入。

## 如何2选择

- 如果你的项目是基于 Node.js，可能会倾向于使用 CommonJS，因为这是 Node.js 的原生模块系统。
- 如果你在开发面向浏览器的模块化前端应用，ES6 模块可能是更好的选择，因为它支持静态分析和树摇（tree-shaking），有助于减少包的大小。

两种模块化标准各有优势，选择哪个标准取决于你的项目需求和运行环境。现代 JavaScript 开发中，越来越多的环境和工具链都支持 ES6 模块，这也是现代 Web 开发的趋势。
