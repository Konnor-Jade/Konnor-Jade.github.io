# Mocha+chai 测试框架 JavaScript

## 什么是 mocha, chai

mocha 是 JavaScript 的一种单元测试框架，既可以在浏览器环境下运行，也可以在 Node.js 环境下运行。使异步测试变得简单而有趣。

---

Chai 是一个用于 node 和浏览器的 BDD / TDD 断言库，可以与任何 javascript 测试框架轻松地配对。

## 安装

建议局部安装

- 全局安装

```bash
npm install --global mocha
yarn global add mocha
```

- 局部安装(开发依赖)

```bash
npm install --save-dev mocha
yarn add --dev mocha
```

- 安装 chai

```bash
npm install chai --save-dev
yarn add --dev chai
```

## 简单示例

Mocha 可以搭配<u>任意断言库(assertion library)</u> 。因为 Mocha + Chai 这种搭配方式应用范围最广，我们选择了 <u>chai</u> ，并使用 <u>expect</u> 这种 `BDD` 方式，原因是它更接近于自然语言，相对比较容易理解些。

- 源码 `add.js`

```bash
module.exports = function (x, y) {
    return x + y;
}
```

- 测试脚本 `add.test.js` :

```bash
const add = require('./add.js');
const { expect } = require('chai');
describe('加法函数的测试', function () {
    it('1 加 1 应该等于 2', function () {
        expect(add(1, 1)).to.be.equal(2);
    });
});
```

## 关于 Mocha 的几个重要概念

Mocha 中有几个重要概念需要了解：

- **测试脚本**：测试用例的脚本，通常命名为 `*.test.js` 或 `*.spec.js`，例如上述示例中的 `add.test.js` 。一般情况下测试脚本是按功能模块划分，一个测试脚本里面包含一个或多个 `describe` 块
- `describe` 块：称为"测试套件"（test suite），表示一组相关的测试。一个 `describe` 块里面包含一个或多个 `it` 块，甚至 `describe` 块里面还可能包含 `describe` 块
- `it` 块：称为"测试用例"（test case），表示一个单独的测试，是测试的最小单位。一个 `it` 块里面包含一个或多个 `断言`
- `断言` ：用于预判、校验用例逻辑的执行结果，在上述示例中，我们使用了 Chai 来写断言

## Mocha 的常见用法

Mocha 是一个灵活的 JavaScript 测试框架，支持异步测试，可以用于 Node.js 和浏览器中的测试。它让你可以组织测试脚本代码，通过 `describe` 和 `it` 函数定义测试套件（test suite）和测试用例（test case）。Chai 作为一个断言库，可以和 Mocha 一起使用，提供 `expect` 或 `should` 风格的断言方法，让测试的编写更加直观和易于理解。

### 使用 `describe` 和 `it`

- **describe**：定义了一个“套件”，用于表示一组相关的测试。
- **it**：定义了一个“测试用例”，用于表示单个测试。

### 示例

假设我们正在测试一个简单的数组功能，我们可以这样使用 Mocha 和 Chai 的 `expect` 风格：

```javascript
// 引入断言库
var expect = require('chai').expect;

// 定义测试套件
describe('Array', function() {
  // 定义一个测试用例
  describe('#indexOf()', function() {
    it('应当在找到元素时返回其索引', function() {
      // 使用 expect 风格的断言
      expect([1, 2, 3].indexOf(2)).to.equal(1);
    });

    it('应当在没有找到元素时返回-1', function() {
      // 另一个 expect 断言
      expect([1, 2, 3].indexOf(4)).to.equal(-1);
    });
  });
});
```

如果你倾向于使用 `should` 风格，示例如下：

```javascript
// 首先调用 should 方法以便在任何对象上使用 should 属性
var should = require('chai').should();
// 定义测试套件
describe('Array', function() {
// 定义一个测试用例
    describe('#indexOf()', function() {
        it('应当在找到元素时返回其索引', function() {
        // 使用 should 风格的断言
        [1, 2, 3].indexOf(2).should.equal(1);
        });
        
        it('应当在没有找到元素时返回-1', function() {
          // 另一个 should 断言
          [1, 2, 3].indexOf(4).should.equal(-1);
        });
    });
});
```

这两个示例展示了如何使用 Mocha 和 Chai 进行基本的单元测试。`describe` 用于组织测试，而 `it` 用于具体的测试用例。通过这种方式，你可以创建结构化和易读的测试代码。

### 异步测试示例

Mocha 也支持异步测试，这对于测试异步函数特别有用。下面是使用 `done` 参数进行异步测试的示例：

```javascript
describe('异步测试', function() {
  it('异步请求应当响应 Hello World', function(done) {
    // 模拟异步请求
    setTimeout(function() {
      var response = 'Hello World';
      // 使用 expect 断言
      expect(response).to.equal('Hello World');
      done(); // 表明测试完成
    }, 1000);
  });
});
```

## chai 常见用法

Chai 是一个流行的 JavaScript 测试断言库，支持行为驱动开发（BDD）和测试驱动开发（TDD）的风格。Chai 提供了丰富的断言方法，使得测试代码既易于书写又易于理解。

### Chai 的主要断言风格

- **Expect/Should**：BDD 风格，支持链式写法，使测试读起来像自然语言。
- **Assert**：TDD 风格，提供传统的断言方法。

### Expect/Should 用法示例

在使用 Expect 或 Should 风格时，首先需要引入 Chai 并选择一个风格：

```javascript
// 引入 chai 并使用 expect 风格
var expect = require('chai').expect;
// 或者使用 should 风格
var should = require('chai').should();
```

### **Expect 示例**：

```javascript
describe('Array', function() {
  describe('#indexOf()', function() {
    it('应当在没有找到元素时返回-1', function() {
      expect([1, 2, 3].indexOf(4)).to.equal(-1);
    });
  });
});
```

### **Should 示例**：

```javascript
describe('Array', function() {
  describe('#indexOf()', function() {
    it('应当在没有找到元素时返回-1', function() {
      [1, 2, 3].indexOf(4).should.equal(-1);
    });
  });
});
```

### Assert 用法示例

Assert 风格提供了一种更接近传统测试表达方式的断言方法：

```javascript
// 引入 chai 并使用 assert 风格
var assert = require('chai').assert;

describe('Array', function() {
  describe('#indexOf()', function() {
    it('应当在没有找到元素时返回-1', function() {
      assert.equal([1, 2, 3].indexOf(4), -1);
    });
  });
});
```

### 更复杂的示例

Chai 提供了许多方法来处理更复杂的测试场景，如对象深度比较、字符串包含、布尔值测试等。

**深度比较**：

```javascript
describe('Object', function() {
  it('应当进行深度比较', function() {
    var obj = { a: { b: 'c' } };
    expect(obj).to.eql({ a: { b: 'c' } }); // eql 用于深度比较
  });
});
```

**字符串包含**：

```javascript
describe('String', function() {
  it('应当找到子字符串', function() {
    expect('Hello world').to.contain('world');
  });
});
```

**布尔值测试**：

```javascript
describe('Boolean', function() {
  it('应当为 true', function() {
    expect(true).to.be.true;
    // 使用 should 风格
    true.should.be.true;
  });
});
```

Chai 的断言方法非常丰富，上面只是一小部分示例。在实际开发中，根据测试的需要选择合适的断言风格和方法，可以有效提高测试的准确性和表达性。
