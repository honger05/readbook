#### A.1 缩进

每一行的层级由2个空格组成，禁止使用制表符（Tab）缩进。

````javascript
// 好的写法
if (true) {
  doSomething();
}
````

#### A.2 行的长度

每行长度不应该超过80个字符，超过80个，应当在一个运算符（，+）后换行。下一行应当增加两级缩进。

````javascript
// 好的写法
doSomething(argument1, argument2, argument3, argument4,
    argument5);

// 不好的写法：第二行只有2个空格的缩进
doSomething(argument1, argument2, argument3, argument4,
  argument5);

// 不好的写法：在运算符之前换行
doSomething(argument1, argument2, argument3, argument4
    , argument5);
````

<!--break-->

#### A.3 原始值

字符串应当始终使用单引号且保持一行（json 中使用双引号），禁止使用斜线另起一行。

````js
// 好的写法
var name = 'honger';

// 好的写法
var name = {
  value: "honger"
}

// 不好的写法： 斜线换行
var longString = 'Here's the story, of a man \
named Brady';
````

数字应该使用十进制整数，科学计数法表示整数，十六进制整数，或者十进制浮点小数，小数点前后应当至少保留一位数字。禁止使用八进制直接量。

````javascript
// 好的写法
var count = 10;

var price = 10.0;
var price = 10.00;

var num = 0xA2;

var num = 1e23;

// 不好的写法：十进制数字以小数点结尾
var price = 10.

// 不好的写法：十进制数字以小数点开头
var price = .1;

// 不好的写法：八进制写法已废弃
var num = 010;
````

特殊值 `null` 只能用以下四种情形

````js
// 用来初始化一个变量，这个变量可能被赋值为一个对象。
var obj = null;

// 用来和一个已经初始化的变量比较，这个变量可以是也可以不是一个对象
var obj = new Object();
var num = 0;
if (obj !== null && num !== null) {
  doSomething();
}

// 当函数的参数期望是对象时，被用作参数传人
doSomething('do', null, null);

// 当函数的返回值期望是对象时，被用作返回值传出
doSomething() {
  return null;
}

// 不好的写法：和一个未被初始化的变量比较
var person;
if (person != null) { // 期望是 true，但结果是 false
  person = getPerson();
}

// 不好的写法：通过测试判断某个参数是否被传递
function doSomething(arg1, arg2, arg3, arg4) {
  if (arg4 != null) {// 因为 undefined == null 所以 期望是 true 但结果是 false
    doSomethingElse();
  }
}
````

避免使用特殊值 `undefined`。判断一个变量是否定义应当使用 typeof 操作符

````javascript
// 好的写法
if (typeof variable == 'undefined') {
  doSomething();
}

// 不好的写法：使用了 undefined 直接量, 1. undefined 不是关键字，可以被赋值。2.变量若未声明，则报错。
if (variable == undefined) {
  doSomething();
}
````

#### A.4 运算符间距

二元运算符前后必须使用一个空格来保持表达式的整洁。包括 赋值运算符 和 逻辑运算符

````javascript
// 好的写法
var found = (values[i] === item);

if (found && (count > 10)) {
  doSomething();
}

for (i = 0; i < count; i++) {
  process(i);
}

// 不好的写法：丢失空格
var found = (values[i]===item);

if (found&&(count>10)) {
  doSomething();
}

for(i=0; i< count; i++){
  process(i);
}
````

#### A.5 括号间距

当使用括号时，紧接左括号之后和紧接右括号之前不应该有空格。

````javascript
// 好的写法
var found = (values[i] === item);

// 不好的写法
var found = ( values[i] === item );
````

#### A.6 对象直接量

````javascript
// 好的写法：适当保留空行，提升可读性，冒号紧接着key值，然后是一个空格。
var object = {

  key1: value1,

  key2: value2,

  func: function() {

  }
}
````

当对象直接量作为函数参数时

````javascript
// 好的写法
doSomething({
  key1: value1,
  key2: value2
});

// 不好的写法
doSomething({ key1: value1, key2: value2 });
````

#### A.7 注释

以下情况应当使用注释

* 代码晦涩难懂
* 可能被误认为错误的代码
* 必要但并不明显的针对特定浏览器的代码
* 对于对象、方法或者属性，生成文档是有必要的（使用恰当的文档注释）

##### A.7.1 单行注释

单行注释应当用来说明一行代码或者一组相关的代码，单行注释可能有以下三种使用方式：

