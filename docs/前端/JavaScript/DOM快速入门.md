# DOM 快速入门 JavaScript

## 概述

DOM（Document Object Model）是一种跨平台和语言独立的接口，允许程序和脚本动态地访问和更新文档的内容、结构以及样式。简而言之，DOM 是一种将 HTML 和 XML 文档表示为树结构的方式，其中每个节点都是文档中的一个部分，比如一个元素或属性。

JavaScript 中内置一个 document 对象，该对象指向整个 DOM，用来表示当前 HTML 文档的对象。并提供了访问和操作网页内容的方法和属性。document 对象是所有 DOM 对象的根节点，它代表了整个 HTML 文档，包括页面的内容、结构和样式。

### document 的关键特性和用途

- 访问和修改页面内容：通过 `document` 对象，你可以查询和修改页面上的元素。例如，使用 `document.getElementById()` 或 `document.querySelector()` 等方法可以找到特定的元素，并通过修改这些元素的属性或样式来改变它们。
- 创建新元素：`document` 提供了创建新页面元素的方法，如 `document.createElement()`，允许动态地向页面添加新的内容。
- 注册事件处理程序：可以通过 `document` 或页面上的特定元素来注册事件处理程序，使得用户与页面交互时执行特定的脚本。
- 获取页面信息：`document` 对象包含了页面的信息，比如 URL（`document.URL`）、页面标题（`document.title`）以及页面的默认视图（`document.defaultView`）等。

```html
<!DOCTYPE html>
<html>
<head>
    <title>Document 示例</title>
</head>
<body>
    <div id="info">信息将在这里显示</div>
    <button onclick="updateContent()">点击我</button>

    <script>
        function updateContent() {
            // 获取id为"info"的元素
            var infoElement = document.getElementById("info");
            
            // 修改元素内容
            infoElement.innerHTML = "欢迎来到 JavaScript 世界！";
            
            // 修改元素样式
            infoElement.style.color = "green";
        }
    </script>
</body>
</html>
```

## 用法

DOM 提供了一系列的方法和属性，允许开发者访问和操作网页的内容、结构和样式。这些方法和属性可以大致分为几个类别，每个类别针对不同的操作和用途。

### 1. 查找元素

#### **getElementById(id)**: 根据元素的 ID 查找单个元素。

```javascript
let element = document.getElementById("myElement");
```

#### **getElementsByClassName(className)**: 根据元素的类名查找元素集合。

```javascript
let elements = document.getElementsByClassName("myClass");
```

#### **getElementsByTagName(tagName)**: 根据元素的标签名查找元素集合。

```javascript
let elements = document.getElementsByTagName("p");
```

#### **querySelector(selector)**: 根据 CSS 选择器查找第一个匹配的元素。

```javascript
let element = document.querySelector(".myClass");
```

#### **querySelectorAll(selector)**: 根据 CSS 选择器查找所有匹配的元素。

```javascript
let elements = document.querySelectorAll("div.myClass");
```

### 2. 创建、添加和删除元素

#### **createElement(tagName)**: 创建一个新的元素。

```javascript
let newDiv = document.createElement("div");
```

#### **appendChild(child)**: 向父元素添加一个子元素。

```javascript
document.body.appendChild(newDiv)
```

#### **removeChild(child)**: 从父元素中删除一个子元素。

```javascript
let parent = document.getElementById("parentElement");
let child = document.getElementById("childElement");
parent.removeChild(child);
```

### 3. 修改元素

#### **innerHTML**: 获取或设置元素的 HTML 内容。

```javascript
element.innerHTML = "<strong>新内容</strong>";
```

#### **textContent**: 获取或设置元素的文本内容。

```javascript
element.textContent = "更多文本";
```

#### **setAttribute(name, value)**: 设置元素的属性。

```javascript
element.setAttribute("href", "https://www.example.com");
```

#### **removeAttribute(name)**: 删除元素的属性。

```javascript
element.removeAttribute("href");
```

#### **classList.add(className)**: 给元素添加一个新的类。

```javascript
element.classList.add("new-class");
```

#### **classList.remove(className)**: 移除元素的一个类。

```javascript
element.classList.remove("old-class");
```

#### **classList.toggle(className)**: 切换元素的类。如果类存在，则删除它；如果不存在，则添加它。

```javascript
element.classList.toggle("active");
```

### 4. 处理事件

#### **addEventListener(event, function)**: 给元素添加一个事件监听器。

```javascript
element.addEventListener("click", function() {
  alert("元素被点击了!");
});
```

#### **removeEventListener(event, function)**: 移除元素的事件监听器。

```javascript
element.removeEventListener("click", functionName);
```

### 5. 操作样式

#### **style.property**: 直接修改元素的样式。

```javascript
element.style.color = "blue";
element.style.marginTop = "20px";
```

#### **getComputedStyle(element)**: 获取元素当前的所有计算样式。

```javascript
let styles = window.getComputedStyle(element);
let color = styles.getPropertyValue("color");
```

### 6. 查询和修改文档信息

#### **document.title**: 获取或设置文档的标题。

```javascript
document.title = "新页面标题";
```

#### **document.URL**: 获取文档的完整 URL。

```javascript
console.log(document.URL);
```

#### **document.documentElement**: 获取文档的根元素（如 HTML）。

```javascript
let rootElement = document.documentElement;
```

### 7. 与窗口或视图相关的功能

#### **document.viewport**: 不是标准 API，但可以通过 `window.innerWidth` 和 `window.innerHeight` 获取视窗（viewport）的宽度和高度。

```javascript
let width = window.innerWidth;
let height = window.innerHeight;
```

#### **scrollIntoView()**: 将元素滚动到视图中。

```javascript
element.scrollIntoView();
```
