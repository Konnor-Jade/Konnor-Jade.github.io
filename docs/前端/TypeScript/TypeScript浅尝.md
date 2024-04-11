# TypeScript是什么

TS是 JS 的超集

- [TypeScript 中文网 (nodejs.cn)](https://ts.nodejs.cn/)

- [[TypeScript 入门教程](https://ts.xcatliu.com/)](https://ts.xcatliu.com/introduction/hello-typescript.html)

- [TypeScript快速入门](https://zhuanlan.zhihu.com/p/598811083)

1. **`TypeScript` 简称：TS，是 JavaScript 的超集**。简单来说就是：JS 有的 TS 都有。JS写的代码在TS的环境下都能跑。
2. 在 JS 基础之上，为 JS 添加了**类型支持**。TypeScript = `Type` + JavaScript
3. TypeScript 是*微软*开发的开源编程语言，可以在任何运行 JavaScript 的地方运行
4. 区别

| TypeScript                                     | JavaScript                                 |
| ---------------------------------------------- | ------------------------------------------ |
| JavaScript 的超集用于解决大型项目的代码复杂性  | 一种脚本语言，用于创建动态网页             |
| 可以在编译期间发现并纠正错误                   | 作为一种解释型语言，只能在运行时发现错误   |
| 强类型，支持静态和动态类型                     | 弱类型，没有静态类型选项                   |
| 最终被编译成 JavaScript 代码，使浏览器可以理解 | 可以直接在浏览器中使用                     |
| 支持模块、泛型和接口                           | 不支持模块，泛型或接口                     |
| 社区的支持仍在增长，而且还不是很大             | 大量的社区支持以及大量文档和解决问题的支持 |

# 安装使用

1. 项目安装

```bash
npm add typescript --dev
```

2. 验证 TypeScript

```bash
tsc -v 
# Version 4.0.2
```

3. 编译 TypeScript 文件

```bash
tsc helloworld.ts
# helloworld.ts => helloworld.js
```

4. 典型工作流

![TS编译.png](https://fastly.jsdelivr.net/gh/Konnor-Jade/image-host/img/202404110928341.awebp)

在上图中包含 3 个 ts 文件：a.ts、b.ts 和 c.ts。这些文件将被 TypeScript 编译器，根据配置的编译选项编译成 3 个 js 文件，即 a.js、b.js 和 c.js。

TypeScript 只会在编译阶段对类型进行静态检查，如果发现有错误，编译时就会报错。而在运行时，编译生成的 JS 与普通的 JavaScript 文件一样，并不会进行类型检查。

对于大多数使用 TypeScript 开发的 Web 项目，我们还会对编译生成的 js 文件进行打包处理，然后在进行部署。

##  ts-node 简化运行 TS 的步骤

每次修改代码后，都要重复执行两个命令，才能运行 TS 代码，太繁琐。

```bash
tsc  你的代码.ts

node 你的代码.js
```

1. 简化方式

使用 `ts-node` 包，直接在 Node.js 中执行 TS 代码。它提供了 `ts-node` 命令，可以简化执行命令。

2. 安装命令

`npm i -g ts-node`

使用方式：

`ts-node hello.ts` 

相当于：1 tsc 命令 2 node（注意：ts-node 不会生成 js 文件）

**解释**：ts-node 命令在内部偷偷的将 TS -> JS，然后，再运行 JS 代码

## **[webstorm 使用](https://blog.csdn.net/David_house/article/details/134077477)**

1. 全局安装

```bash
npm i -g  typescript
tsc -v
```

2. 初始化项目目录

```bash
tsc --init
```

3. 安装 ts-node, 在 webstorm 插件市场安装 ts-node 插件

```bash
npm i -g ts-node
```

# 常用语法

TS类型注解
------

TypeScript 是 JS 的超集，TS 提供了 JS 的所有功能，并且额外的增加了：**类型系统**

*   TS中定义变量(常量)可以指定类型了。
*   A类型的变量不能保存B类型的数据

**可以显示标记出代码中的意外行为，从而降低了发生错误的可能性**

### 类型注解

格式

```typescript
let 变量名: 类型 = 初始值

```

示例代码:

```typescript
let age: number = 18

```

说明：代码中的 `: number` 就是**类型注解**

作用：为变量添加类型约束**。

上述代码中，约定变量 age 的类型为 number 类型，就只能给变量赋值该类型的值，否则，就会报错

```typescript

let age: number = '18'

```

类型推论
----

在 TS 中，某些没有明确指定类型的情况下，**TS 的类型推论机制会自动提供类型**。好处：由于类型推论的存在，有些情况下的类型注解可以省略不写

### 发生类型推论的 2 种常见场景

0.  声明变量并初始化时
1.  决定函数返回值时

```typescript
let age = 18
function add(num1: number, num2: number) {
  return num1 + num2
}

```

TS的类型
-----

### 常用基础类型

将 TS 中的常用**基础类型**分为两类

0.  JS 已有类型

    0.  原始类型：`number/string/boolean/null/undefined/symbol`
    1.  对象类型：`object`（包括，数组、对象、函数等对象）
1.  TS 新增类型

    0.  联合类型
    1.  自定义类型(类型别名)
    2.  接口
    3.  元组
    4.  字面量类型
    5.  枚举
    6.  void
    7.  any 等

*   注意：

    0.  原始类型在 TS 和 JS 中写法一致
    1.  对象类型在 TS 中更加细化，每个具体的对象（比如，数组、对象、函数）都有自己的类型语法

原始类型
----

*   原始类型：`number/string/boolean/null/undefined/symbol`
*   特点：简单，这些类型，完全按照 JS 中类型的名称来书写

```typescript
let age: number = 18

let myName: string = '小花'

let isLoading: boolean = false

let un: undefined = undefined

let timer:null = null

```

联合类型
----

如何定义一个变量可以是null也可以是 number 类型?

联合类型的用法：

```typescript
let arr: (number | string)[] = [1, 'a', 3, 'b']

```

### 联合类型的格式

```typescript
let 变量: 类型1 | 类型2 | 类型3 .... = 初始值

```

解释：`|`（竖线）在 TS 中叫做**联合类型**，即：由两个或多个其他类型组成的类型，表示可以是这些类型中的任意一种

### 应用场景

1. 定时器id

```typescript
let timer:number|null = null
timer = 2

let arr: (number|string|boolean)[] = [1,2,3]

arr[0] = '1'
arr[2] = true

```

注意：这是 TS 中联合类型的语法，只有一根竖线，不要与 JS 中的或（|| 或）混淆了

数组类型
----

### 两种写法

格式

```typescript
let 变量: 类型[] = [值1，...]
let 变量: Array<类型> = [值1，...]

```

### 基本示例

```typescript
let numbers: number[] = [1, 3, 5] 

let strings: Array<string> = ['a', 'b', 'c'] 

```

### 拓展示例

如何定义一个数组，它的元素可能是字符串类型，也可能是数值类型。

分析，结合联合类型来使用

```typescript
let arr: (number | string) [] = ['1', 1]
```

这里有个有优先级的问题

类型别名
----

```bash
type 别名 = 类型
```

使用

```typescript
type s = string 

const str1:s = 'abc'
const str2:string = 'abc'
```

### 作用

1. 给类型起别名
2. 定义了新类型

### 场景

给复杂类型起别名

```typescript
// type NewType = string | number

// let a: NewType = 1
// let b: NewType = '1'

// let arr: NewType[] = [1, '1']
    
type MyArr = (number | string) []
const arr:MyArr = [1, '1']


```

别名可以是任意的合法字符串，一般**首字母大写**

函数-单个定义
-------

### 函数的类型

函数的类型实际上指的是：`函数参数`和`返回值`的类型

### 格式

```typescript
function 函数名(形参1： 类型=默认值， 形参2：类型=默认值): 返回值类型 { }


const 函数名（形参1： 类型=默认值， 形参2：类型=默认值):返回值类型 => { }

```

### 示例

```typescript
function add(num1: number, num2: number): number {
  return num1 + num2
}

const add = (num1: number=10, num2: number=20): number => {
  return num1 + num2
}

add（1,'1') 
```

函数-统一定义函数格式
-----------

定义多个具有相同参数类型和返回值类型的函数时，代码比较累赘

```typescript
const add = (a:number,b:number):number =>{
    return a + b
}
const sub = (a:number,b:number):number =>{
    return a - b
}

```

### 分析

把拥有相同形参和实参的函数当做一个整体，来定义

```typescript
const add1 : (n1:number,n2:number)=>number  =  (a,b)=>{return a+b }
```

提炼自定义类型

```typescript
type Fn = (n1:number,n2:number) =>number 
const add1 : Fn = (a,b)=>{return a+b }
```

函数返回值是void
----------

### void 类型

如果函数没有返回值，那么，函数返回值类型为：`void`

```typescript
function greet(name: string): void {
  console.log('Hello', name)
}
```

如果一个函数没有返回值，此时，在 TS 的类型中，应该使用 `void` 类型，有如下三种情况会满足

*   不写return
*   写return ，但是后面不接内容
*   写return undefined

```typescript
const add = () => {}

const add = (): void => {}

const add = (): undefined => {
  return undefined
}

```

### void和undefined的区别

0.  如果函数没有指定返回值，调用结束之后，值是undefined的

1.  当不能直接声明返回值是undefined

    ```typescript
    function add(a:number, b:number): undefined { 
      console.log(a,b)
    }
    ```

函数-可选参数
-------

### 场景

使用函数实现某个功能时，参数可以传也可以不传。

例如：数组的 slice 方法，可以 `slice()` 也可以 `slice(1)` 还可以 `slice(1, 3)`\] 这种情况下，在给函数参数指定类型时，就用到**可选参数**了

### 格式

可选参数：在可选参数名的后面添加 `?`（问号）

```typescript
function mySlice(start?: number, end?: number): void {
  console.log('起始索引：', start, '结束索引：', end)
}
```

注意：**可选参数只能出现在参数列表的最后**，也就是说可选参数后面不能再出现必选参数

### 可选和默认值的区别

相同点： 调用函数时，可以少传参数

区别：设置了默认值之后，就是可选的了，不写就会使用默认值； 可选的并一定有值。

注意：它们不能一起使用。优先使用默认值

![](https://fastly.jsdelivr.net/gh/Konnor-Jade/image-host/img/202404111019942.awebp)

对象类型-单独使用
---------

### 格式

```typescript
const 对象名: {
    属性名1：类型1，
    属性名2：类型2，
    方法名1(形参1: 类型1，形参2: 类型2)： 返回值类型,
    方法名2:(形参1: 类型1，形参2: 类型2)=>返回值类型
} = { 属性名1: 值1，属性名2：值2  }
```

可选属性用 ?

```typescript
const 对象名: {属性名1？：类型1，属性名2：类型2 } = { 属性名2：值2 }  
```

### 示例

```typescript
const goodItem:{name: string, price: number, func: ()=>string }  = {
    name: '手机', 
    price: 2000, 
    func:function(){ return '打电话' }
}
```

说明:

1. 使用 `{}` 来描述对象结构
2. 属性采用`属性名: 类型`的形式，如果是多行，可以省略,
3. 方法采用`方法名(): 返回值类型`的形式
4. 可选使用 ?

对象类型-类型别名
---------

把类型注解封装一下，定义类型

### 示例

```typescript
type Person = {
  name: string，
  age: number
  sayHi(): void
}

let person: Person = {
  name: '小花',
  age: 18
  sayHi() {}
}

function f1 (p: Persion) :void {
  
}
```

### 小结

创建类型别名后，直接使用该类型别名作为变量的类型注解即可

对象类型-接口
-------

### 场景

当一个对象类型被多次使用时，可以有两种方式来来**描述对象**的类型，达到复用的目的。

1. 类型别名，type
2. 接口, interface

### 格式

```typescript
interface 接口名  {
    属性1: 类型1, 属性2: 类型2,
}
```

### 示例

```typescript
interface IGoodItem  {
    name: string, price: number, func: ()=>string
}

const good1: IGoodItem = {
    name: '手表',
    price: 200,
    func: function() {
        return '看时间'
    }
}

const good2: IGoodItem = {
    name: '手机',
    price: 2000,
    func: function() {
        return '打电话'
    }
}

```

解释：

1. 使用 `interface` 关键字来声明接口
2. 接口名称(比如，此处的 IPerson)，可以是任意合法的变量名称，推荐以 `I` 开头
3. 声明接口后，直接使用接口名称作为变量的类型

### 接口和类型的区别

interface（接口）和 type（类型别名）的对比：

*   相同点：都可以给对象指定类型

*   不同点:

    *   接口，只能为对象指定类型。它可以继承。
    *   类型别名，不仅可以为对象指定类型，实际上可以为任意类型指定别名

推荐：**能使用 type 就是用 type**

```typescript
interface IPerson {
    name: string,
    age: number
}

const user1：IPerson = {
    name: 'a',
    age: 20
}

type Person  = {
    name: string,
    age: number
}

const user2：Person = {
    name: 'b',
    age: 20
}

```

接口继承
----

### 背景

比如，这两个接口都有 x、y 两个属性，重复写两次，可以，但很繁琐

```typescript
interface IPoint2D { x: number; y: number }
interface IPoint3D { x: number; y: number; z: number }

```

### 分析

如果两个接口之间有相同的属性或方法，可以将**公共的属性或方法抽离出来，通过继承来实现复用**

### 继承格式

```php
interface 接口2 extends 接口1 {
    属性1： 类型1， 
    ... 
}

```

### 接口继承的示例

```typescript
interface Point2D { x: number; y: number }

interface Point3D extends Point2D {
  z: number
}

```

解释：

0.  使用 `extends`(继承)关键字实现了接口 Point3D 继承 Point2D
1.  继承后，Point3D 就有了 Point2D 的所有属性和方法(此时，Point3D 同时有 x、y、z 三个属性)

元组
--

### 场景

固定结构的数据， 例如

*   使用经纬度坐标来标记位置信息
*   使用x,y来记录鼠标的位置

可以使用数组来记录坐标

```typescript
let position: number[] = [116.2317, 39.5427] 

```

### 问题

使用 number\[\] 的缺点：不严谨，因为该类型的数组中可以出现任意多个数字，而类似于经纬度只能有两个数字。

### 元组 Tuple

**元组是**另一种特殊的**数组**：

*   它确切地包含多少个元素
*   特定索引对应的类型

```typescript
let position: [number, number] = [39.5427, 116.2317]
```

解释：

0.  元组类型可以确切地标记出有多少个元素，以及每个元素的类型
1.  该示例中，元素有两个元素，每个元素的类型都是 number

### 示例

模拟定义useState。

useState的返回值是一个数组，第一个元素是number，第二个是修改number的函数。

```typescript
function useState(n: number): [number, (number)=>void] {
        const setN = (n1) => {
            n = n1
        }
        return [n, setN]
    }
const [num ,setNum] = useState(10)
```

字面量类型
-----

### 思考

```typescript
let str1 = 'hello 武汉'
const str2 = 'hello 武汉'
```

问： str1是什么类型？ str2是什么类型？

通过 TS 类型推论机制，可以得到答案：

0.  变量 str1 的类型为：string
1.  变量 str2 的类型为：'Hello TS'

### 解释

0.  str1 是一个变量(let)，它的值可以是任意字符串，所以类型为:string
1.  str2 是一个常量(const)，它的**值不能变化**只能是 'hello 武汉'，所以，它的类型为:'hello 武汉'

*   注意：此处的 'Hello TS'，就是一个**字面量类型**，也就是说某个特定的字符串也可以作为 TS 中的类型

### 字面量类型

任意的 JS 字面量（比如，对象、数字等）都可以作为类型使用

说明：

0.  上面的let a等价于const
1.  简写为 const a = 'abc'

字面量：`{ name: 'jack' }` `[]` `18` `20` `'abc'` `false` `function() {}`

### 字面量的作用

单个字面量没有什么用处，它一般**和联合类型一起使用** ， 用来表示一组明确的可选值列表

### 示例1

比如，在贪吃蛇游戏中，游戏的方向的可选值只能是上、下、左、右中的任意一个

```javascript
type Direction = 'up' | 'down' | 'left' | 'right'
function changeDirection(direction: Direction) {
  console.log(direction)
}

changeDirection('up')
```

解释：参数 direction 的值只能是 up/down/left/right 中的任意一个

优势：相比于 string 类型，使用字面量类型更加精确、严谨

### 示例2

redux 中的actiontype

```typescript
type ActionType = 'ADD_TODO' | 'DEL_TODO'
function reducer(type:ActionType) {
  if(type === 'ADD_TODO')
}
```

### 示例3

性别取值只能有两个

```typescript
let gender: 'girl' | 'boy' = 'boy'
    gender = 'abc' 
```

### 小结

字面量类型约定：只能取**某些个**特定的值。一般和联合类型一起使用。
