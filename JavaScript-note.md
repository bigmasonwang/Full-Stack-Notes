## 变量, 运算, 表达式

### 变量声明

* var(ES5) 作用于函数 `for (var i=0; i<5 ; i++)`
* let(ES6) 作用于块(statements 或花括号中) 可被更改
* conest(ES6) 作用于块 不能被更改

### 运算符

* Binary Operators: 
  * *Arithmetic Operators* (+, -, *, /)
  * *Assignment Operators* (=, +=, -=, *=)
  * *Logical Operators* (&&, ||, ! ​)
  * *Comma Operator (,)*: The Comma operator evaluates each operand from left to right and returns the value of right most operand.
  * *Comparison Operators* (<, >, ==, !=)
  * *Bitwise Operators* (&, |, ^) ;  AND, OR, XOR
  * *String Operators* (++)
  * *Conditional Operators* (?:)
* Unary Operators
  * `typeof`: Returns the type of the given operand
  * `delete`: Deletes an object, object’s attribute or an instance in an array
  * `void`: Specifies that an expression does not return anything
  * *Increment Operators* : ++, --

### 关键字

- `this`: points to the current object
- `super`: calls methods on an object’s parent, for example, call parent’s constructor
- `function`: used to define a function
- `function*`: used to define a generator function
- `async function`: used to define an async function

### 解构赋值

看例子

```JavaScript
const student = {
  ID: '21',
  name: 'Jhon',
  GPA: '3.0',
};

// one way
const id = student.ID;
const name = student.name;
const GPA = student.GPA;

// destructuring
const {ID, name, GPA} = student;

// even
const {name:n} = student;
```

### 展开语法

```javascript
const person = { name: "Jhon"};
const student = { ID: "21", GPA: "3.0"};

const new_object = { ...person, ...student, semester: '3'};
console.log(new_object);
```

## 函数

### 声明

- *Function Declaration* 
  - `function function_name(Arg1, Arg2..){}`
- *Function Expression* 常用于callback function
  - *Named*: `var var_name = function function_name(Arg1,Arg2..){};`
  - *Anonymous*:`var var_name = function(Arg1, Arg2..){};`
- *Generator Function*
  - `function* name(Arg1, Arg2..) {}`
- *Generator Function Expression*
  - *Named*: `function* function_name(Arg1,Arg2..){}`
  - *Anonymous*:`function* (Arg1,Arg2..){}`
- *Arrow Function* 简练
  - `var var_name = (Arg1, Arg2..) => {};`
- *Function Constructor*
  - `var var_name = new Function(Arg1, Arg2..,'FunctionBodyString');`

匿名函数(anonymous function) 在运行时被声明, 即定义与调用会同时进行

### Arrow function

考虑以下例子

```javascript
const students = [
  { ID: 1, present: true},
  { ID: 2, present: true},
  { ID: 3, present: false}, 
];

// ES5 function
const presentStudents = students.filter(function(student){return student.present;});

// ES6 arrow function
const presentStudents = students.filter(student => student.present);

console.log(presentStudents);
```

上述例子中, 省略了`function`关键字; 在函数内部只有一个statement, 故省略了花括号; 只有一个parameter, 故省略了圆括号.

### Higher-Order function

函数可以赋值给变量, 也可作为参数传递(callback). 高阶函数是对其他函数进行操作的函数，操作可以是将它们作为参数，或者是返回它们。 简单来说，高阶函数是一个接收函数作为参数或将函数作为输出返回的函数。

例如，Array.prototype.map，Array.prototype.filter 和 Array.prototype.reduce 是语言中内置的一些高阶函数。

例子

```javascript
notSquared = [2,6,3,1];
squared = notSquared.map(n => n*n); // [4,36,9,1]
```

## Class

JavaScript的类是构造函数的语法糖, 所以可以说类是对象

### Class Creation

```javascript
class Developer {
  constructor(firstname, lastname) {
    this.firstname = firstname;
    this.lastname = lastname;
  }

  getName() {
    return `${this.firstname} ${this.lastname}`;
  }
}

var me = new Developer('Robin', 'Wieruch');

console.log(me.getName());
```

### Object Creation

```javascript
let computer = { brand : 'HP', RAM : '8 GB', clockspeed : "2 GHz"};

// object definitions can have spaces and newlines!
let computer2 = { 
  brand : 'HP',
  RAM : '8 GB',
  clockspeed : "2 GHz"
};

// Objects can also have 'functions' called methods
let computer3 = {
  brand : 'HP',
  RAM : '8 GB',
  clockspeed : "2 GHz",
  
  printRam() {
    console.log(this.RAM)
  }
}
```

### this关键字与绑定

在JavaScript中, `this` 的值与它所处的环境有关, 例如在一个函数中使用它, 它的值将取决于该函数是如何被调用的. 

