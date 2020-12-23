## Hello World

```javascript
// index.js
import React from 'react';
import ReactDOM from 'react-dom';
import App from './app.js';

ReactDOM.render(
  <App />, 
  document.getElementById('root')
);

// app.js
import React from 'react';

export default class App extends React.Component {
  render() {
    return (
      <span>Hello World</span>
    );
  }
}
```



![svg viewer](https://www.educative.io/api/collection/10370001/5687272380825600/page/5750085036015616/image/5191852874530816)



过去网站和web应用程序是从服务器呈现的, 用户在浏览器中访问URL，并从Web服务器请求一个HTML文件及其所有关联的HTML，CSS和JavaScript文件。 经过一段时间的网络延迟后，用户会在浏览器（客户端）中看到呈现的HTML，并开始与其进行交互。 每进行一次其他页面转换（即：访问另一个URL）将再次启动此过程。 这种方式，本质上所有关键的事情都由服务器完成，而客户端仅通过逐页呈现而起着最小的作用。

相反，现代JavaScript将焦点从服务器转移到了客户端。 用户访问URL，并请求一个最小的HTML文件和一个关联的JavaScript文件。 经过一段时间的网络延迟后，用户会在浏览器中看到由JavaScript渲染的HTML，并开始与其进行交互。 每进行一次额外的页面转换，都不会从网络服务器请求更多文件，而是会使用最初请求的JavaScript来呈现新页面。 同样，用户的每个其他交互也要在客户端上处理。 在此现代版本中，服务器主要通过一个最小的HTML文件跨线提供JavaScript。 然后，HTML文件在客户端执行所有链接的JavaScript，以使用HTML和JavaScript呈现整个应用程序进行交互。

## React 目录结构

使用 [`create-react-app`](https://github.com/facebook/create-react-app)来引导程序 

```shell
npm install --global create-react-app
$ create-react-app first_react_app
cd first_react_app
npm start
```

可以得到如下[文件结构](https://create-react-app.dev/docs/folder-structure/):

```
my-app/
  README.md
  node_modules/
  package.json
  public/
    index.html
    favicon.ico
  src/
    App.css
    App.js
    App.test.js
    index.css
    index.js
    logo.svg
```

## JSX

JSX将HTML和JavaScript混合, 看如下例子:

```javascript
import React from 'react';

const title = 'React';

function App() {
    return (
      <div>
          <h1> Hello {title} </h1>
					<label htmlFor="search">Search: </label>
          <input id="search" type="text" />
      </div>
    );
}

export default App;
```

注意`htmlFor`对应的是HTML中的`for`属性, JSX替换了一些HTML内部属性,  这些属性以驼峰方式命名, 如 `className`取代了`class`, `onClick`取代了`onclick`.

JSX的花括号中可以使用任意JavaScript表达式(expressions), 注意要与声明(statements)区分.

## Lists in React

通过JSX可以渲染一些简单的变量, 现在尝试渲染一个列表. 可以使用JavaScript的`map`方法:

```javascript
import React from 'react';

const list = [
  {
    title: 'React',
    url: 'https://reactjs.org/',
    author: 'Jordan Walke',
    num_comments: 3,
    points: 4,
    objectID: 0,
  },
  {
    title: 'Redux',
    url: 'https://redux.js.org/',
    author: 'Dan Abramov, Andrew Clark',
    num_comments: 2,
    points: 5,
    objectID: 1,
  },
];


function App() {
  return (
    <div>
    ...
    <hr />
    {
      list.map(function(item) {
      return (
      <div key={item.objectID}>
        <span>
        <a href={item.url}>{item.title}</a>
        </span>
        <span>{item.author}</span>
        <span>{item.num_comments}</span>
        <span>{item.points}</span>
      </div>
      );
  })}
  </div>
  );
}

export default App;
```

### key

要注意的是, 列表中的每一个元素都应当有一个`key`属性. [比如](https://codepen.io/gaearon/pen/GjPyQr?editors=0011

```javascript
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((numbers) =>
  <li>{numbers}</li>
);

ReactDOM.render(
  <ul>{listItems}</ul>,
  document.getElementById('root')
);
```

Console会有如下提示:

```
"Warning: Each child in a list should have a unique 'key' prop.
```

于是 我们加上`key`:

```javascript
function NumberList(props) {
  const numbers = props.numbers;
  const listItems = numbers.map((number) =>
    <li key={number.toString()}>
      {number}
    </li>
  );
  return (
    <ul>{listItems}</ul>
  );
}

const numbers = [1, 2, 3, 4, 5];
ReactDOM.render(
  <NumberList numbers={numbers} />,
  document.getElementById('root')
);
```

`key`帮助React识别哪些项目已更改,添加或删除. 最好使用一个字符串来作为`key`, 通常是数据的ID, 没有ID的话用index, 但是如果列表项的顺序会发生更改, 则不建议用index作为`key`, 这会[影响性能](https://dev.to/jtonzing/the-significance-of-react-keys---a-visual-explanation--56l7)

## Component

上面的例子中`App()`与 `List()`杂糅在了一起, 现在将其分开:

```javascript
import React from 'react';

const list = [
  {
    title: 'React',
    url: 'https://reactjs.org/',
    author: 'Jordan Walke',
    num_comments: 3,
    points: 4,
    objectID: 0,
  },
  {
    title: 'Redux',
    url: 'https://redux.js.org/',
    author: 'Dan Abramov, Andrew Clark',
    num_comments: 2,
    points: 5,
    objectID: 1,
  },
];

function App() {
  return (
    <div>
			...
      <List />
    </div>
  );
}

function List() {
  return list.map(function(item) {
    return (
      <div key={item.objectID}>
        <span>
          <a href={item.url}>{item.title}</a>
        </span>
        <span>{item.author}</span>
        <span>{item.num_comments}</span>
        <span>{item.points}</span>
      </div>
    );
  });
}

export default App;
```

react的component可以类比class, 定义一个组件, 可以有多个实例.

在定义了一个组件之后, 可以把它当成HTML的`element`用在JSX里, 即被实例化.

## React DOM

React 的元素是不可变的, 创建元素后, 将无法更改其子元素或属性, 它表示特定时间的UI. 

为了更新UI, 我们可以创建新的元素然后传递给`ReactDOM.render()`, 一个计时器的例子如下:

```javascript
function tick() {
  const element = (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {new Date().toLocaleTimeString()}.</h2>
    </div>
  );
  ReactDOM.render(element, document.getElementById('root'));
}

setInterval(tick, 1000);
```















