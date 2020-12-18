## 选择器

三个最常用的选择器:

* tag selector
* class selector
* ID selector

```html
<!DOCTYPE html>
<html>
<head>
  <title>Tag, class, and ID selectors</title>
  <style>
    /* Tag selector*/
    h1 { color: red; }

    /* Class selector */
    .blue { color: blue; }

    /* ID selector */
    #greenLabel { color: green; }
  </style>
</head>
<body>
  <h1>This should be RED</h1>
  <h2 class="blue">This should be BLUE</h2>
  <h3 id="greenLabel">This is set to GREEN</h3>
  <h1>This is also RED</h1>
</body>
</html>
```

关于权重: 越具体的选择器权重越高, 即 ID>class>tag

### 属性选择器

```css
selector[attr]
selector[attr operator "value"]
```

用上述语法选择包含特定属性值的元素.

例子

```css
/* 存在title属性的<a> 元素 */
a[title] {
  color: purple;
}

/* 存在href属性并且属性值匹配"https://example.org"的<a> 元素 */
a[href="https://example.org"] {
  color: green;
}

/* 存在href属性并且属性值包含"example"的<a> 元素 */
a[href*="example"] {
  font-size: 2em;
}

/* 存在href属性并且属性值结尾是".org"的<a> 元素 */
a[href$=".org"] {
  font-style: italic;
}

/* 存在href属性并且属性值开头是"http://"的<a> 元素 */
a[href^= "http://"] {
  background-color: orangered;
}

/* 存在class属性并且属性值包含以空格分隔的"logo"的<a>元素 */
a[class~="logo"] {
  padding: 2px;
}
```

### 分组选择器

假设希望 h2 元素和段落都有灰色。为达到这个目的，最容易的做法是使用以下声明：

```css
h2, p {color:gray;}
```

### 通配符选择器

```css
* { font-style: italic }
*[title] { font-weight: bold; }
```

### 伪类选择器

常用的有 `:link` `:visited` `:hover`等

### 后代选择器

```html
<!DOCTYPE html>
<html>
<head>
  <title>Descendant selectors</title>
  <style>
    body {
      font-family: Verdana, Helvetica, sans-serif;
    }

    h1 strong {
      color: red;
    }

    div.important strong {
      color: white;
      background-color: #404040;
    }
  </style>
</head>
<body>
  <h1>This is <strong>Important</strong></h1>
  <div class="important">
    <p>
      Lorem ipsum dolor <strong>sit</strong>
      amet, consectetur <strong>adipiscing</strong>
      elit fusce vel sapien elit in malesuada semper mi,
      <strong>id</strong> sollicitudin urna fermentum.
    </p>
  </div>
  <div>
    <p>
      Lorem <strong>ipsum</strong> dolor sit amet, consectetur
      adipiscing elit fusce vel.
    </p>
  </div>
</body>
</html>
```

### 子选择器

 ```html
<!DOCTYPE html>
<html>
<head>
  <title>Child selectors</title>
  <style>
    article > h2 {
      font-style: italic;
    }
  </style>
</head>
<body>
  <h2>Outside of article</h2>
  <article>
    <h2>Within article</h2>
    <div>
      <h2>Not directly within article</h2>
    </div>
  </article>
</body>
</html>
 ```

此外, 用伪类选择器也可达到效果

如 `article:first-child`

### 相邻选择器

```html
<!DOCTYPE html>
<html>
<head>
  <title>Sibling selectors</title>
  <style>
    body {
      font-family: Verdana, Helvetica, sans-serif;
      margin-left: 16px;
    }
    p { margin: 0; }
    h1 + p { background-color: yellow; }
    h1 + span { background-color: orangered; }
    h1 ~ p { font-style: italic; }
    h1 ~ span { 
      display: block;
      font-weight: bold;
    }
    h1 ~ * { margin-left: 24px; }
  </style>
</head>
<body>
  <h1>I'm looking for my siblings...</h1>
  <p>I'm a direct sibling (p)</p>
  <span>I'm a (span) sibling of (h1)</span>
  <p>I'm another sibling of type (p)</p>
  <p>Let me tell you, I'm (p), too</p>
  <span>I'm another span of (h1) :-)</span>
</body>
</html>
```



## Style Properties

### Colors

* RGB表示 `color: rgb(100%, 0%, 0%); /* red */`
* RGBA表示 A指的是透明度(transparency) `background-color: rgba(249, 163, 197, 0.5); /* pink */`

* 16进制表示 `color: #ff0000; /* red */`
* HSL表示 HSL (hue, saturation, and luminance) 色相饱和度亮度 `color: hsl(0, 100%, 50%); /* red */`

### Size

* em 为font-size的倍数
* rem
* percentage

### URL

`background-image: url(Images/pageBkg.png)`

### 层叠顺序

*越具体的选择器优先级越高, 优先级相同则根据选择*

1. `!important` `p { color: blue !important; }`
2. 内部样式 `<h1 style="color: green;">Heading</h1>`
3. ID selector
4. lass, attribute, or pseudo-selector
5. element selectors
6. universal selector



数值计算计算方式:

* A - the count of ID selectors
* B - the count of class selectors, attributes selectors, and pseudo-classes
* C - the count of type selectors and pseudo-elements

```css
/* A=0, B=0, C=0 -> specificity = 0 */
*

/* A=0, B=0, C=1 -> specificity = 1 */
li

/* A=0, B=0, C=2 -> specificity = 2 */
ul li

/* A=0, B=0, C=3 -> specificity = 3 */
ul ol+li

/* A=0, B=1, C=1 -> specificity = 11 */
h1 + *[href$='http:']

/* A=0, B=1, C=3 -> specificity = 13 */
ul ol li.spec

/* A=0, B=2, C=1 -> specificity = 21 */
li.spec.next

/* A=1, B=0, C=0 -> specificity = 100 */
#myTag

/* A=1, B=0, C=1 -> specificity = 101 */
#yourTag:not(foo)
```

根据位置确定优先级:

1. The first priority location is the `<style>` element in the head of the HTML document.
2. The second priority location is a style sheet imported by an `@import` at-rule embedded within the `<style>` element
3. The third priority location is a style sheet attached by a `<link>` element.
4. The fourth priority location is a style sheet imported by an `@import` at-rule embedded within a style sheet attached by a `<link>` element.
5. The fifth priority location is a style sheet attached by an end-user. An exception is made for `!important` rules in an end-user style sheet. These rules are given the highest priority.
6. And last, the sixth (lowest) priority location is the default style sheet supplied by a browser.

## Media

跨设备渲染



# 基本样式模式

## Text formatting

[Fundamental text and font styling](https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Fundamentals)

* Font: color, font-family, font-size, font-style, font-weight, text-transform, text-decoration, text-shadow
* Text layout: text-align, text-indent, line-height, letter-spacing, word-spacing

[List style](https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Styling_lists)

* list-style, list-style-image, list-style-position, list-style-type

使用[web fonts](https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Web_fonts)

```css
@font-face {
  font-family: "myFont";
  src: url("myFont.woff");
}
html {
  font-family: "myFont", "Bitstream Vera Serif", serif;
}
```

### Box model

margin, border, padding, 外, 边, 内












































