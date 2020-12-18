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



