#### Implicit Binding 隐式绑定

**隐式绑定**，如果函数调用时，前面存在调用它的对象，那么this就会隐式绑定到这个对象上，看个例子：

```JavaScript
class Developer {
  constructor(firstname, lastname) {
    this.firstname = firstname;
    this.lastname = lastname;
  }

  getName() {
    return `${this.firstname} ${this.lastname}`;
  }
}

var me = new Developer('Robin', 'Wieruch');
console.log(me.getName()); // 'this' is me
var hobbit = new Developer('Frodo', 'Baggins');
console.log(hobbit.getName()); // 'this' is 'hobbit'
```

#### Explicit Binding 显式绑定

**显式绑定**是指我们通过call、apply以及bind方法改变this的行为，相比隐式绑定，我们能清楚的感知 this 指向变化过程。来看个例子：

```JavaScript
class Developer {
  constructor(firstname, lastname) {
    this.firstname = firstname;
    this.lastname = lastname;
  }
}

var printName = function() {
  console.log(`My name is ${this.firstname} ${this.lastname}`);
};

var me = new Developer('Robin', 'Wieruch');

// '.call()' can be used to explicitly bind a function to an object
printName.call(me);

// printName() is not bound to an object so 'this' is undefined
printName();

var printInfo = function(lang1, lang2, lang3) {
  console.log(`My name is ${this.firstname} ${this.lastname} and I know ${lang1}, ${lang2}, and ${lang3}`);
}

// Create an array of languages
languages = ['Javascript','C++', 'Python'];

// Pass each argument individually by indexing the array
printInfo.call(me, languages[0], languages[1], languages[2]);

// Pass all the arguments in one array to .apply()
printInfo.apply(me, languages);
```

上述例子中使用`call()`函数将`printName()`函数显示绑定到`me`对象. 如果在没有绑定任何对象的情况下调用`printName()`则会打印`undefined` 因为`this`是`undefined`. 如果希望将参数作为数组传递, 则使用`apply()`函数.

`bind()`设置`this`的内容并返回一个绑定了this的新函数,例子:

```JavaScript
class Developer {
  constructor(firstname, lastname) {
    this.firstname = firstname;
    this.lastname = lastname;
  }
}

var printName = function() {
  console.log(`My name is ${this.firstname} ${this.lastname}`);
};

var me = new Developer('Robin', 'Wieruch');

// Here we bind the me object to the printName() function and get a new function called newPrintName()
const newPrintName = printName.bind(me);

// bound newPrintName() prints appropriately
newPrintName();

// unbound printName() prints undefined
printName();
```

### 继承

使用`extends`关键字:

```JavaScript
class Developer {
  constructor(firstname, lastname) {
    this.firstname = firstname;
    this.lastname = lastname;
  }

  getName() {
    return this.firstname + ' ' + this.lastname;
  }
}

class ReactDeveloper extends Developer {
  getJob() {
    return 'React Developer';
  }
}

var me = new ReactDeveloper('Robin', 'Wieruch');

console.log(me.getName());
console.log(me.getJob());
```

不用继承的一个例子:

假设你是一个游戏制作人, 游戏中有两个角色: 一个魔法师会释放咒语, 一个射手会发射激光. 很自然你会创建一个父类:`Character`, 然后就是两个子类`Caster`和`Shooter`, 分别会`cast()`和`shoot()`. 但是现在如果又有个新角色, 又会释放咒语又会发射激光怎么办, 现在有两个办法:

1. 让`shoot()`和`cast()`函数称为父类`Character`的一部分, 并让`ShooterFighter`类继承它. 这样会带来问题: 射手和法师将继承他们不需要的`cast()`和`shoot()`.
2. 复制`cast()`和`shoot()`函数, 将其作为本地方法添加到`ShooterFighter`类中. 但复制代码是一种不好的做法, 违背了使用类的目的.

为了解决上述问题, 我们可以用组合(composition). 与继承的 **IS-A** 原则相对, 组合采用 **HAS_A** 原则: `ShooterFighter` 类**HAS-A** `shoot()` 函数 和 `cast()` 函数.

组合的一些优势:

* 不必事先定义类别分类, 这使代码可适应变化.
* 仅需对源代码进行很少的修改, 故带来很少的错误.
* 代码复用



## 模块化

类似Java中每个文件只有一个class, 在JavaScript中也是如此. 比如两个模块`Person.js` and `Student.js`, 注意这些文件应该放在`App`目录下.

定义在模块中类是private的, 我们可以使用 import/export使之public, 例如

```JavaScript
import React, { Component } from 'react'; 
import logo from './logo.svg'; 
import './App.css';
```

语法:

```javascript
// To make a class default export inside a module
export default class_name {....}

// To import a default export class from a module
import class_name from module_name;
```

























