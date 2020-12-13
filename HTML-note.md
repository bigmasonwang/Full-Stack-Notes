## 文档类型

`!DOCTYPE` 标签表示当浏览器解析文档时要使用的标记类型, `!DOCTUPE html` 表示该文档为HTML5. 

## 注释

使用`<!-- ... -->` 标记注释, 例如

```html
<!-- Display the “see also” section -->
<p>You can find more information on this topic:</p>
```

## \<head> 标签

在\<head> 标签内部必须包含 `<title>` 元素, 可选的元素包括`<style>`, `<link>`, `<script>`, `<noscript>`, `<meta>`, 和 `<base>`.

`<title>` 标记了页面的标题, 会体现在浏览器的工具栏和收藏夹以及搜索引擎的结果展示上.

`<style>` 标记了样式表, 如

```html
<head>
  <title>Table of Contents</title>
  <style>
    body {
      font-family: Verdana, Arial, sans-serif;
    }
  </style>
</head>
```

如果想用外部样式表, 我们需要用`<link>` 链接css文件

```html
<head>
  <title>Table of Contents</title>
  <link href="style.css" rel="stylesheet" />
</head>
```

`herf` 属性链接了目标文档, `rel` 熟悉描述了页面和链接文档的关系(relationship).

 `<script>` 标签定义了JavaScript代码片段. 我们要注意在浏览器读到`<script>`标签后会立即处理, 因此如果把`<script>`放在 `<head>`标签内, 代码会在浏览器读到页面内容前执行.

与 `<script>`相伴的是`<noscript>`, 用于在页面不能使用JavaScript时展示信息, 如

```html
<head>
  <script>
    document.write("Hello from JavaScript");
  </script>
  <noscript>Sorry, your browser does not support JavaScript</noscript>
</head>
```

搜索引擎会检视文档内容和元数据(metadata), 如 author, keywords等等, 我们可用 `<meta>`标签声明, 如

```html
<head>
  <title>My book's Table of Contents</title>
  <meta name="description" content="This page provides you the TOC">
  <meta name="author" content="Istvan Novak">
  <meta name="keywords" content="html,css,javascript">
</head>
```

此外 `<meta>` 还可描述页面编码, 如

```html
<meta charset="utf-8">
```

## \<body>标签定义HTML内容

可分为行内元素(如 `<strong>`, `<em>`, `<span>`)和块级元素(如`<p>`, `<h1>`, `<div>`).

HTML5 定义了一系列标签来渲染文本

| tag               | 含义               | 例子                                                         |
| ----------------- | ------------------ | ------------------------------------------------------------ |
| `<abbr>`          | abbreviation       | `This website is all about <abbr title="HyperText Markup Language">HTML</abbr>.` |
| `<b>`/ `<strong>` | bold               | `<b> HTML5 is so cool </b>`                                  |
| `<bdo>`           | direction override | `<p><bdo dir="rtl">This paragraph will go right-to-left.</bdo></p>` |
| `<big>`           | big                | `<big> HTML5 is so cool! </big>`                             |
| `<code>`          |                    |                                                              |
| `<del>`           | delete             |                                                              |
| `<dfn>`           | definition         |                                                              |
| `<em>`            | emphasize          |                                                              |
| `<i>`             | itallic            |                                                              |
| `<ins>`           | insert             |                                                              |
| `<mark>`          | highlight          |                                                              |
| `<pre>`           | preserve           |                                                              |
| `<q>`             | quotation          |                                                              |
| `<samp>`          | sample             |                                                              |
| `<sub>`           | subscript          |                                                              |
| `<sup>`           | superscript        |                                                              |
| `<u>`             | underline          |                                                              |
| `<var>`           | variable           |                                                              |
|                   |                    |                                                              |

可以用`<ul>`和`<ol>`标签添加列表, 如

```html
<!DOCTYPE html>
<html>
<head>
  <title>Using HTML Lists</title>
</head>
<body>
  <p>This is an <em>unordered</em> list:</p>
  <ul>
    <li>Apple</li>
    <li>Banana</li>
    <li>Pear</li>
  </ul>
  <p>This is an <em>ordered</em> list:</p>
  <ol>
    <li>Open the door</li>
    <li>Step out</li>
    <li>Start your journey</li>
  </ol>
  <p>This ordered list is customized</p>
  <ol start="5" reversed type="I">
    <li>Roman 5</li>
    <li>Roman 4</li>
    <li>Roman 3</li>
  </ol>
</body>
</html>
```

此外, 无序列表广泛应用于导航结构如菜单和工具栏.

## 语义化 -- 不要通篇\<div>

一个页面可以写成这样的形式

```html
<body>
 	<div class="header">
    something
  </div>
  <div class="mainContent">
    something
  </div>
  <div class="footer">
    something
  </div>
</body>
```

这种形式不利于搜索引擎或一些分析工具理解页面结构.

取而代之, 我们可以用[语义元素](https://www.w3schools.com/html/html5_semantic_elements.asp), 例如

```html
<body>
  <header>head</header>
  <section>1</section>
  <section>2</section>
  <footer>foot</footer>
</body>
```

相比之下, 这种形式更易理解与维护. 

### Headers

The `header` element [represents](https://html.spec.whatwg.org/multipage/dom.html#represents) a group of introductory or navigational aids.

搜索引擎会给`<header>`中的词相较`<section>`更高的权重; 另外也可以很快地根据各个`<section>`生成导航栏.

`<header>`可以作为整个页面的标题, 也可作为部分内容的标题. 例如

```html
<!DOCTYPE html>
<html>
<head>
  <title>Using Page Headers (no style)</title>
</head>
<body>
  <header class="pageHeader">
    <h1>Articles about Visual Studio</h1>
    <p class="byLine">edited by Istvan Novak</p>
  </header>
  <article>
    <header class="articleHeader">
      <h2>Visual Studio Platform and Extensibility</h2>
      <h3>April, 2008</h3>
    </header>
    <div class="mainContent">
      <p>
        Sed tincidunt hendrerit iaculis. Phasellus eget 
        dolor ac nisi porttitor porta. Integer tortor sem, 
        condimentum a auctor ac, interdum eget. 
      </p>
    </div>
  </article>
  <article>
    <header class="articleHeader">
      <h2>Creating Visual Studio Packages</h2>
      <h3>June, 2009</h3>
    </header>
    <div class="mainContent">
      <p>
        Phasellus condimentum suscipit molestie. Praesent 
        volutpat nunc orci, rhoncus accumsan nunc sodales 
        molestie. Proin quis risus eget mauris ultricies tempor. 
      </p>
    </div>
  </article>
</body>
</html>
```

这个例子中, 我们用不同的class区分了页面标题和文章标题; 注意到用了`<h2>`,`<h3>`两个标题显得有些混乱, 一个可改进的方法是使用 `<hgroup>` 标签:

```html
<header class="articleHeader">
  <hgroup>
    <h2>Creating Visual Studio Packages</h2>
    <h3>June, 2009</h3>
  </hgroup>
  <p class="author">John Doe</p>
</header>
```

### Footers

The `footer` element [represents](https://html.spec.whatwg.org/multipage/dom.html#represents) a footer for its nearest ancestor [sectioning content](https://html.spec.whatwg.org/multipage/dom.html#sectioning-content-2) or [sectioning root](https://html.spec.whatwg.org/multipage/sections.html#sectioning-root) element. A footer typically contains information about its section such as who wrote it, links to related documents, copyright data, and the like.

可用于标记每篇文章的阅读量, 页面末尾的版权信息等等





































