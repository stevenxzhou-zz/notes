## Node Basics


#### 1. HTML 6个不同个Node类型

1. Document， 对应`Node.DOCUMENT_NODE` (9)
* e.g. `window.document`
2. DocumentType, 对应`Node.DOCUMENT_TYPE_NODE`(10)
* e.g. `<!DOCTYPE html>`
3. ELEMENT, 对应`Node.ELEMENT_NODE` (1)
* e.g. `<body> <a>`
4. Attribute, 对应`Node.ATTRIBUTE_NODE` (2)
* e.g. `<a class=“right”/>`
5. Text,  对应`Node.TEXT_NODE` (3)
* e.g. `#Text`
6. DocumentFragment, 对应`Node.DOCUMENT_FRAGMENT_NODE` (11)


#### 2. Node的基本属性

```javascript
//有以下方法可以确认某一个node的Type
document.querySelector(‘a’).nodeType === 1
document.querySelector(‘a’).nodeType === Node.ELEMENT_NODE

// 查看当前node的终极owner node, 通常也就是document node
node.ownerDocument

// 查看当前node的向下相邻的姊妹
node.nextSibling

// 常看当前node的向上相邻的姊妹
node.previousSibling

// 查看当前node紧相邻的父级node
node.parentNode

// 注意如果是确定要查看父级的Element，则可以使用下面的专用指令
// 而且如果当前node之前如果有空格，那么parentElement将会把他识别为#text
node.parentElement

// element 设置css
element.style.color=red
```

#### 3. textContent和innerText的使用区别

###### textContent
- 赋值时会将引号里边的HTML字符按照字符串读取
- 读的时候则会忽略所有HTML忽略，只保留文字
- 不会受css变化的影响，对整个document可见
- 在text， comment和XML中的nodeValue和textCotent的属性完全一致

###### innerText
- 会依赖css的变化， 比如css设置文字隐藏，则innerText不会出任何文本


#### 4. Node 和 Element 独占的常用方法

###### Node
- `firstChild()`
- `lastChild()`
- `childNodes()`
- `insertBefore(new, sibiling)`
- `insertAfter()`
- `removeChild()`
- `replaceChild()`

###### Element
- `firstElementChild()`
- `children()`


## Interview Questions:  
1. How to delete a node from it’s parent?  
2. How to recursively print all the nodes in the document?  
3. How to remove all the child nodes from their parent node?  