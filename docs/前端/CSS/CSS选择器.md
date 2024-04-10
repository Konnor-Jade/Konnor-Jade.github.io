# CSS 选择器

CSS 选择器是 CSS 规则的一部分，它们决定了哪些元素应该被应用相应的样式规则。CSS 选择器的种类繁多，功能强大，能够精确地定位到文档中的元素。了解和掌握不同类型的选择器对于编写高效和可维护的样式表至关重要。🎨🔍

## 基本选择器

### **通用选择器（Universal Selector）**:

- 语法：`*`
- 作用：匹配文档中的所有元素。
- 示例：`* { margin: 0; padding: 0; }`

### **类型选择器（Type Selector）**:

- 语法：`elementname`
- 作用：匹配所有给定类型的元素。
- 示例：`div { color: blue; }`

### **类选择器（Class Selector）**:

- 语法：`.classname`
- 作用：匹配具有指定类的元素。
- 示例：`.alert { font-weight: bold; }`

### **ID 选择器（ID Selector）**:

- 语法：`#idname`
- 作用：匹配具有指定 ID 的元素。
- 示例：`#header { background-color: #333; }`

### **属性选择器（Attribute Selector）**:

属性选择器根据元素的属性及属性值来选择元素。

- 语法：`[attribute="value"]`
- 作用：匹配具有指定属性的元素。
- 示例：`input[type="text"] { border: 1px solid #ccc; }`

例子：选择具有特定属性的元素

```css
/* 选择所有具有 target 属性的 <a> 元素 */
a[target] {
  color: red;
}
```

例子：选择属性值等于特定值的元素

```css
/* 选择 target="_blank" 的所有 <a> 元素 */
a[target="_blank"] {
  font-weight: bold;
}
```

## 组合选择器

### **后代选择器（Descendant Selector）**:

- 语法：`A B`
- 作用：选择 A 元素内部的所有 B 元素。
- 示例：`ul li { list-style-type: square; }`

### **子选择器（Child Selector）**:

- 语法：`A > B`
- 作用：选择直接作为 A 元素子元素的 B 元素。
- 示例：`div > p { color: red; }`

### **相邻兄弟选择器（Adjacent Sibling Selector）**:

- 语法：`A + B`
- 作用：选择紧接在 A 元素之后的同级 B 元素。
- 示例：`h1 + p { font-weight: bold; }`

### **通用兄弟选择器（General Sibling Selector）**:

- 语法：`A ~ B`
- 作用：选择 A 元素之后的所有同级 B 元素。
- 示例：`h1 ~ p { color: green; }`

## (待定)伪类选择器

### **链接伪类**:

- `:link`、`:visited`、`:hover`、`:active` 用于定义链接的不同状态。
- 示例：`a:hover { color: red; }`

例子：链接伪类

```css
/* 选择鼠标悬停在其上的链接 */ 
a:hover { color: green; }
```

### **结构伪类**:

- `:first-child`、`:last-child`、`:nth-child(n)` 用于根据元素在其父元素中的位置选择元素。
- 示例：`p:first-child { font-size: 20px; }`

例子：结构性伪类

```css
/* 选择父元素的第一个 <p> 子元素 */ 
p:first-child { color: blue; }
```

### **输入表单伪类**:

- `:focus`、`:disabled` 用于根据表单元素的状态选择元素。
- 示例：`input:focus { border-color: blue; }`

## (待定)伪元素选择器

### **::before** 和**::after****:**

- 用于在元素内容的前面或后面插入新内容。
- 示例：`p::before { content: "注意："; }`

### **::first-line** 和 **::first-letter**:

- 分别用于选择元素的第一行和第一个字母。
- 示例：`p::first-letter { font-size: 200%; }`

伪元素选择器用于样式化元素的特定部分，或是创建不存在于文档树中的元素。

例子：用于选择元素的第一行

```css
/* 选择每个 <p> 元素的第一行 */ 
p::first-line { 
    font-variant: small-caps; 
}
```

例子：在元素前后添加内容

```css
/* 在每个 <h1> 元素前添加一个装饰性图形 */ 
h1::before { 
    content: url(arrow.png); 
} 

/* 在每个 <h1> 元素后添加一行文本 */ 
h1::after { 
    content: "结束"; 
}
```
