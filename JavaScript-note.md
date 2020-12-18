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
- *Arrow Function* 短
  - `var var_name = (Arg1, Arg2..) => {};`
- *Function Constructor*
  - `var var_name = new Function(Arg1, Arg2..,'FunctionBodyString');`

匿名函数(anonymous function) 在运行时被声明, 即定义与调用会同时进行













