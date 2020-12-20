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

### JSX

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

JSX的花括号中可以使用任意JavaScript表达式(expressions), 注意要与声明(statements)区分





















