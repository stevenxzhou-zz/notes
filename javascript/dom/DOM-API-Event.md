#### EventTarget接口的三个方法
>`Element`, `document`节点，`window`对象都实现了这个接口，另外`XMLHttpRequest, AudioNode, AudioContext`等浏览器内置对象也实现了这个接口。所有的这些都可以共享`addEventListener(), removeEventListener(), dispatchEvent()`这三种方法。

需要特别注意的是`addEventListener()`有三个参数, 分别是`type, listener, useCapture`. 其中`useCapture`在老式浏览器中非可选参数，所以必须写。在新浏览器中为可选，默认为`False`, 表示在从window向下遍历元素的时候，每当发现这个名字的事件，不要当即触发，而只在冒泡阶段，也就是发现Target之后，往回向window遍历的时候再触发。主要涉及的就是想要listener以什么样的顺序被激活。至上而下还是至下而上，默认是至下而上。

`dispatchEvent()`是用来触发事件的，一般情况下返回值为`true`，但是如果事件被阻止触发`Event.preventDefault()`, 返回值为`false`。

#### 1. 监听函数
DOM提供三种方式来触发监听方法listener
1. 通过Element的事件属性，例如`onclick=‘console.log(‘触发事件’)’`, 这个方法只会在冒泡阶段触发。
2. 直接在Js中通过Element节点来触发， 如`div.onclick = function(){console.log(‘触发事件’)};`，这个方法也只会在冒泡阶段触发。
3. 上面提到过的`addEventListener()`方法。这个可以设定是想在捕获阶段还是冒泡阶段触发。还可以针对同一个事件，添加多个监听函数。另外还可以部署在`window`, `XMLHttpRequest`的上面。因此推荐使用这个方法。只有在考虑浏览器兼容问题的时候（因为1，2两种方法所有浏览器都通用）才使用1，2方法。
4. 特别需要注意在监听器函数里this对象的指向问题。`addEventListener()`调用的监听函数会指向Element标签内的attribute, 而标签内的`onclick=func()`则会指向window。如需要指向当前标签内的attribute，需要写成这种形式`onclick=func(this)`。

#### 2. 事件的传播
事件的传播有三个阶段`capture phase`,  `target phase`,  `bubbling phase`， 其中需要注意target阶段相当于合并了capture和bubbling的阶段， 所以在把useCapture设定true和false的时候，会分别执行，只是显示的形式会是target而已。[举例](http://codepen.io/stevenz1987/pen/kXGxxw)。

事件的代理是一种通过父节点定义监听函数，利用冒泡阶段的级联触发，监听子元素事件的方式。[举例](http://codepen.io/stevenz1987/pen/XKZzkV)

#### 3. 定义一个Event对象
可以通过如下方法自定义，并触发一个Event对象
```javascript
// bubbles 表示对象是否冒泡
var ev = new Event(“look”, {“bubbles”: true, “cancelable”: false});
document.dispatchEvent(ev);
```
#### 4. Event对象具有如下属性
- `bubbles` 是否会冒泡
- `eventPhase` 表示事件所处阶段，0 表示没有方式, 1 捕获阶段, 2 到达目标阶段, 3 冒泡阶段。
- `cancleable` 表示事件是否可以通过 `event.preventDefault()`来取消对应事件，同时可以通过`event.defaultPrevented`属性来查看对应事件是否调用过`preventDefault()`方法。
- `currentTarget` 和`target`
- `currentTarget` 对应的是绑定监听函数的节点，也就是监听函数内的this对象，而`target`对应的是鼠标实实在在点击的那个点，这个点并不一定绑定了监听函数，但是在`currentTarget`的监听函数会因其激活了冒泡效应，进而激活了绑定监听函数的节点。有些时候，`currentTarget`和`target`会对应同一个节点，也就是在绑定监听函数的节点没有子节点的情况。
- `type, detail, timeStamp`
  - `type` 事件类型 如`click`, 大小写敏感
  - `detail` 和具体的事件类型有关, 如dbclick对应的`detail`值总是2
  - `timeStamp` 表示事件发生的时间
- `preventDefault()`
  - 可以阻止浏览器预先设置的时间。例如a标签点击后的跳转，还有checkbox点击后会选择。
- `stopPropagation()`
  - 阻止冒泡过程中，当前节点之上的事件被触发。而当节点本身就算定义了多个事件，也同样会被触发。
- `stopImmediatePropagation()`
  - 除了具备`stopPropagation()`的功能以外，还会阻止当前节点其他在紧随其后定义的事件被触发。

## 参考：
[1] 阮一峰: [Javascript教学 DOM Event对象](http://javascript.ruanyifeng.com/dom/event.html)