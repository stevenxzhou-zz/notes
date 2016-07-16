#### 1. 什么是Sass?
Sass是为传统CSS提供的预处理工具，通过Sass，程序员可以写出符合传统编程思维的代码，并通过Sass自带的编译工具，编译成传统的CSS共Web页面调用。

#### 2. 安装和使用
```bash
# 安装, 如果没有gem命令，则需要安装Ruby的运行环境
gem install sass

# 直接输出编译好的css代码
sass test.scss
	
# 输出编译好的css代码到指定文件
sass test.css test.css
	
# 以不同的风格输出，开发用nested，prod用compressed
—style nested/expanded/compact/compressed
	
# 动态的loop跟踪文件的变动，并及时重新编译
—watch input.scss:output.css
—watch app/sass:public/stylesheets
```
#### 3. 基本用法
3.1 变量
```css
$blue: #1875e7;
$side: left;
div {
	color: $blue;
	border-#{$side}-radius: 5px;
}
```
3.2 计算功能
```css
body {
	margin: (14px/2);
	top: 50px + 100px;
	right: $var * 10%;
}
```
3.3 嵌套
```css
/* 传统css */
div h1 {
	color: red
}
/* Sass */
div {
	h1 {
		color: red;
	}
}
/* 传统css */
p {
	border-color: red;
}
/* Sass 属性嵌套 注意冒号!*/
p {
	border: {
		color: red;
	}
}
/* 传统css */
a:hover{
	color: #ffb3ff;
}
/* Sass 引用父元素 */
a {
	&:hover { color: #ffb3ff; }
}
```
3.4 注释
`//` 临时行注释，编译后省略  
`/* */` 编译后保存，压缩后省略  
`/*! 重要注释 */` 不会被编译器省略, 也不会再压缩后省略

#### 4. 代码的重用
4.1 继承
```css
.class1 {
	border: 1px slid #ddd;
}
.class2 {
	@extend .class1
	font-size: 120%;
}
```
4.2 Mixin 
```css
@mixin left {
	float: left:
	margin-left: 10px;
}
div {
	@include left;
}
/* 指定参数和Default参数 */
@mixin left($value: 10px) {
	float: left;
	margin-right: $value;
}
div {
	@include left(20px);
}
/* 生成浏览器前缀 */
@mixin rounded($vert, $horz, $radius: 10px) {
	border-#{$vert}-#{$horz}-radius: $radius;
	-moz-border-#{$vert}-#{$horz}-radius: $radius;
	-webkit-border-#{$vert}-#{$horz}-radius: $radius;
}
# nabber li {@include rounded(top, left);}
# footer {@include rounded(top, left, 5px);}
```
4.3 颜色函数
```css
lighten(#cc3, 10%) // #d6d65c
darken(), graysale(), complement()
```
4.4 插入文件
和传统css一样用`@import “path/to/filename.scss”`

#### 5. 高级语法
5.1 条件语句
```css
/* @if @else*/
p {
	@if 1 + 1 == 2 {border: 1px solid;}
	@if 5 < 3 {border: 2px dotted;} @else  {border: 3px dotted;}
}
```
5.2 循环语句
```css
/* @for 10个border的css */
@for $i from 1 to 10 {
	.border-#{$i} {
		border: #{$i}px solid blue;
	}
}
/* @each */
@each $memeber in a, b, c, d {
	.#{$memeber} {
		background-image: url(“/image/#{$member}.jpg”);
	}
}
```
5.3 自定义函数
```css
@function double($n) {
	@return $n * 2;
}
#sidebar {
	width: double(5px;);
}
```

#### 参考
[1] [SASS用法指南](http://www.ruanyifeng.com/blog/2012/06/sass.html)  
[2] [为您详细比较三个 CSS 预处理器（框架）：Sass、LESS 和 Stylus](http://www.oschina.net/question/12_44255)