* 独占一行的注释，用来解释下一行代码。`这行注释之前必须留个空行，反斜杠之后要跟一个空格`
* 禁止在代码行的尾部添加注释
* 多行，用来注释掉一个代码块

````javascript
// 好的写法
if (condition) {

  // 解释下一行,上留一个空行，前留一个空格
  doSomething();
}

// if (condition) {
//  doSomething();
// }
````

##### A.7.2 多行注释

同单行注释差不多

````javascript
/*
 *
 */
````

##### A.7.3 注释声明

注释的时候也可以用来给一段代码声明额外的信息。

* `TODO`: 说明代码还未完成，应当包含下一步要做的事情
* `HACK`: 表明代码走了一个捷径，应当包含使用 hack 的原因。这也可能表明还有更好的解决方法。
* `XXX`: 说明代码是有问题的并应当尽快修复
* `FIXME`: 说明代码是有问题的并尽快修复。重要性略次于 XXX
* `REVIEW`: 说明代码任何可能的改动都需要评审

这些声明可能在一行或多行注释中使用。

````javascript
// TODO: 我希望一种更快的方式
doSomething();

/*
 * HACK: 不得不针对 IE 做的特殊处理，我计划后续有时间重写这部分
 * 这些代码可能需要在 v1.2 版本之前替换掉。
 */
if (document.all) {
  doSomething();
}

// REVIEW: 有更好的方法吗？
if (document.all) {
  doSomething();
}

// XXX: 这段代码是有问题的，应当尽快修复
if (document.all) {
  doSomething();
}
````

##### A.7.4 变量声明

所有的变量在使用前应当事先定义。

````javascript
// 小而短的一组变量可以声明在一行
var x, j, width, height;

// 长变量应当使用多 var 模式，压缩器会把它们改成但 var 的。这也可能表明还有更好的解决方法。
var longlonglongVariable;
var longloginlongAttr;
````

##### A.7.5 函数声明

函数应当在使用前定义

````javascript
// 好的写法
function doSomething(arg1, arg2) {

}

// 不好的写法：不恰当的空格
function doSomething (arg1, arg2) {

}

// 不好的写法：函数表达式
var doSomething = function(arg1, arg2) {

}
````

函数内部定义的函数，应当在 var 语句之后立即定义

````javascript
function outer() {
  var a = 10,
      b = 11,
      c;

  function inner() {

  }

  // 调用 inner 的代码。。。
}
````

立即调用函数应当用圆括号包裹

````javascript
// 好的写法
var value = (function() {
  return {
    message: "Hi"
  }
}());

// 不好的写法: 没包裹
var value = function() {
  return {
    message: "Hi"
  }
}();

// 不好的写法： 圆括号位置不恰当
var value = (function() {
  return {
    message: "Hi"
  }
})();

````

#### A.7.6 命名

`变量命名`：变量名第一个单词应当是一个名词，以避免同函数混淆，可以是驼峰，也可以是下划线，但要保持统一。

````javascript
// 好的写法（优先）
var accountNumber = 99;

// 也是可以的 （个人癖好）
var account_number = 90;

// 不好的写法：动词开头
var getAccountNumber = 90;

// 不好的写法：首字母大写了
var AccountNumber = 90;
````

`函数命名`：必须是驼峰，函数第一个单词应当是动词，禁止使用下划线。

````javascript
// 好的写法
function doSomething() {

}

// 不好的写法
function DoSomething() {

}

// 不好的写法：第一个单词不是动词
function car() {

}

// 不好的写法：禁止使用下划线
function do_something() {

}
````

`构造函数`：必须驼峰，且首字母大写

````javascript
// 好的写法
function MyObject() {}
````

`常量`：必须是所有字母大写，不同单词之间用下划线隔开

#### A.7.7 赋值

当给变量赋值时，如果右侧含有比较语句的表达式，需要用圆括号包裹

````javascript
// 好的写法
var flag = (i < count);

// 不好的写法
var flag = i < count;
````

#### A.7.8 等号运算符

使用 === 和 !== 避免弱类型转换错误

````javascript
// 好的写法
var same = (a === b);

// 不好的写法
var same = (a == b);
````

#### A.7.9 三元操作符

仅仅用在条件赋值语句中，而不要作为 if 的替代品

````javascript
// 好的写法
var value = condition ? v1 : v2;

// 不好的写法： 应当使用 if
condition ? doSomething() : doSomethingElse();
````