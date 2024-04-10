## ES6（JavaScript6）

一种标准、js6

## let  命令

区别于 var，let 有局部和全局的作用域的区别

var 只要重名就是全局变量，变量提升

## const 命令

- 声明同时必须赋值
- 常量无法改变
- **指向内存的地址是不可变的,地址中的内容是可以更改的**

```javascript
// const
const LOVE_YOU = false; // 声明同时必须得赋值
LOVE_YOU = true;// 报错，无法盖板

_/* 引用类型 */_
let user = {
  name: "王华华",
  age: 10
};
const LOVE_YOU = user;
_// {const 常量名} 指向内存的地址是不可变的,地址中的内容是可以更改的_
_//敲黑板,js精讲中的有提到,基本数据类型(undefined null number string boolean)_
_//和引用类型(array object)_
_//红宝书 69页面和70也有比较明确的说明这个问题_
console.log(LOVE_YOU.age); _//10 _
user.age = 12;
console.log(LOVE_YOU.age); _//12 改变了_
_/* 基本数据类型 */_
let num = 66 
const NUMS = num 

console.log(NUMS); _//66_
num = 88
console.log(NUMS); _//66 还是没改变_
console.log(num); _//88 已经改变了 _
```

## 变量的解构赋值（数组）

```javascript
let a, b, c;
a = b = c = 1;
let [a, ,c] = [1,2,3];
_// ====================================================_
_//解构赋值_
let oldArray = [4,5,6]


_let [d,e,f] = oldArray_
_console.log(d,e,f); //4 5 6_

_let [d,e,] = oldArray_
_console.log(d,e,f); //4 5 {f is not undefined}_
_console.log(d,e); //4 5 _

_let [d,[e,f]] = [4,[5,6]]_
_console.log(d,e,f); //4 5 6_

_let [d,e,f] = [4,,6]_
_console.log(d,e,f); //4 undefined 6_

_let [d,...e] = oldArray //三点运算符,这里面有很多拓展_
_console.log(d,e); //4 [ 5, 6 ]_

_let [d,e=66,f="default"] = [4,5] // 解构前后都可以赋值,且会被后定义的数据覆盖_
_console.log(d,e,f); //4 5 default_
```

## 变量的解构赋值（对象）

```javascript
var obj = {
    a: 1,
    b: 2
}
_// 对象的解构赋值,重要的是键名能对上,没对上键名就_
var {
    a: A, _//定义一个A 使其等于解构对象中的a  此时,能够打印定义的A,a则打印不出来,undefined_
    c: c, _//同理  _
    b _//省略:b_
} = obj

console.log('A :>> ', A); // 1
console.log('a :>> ', a); // undefined 实际是未定义
console.log('c :>> ', c); // undefined
console.log('b :>> ', b); // 2

_// 基本对象的解构赋值===============================_
_/* 大括号在机构赋值的时候不能出现在一行的最前面,否则,{}则会被识别
   为一个语法块,而不是我们想要的解构语法,这个时候需要用一个()包
   起来即可
   {a,b,c} = obj ❌
   ({a,b,c} = obj) ✔
__*/_
_// 注意事项===============================_

var objs = {
    arr: [
        'yo.',
        {
            a: 1
        }
    ]
}

let {
    arr: [
        green,
        {
            a
        }
    ]
} = objs
_// console.log('green :>> ', green); // yo._
_// console.log('a :>> ', a); // 1_
_// 复杂数据对象的解构赋值 ===============================_

let {
    d = 1,
    e = 2
} = {
    d: 10
}
_// console.log('d :>> ', d); // 10  _
_// console.log('e :>> ', e); // 2_
_//默认数据对象初始值的解构赋值 ===============================_

let res = { _//接口返回的内容_
    status: 200,
    code: 200,
    message: "正常",
    data: [{
        name: "老李",
        sex: "male",
        like: "female"
    }]
}
let {
    status,
    code,
    message,
    data: userArry
} = res _//直接解构赋值_
_// console.log('status :>> ', status); // 200_
_// console.log('code :>> ', code); // 200_
_// console.log('message :>> ', message); // 正常_
_// console.log('userArry :>> ', userArry); // Arry_
_//赋值解构的用途之--接口 ===============================_

let {floor,pow} = Math;_//将方法提取出来_
_//floor 是化整数的方法 pow 是乘方的方法传参数(p1,p2)p1是底数,p2是指数_
let numberfloor = 1.9
let numberpow = 3
_// console.log('floor(numberfloor) :>> ', floor(numberfloor)); // 1_
_// console.log('pow(numberpow,3) :>> ', pow(numberpow,3)); // 27_
_//解构赋值的用途之-- 方法/函数式编程 ===============================_
_//请大声告诉我,谁是js中的一等公民? ?_
_//自己敲代码,本代码仅供参考 囧 ~_
```

## 变量的解构赋值（其他）

```javascript
let {length} = 'yo.'
console.log(length) // 打印长度

let {a, b, c} = 'yo.'
console.log(a,b,c)


_//还可以使用spread_
let arr = [1, 2];

function test(a, b) {
    console.log(a);
    console.log(b);
}

test(...arr);
```

## 新增字符串的方法

```javascript
console.log('yo'.includes('y'));// true

console.log('yo'.startsWith('o')// false 
console.log('yo'.endsWith('o')// true
console.log('yo'.repeat(3)// 'yoyoyo'
```

## 模版字符串

```javascript
let title  "hello world"
let plt = `
<div>
    <span>${title}</span>
</div>
`
```

## Symbol 类型

```javascript
let a = Symbol('this is a symbol');

let b = Symbol('this is a symbol');

console.log(a === b); // false
```

## Prxoy 类型

```javascript
let user = {
    full_name: function(){
        return this.fname + " " + this.lname;
    }
}
user.fname = 'Bob'
user.lname = 'Wood'
//================================

var user = new Proxy({}, {
    get: function(obj, prop){
        return this.fname + " " + this.lname;
    }
})
user.fname = 'Bob'
user.lname = 'Wood'
console.log(user.full_name)
```
