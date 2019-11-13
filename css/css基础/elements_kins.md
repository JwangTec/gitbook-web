# css元素分类

## 概述

在CSS中，html中的标签元素大体被分为三种不同的类型：块状元素、内联元素(又叫行内元素)和内联块状元素。

常用的块状元素有：

```
<div>、<p>、<h1>...<h6>、<ol>、<ul>、<dl>、<table>、<address>、<blockquote> 、<form>
```

常用的内联元素有：

```
<a>、<span>、<br>、<i>、<em>、<strong>、<label>、<q>、<var>、<cite>、<code>
```

常用的内联块状元素有：

```
<img>、<input>
```

## 块级元素 block

#### 块级元素特点：

1、每个块级元素都从新的一行开始，并且其后的元素也另起一行。

2、元素的高度、宽度、行高以及顶和底边距都可设置。

3、元素宽度在不设置的情况下，是它本身父容器的100%（和父元素的宽度一致），除非设定一个宽度


```
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>内联块状元素</title>
<style type="text/css">
div,p{background:pink;}
</style>
</head>
<body>
<div>div1</div>
<div>div2</div>
<p>段落1段落1段落1段落1段落1</p>
</body>
</html>

```
## 内联元素 inline

#### 内联元素特点:

1、和其他元素都在一行上；

2、元素的高度、宽度及顶部和底部边距不可设置；

3、元素的宽度就是它包含的文字或图片的宽度，不可改变。

```

<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=gb2312" />
<title>行内元素标签</title>
<style type="text/css">
a,span,em{
	background:pink;/*设置a、span、em标签背景颜色都为粉色*/
}
</style>
</head>
<body>
<a href="http://www.baidu.com">百度</a>
<a href="http://www.imooc.com">慕课网</a>
<span>33333</span>
<span>44444</span><em>555555</em>
</body>
</html>

```

## 内联块状 inline-block

#### 特点

1、和其他元素都在一行上；

2、元素的高度、宽度、行高以及顶和底边距都可设置。

```

<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=gb2312" />
<title>内联块状元素</title>
<style type="text/css">
a{
    
	width:20px;/*在默认情况下宽度不起作用*/
	height:20px;/*在默认情况下高度不起作用*/
	background:pink;/*设置背景颜色为粉色*/
	text-align:center; /*设置文本居中显示*/
	display:inline-block;
}
</style>
</head>
<body>
<a>1</a>
<a>2</a>
<a>3</a>
<a>4</a>
</body>
</html>

```

## 类型转换

通过display:block 我们可以将元素转换类型

```
a{display:block;}

```