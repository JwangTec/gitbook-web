# CSS布局模型

##css布局模型

css 布局模型能够决定盒模型直接如何排列

![](../../pics/css/IMGS/flex_01.gif)

css的布局模式分类

1、流动模型（Flow）

2、浮动模型 (Float)

3、层模型（Layer）

## Flow 流动模型

流动（Flow）是默认的网页布局模式。也就是说网页在默认状态下的 HTML 网页元素都是根据流动模型来分布网页内容的。

流动布局模型具有2个比较典型的特征：

1. 块状元素都会在所处的包含元素内自上而下按顺序垂直延伸分布，因为在默认状态下，块状元素的宽度都为100%。实际上，块状元素都会以行的形式占据位置。

	```
	<div id="box2">box2</div><!--块状元素，由于没有设置宽度，宽度默认显示为100%-->
	<h1>标题</h1><!--块状元素，由于没有设置宽度，宽度默认显示为100%-->
	<p>文本段文本段段文本段文本段文本段文本段文本段。</p><!--块状元素，由于没有设置宽度，宽度默认显示为100%-->
	
	<div id="box1">box1</div>
	```
	
2. 第二点，在流动模型下，内联元素都会在所处的包含元素内从左到右水平分布显示。（内联元素可不像块状元素这么霸道独占一行）

右侧代码编辑器中内联元素标签a、span、em、strong都是内联元素。

	```
	<em>emmmm..</em>
	
	<strong>strong..</strong>
	
	<b>b..</b>
	
	```
	
## float 浮动模型

块状元素这么霸道都是独占一行，如果现在我们想让两个块状元素并排显示，怎么办呢？不要着急，设置元素浮动就可以实现这一愿望。

任何元素在默认情况下是不能浮动的，但可以用 CSS 定义为浮动，如 div、p、table、img 等元素都可以被定义为浮动。

```
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>

        div{
            width:200px;
            height:200px;
            border:2px red solid;
            float:left;
        }
    </style>
</head>
<body>



<div id="div1"></div>
<div id="div2"></div>

```

还可以把div分布到两边

```
        #div3{
            width:200px;
            height:200px;
            border:2px red solid;
            float:left;
        }

        #div4{
            width:200px;
            height:200px;
            border:2px red solid;
            float:right;
        }
        
<div id="div3"></div>
<div id="div4"></div>
```

## 层模型

层模型能让层一样可以对每个图层能够精确定位操作

层模型有三种形式：

1、绝对定位(position: absolute)

2、相对定位(position: relative)

3、固定定位(position: fixed)

#### 1. 绝对定位,把图形定义在绝对的位置

	```
	
	<!DOCTYPE HTML>
	<html>
	<head>
	    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
	    <title>absolute样式</title>
	    <style type="text/css">
	        #div1{
	            width:200px;
	            height:200px;
	            border:2px red solid;
	            position:absolute;
	            left:10px;
	            top:200px;
	
	
	        }
	
	
	        #div2{
	            width:200px;
	            height:200px;
	            border:2px red solid;
	            position:absolute;
	            left:20px;
	            top:300px;
	
	
	        }
	    </style>
	</head>
	<body>
	<div id="div1"></div>
	<div id="div2"></div>
	</body>
	</html>
	```
	
	
#### 2. 相对定位


如果想为元素设置层模型中的相对定位，需要设置position:relative（表示相对定位），它通过left、right、top、bottom属性确定元素在正常文档流中的偏移位置。相对定位完成的过程是首先按static(float)方式生成一个元素(并且元素像层一样浮动了起来)，然后相对于以前的位置移动，移动的方向和幅度由left、right、top、bottom属性确定，偏移前的位置保留不动。

	```
	
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Title</title>
	    <style>
	
	
	
	        #div1{
	            width:200px;
	            height:200px;
	            border:2px red solid;
	            position:relative;
	            left:100px;
	            top:50px;
	        }
	    </style>
	</head>
	<body>
	
	
	
	
	<div id="div1"></div>
	</body>
	</html>
	```

#### 3.固定定位

fixed：表示固定定位，与absolute定位类型类似，但它的相对移动的坐标是视图（屏幕内的网页窗口）本身。由于视图本身是固定的，它不会随浏览器窗口的滚动条滚动而变化

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>


        p{
            width:200px;
            height:200px;
            border:2px red solid;
            position:fixed;
            left:100px;
            top:50px;
        }

        div{
            width:200px;
            height:200px;
            border:2px red solid;

            left:100px;
            top:50px;
        }
    </style>
</head>
<body>




<p>文本文本文本文本文本文本本文本文<p>



</body>
</html>

```

## 相对定位和绝对定位的组合使用

#### 概述

上面看到 绝对定位是基于整个html的原点来进行位移的,其实我们也可以让绝对定位的参照点为某个元素,这就涉及到他们的组合使用了

#### 使用

1. 参照定位的元素必须是相对定位元素的前辈元素：

	```
	<div id="box1"><!--参照定位的元素-->
	    <div id="box2">相对参照元素进行定位</div><!--相对定位元素-->
	</div>
	
	```

2. 参照定位的元素必须加入position:relative;

	```
	
	#box1{
	    width:200px;
	    height:200px;
	    position:relative;        
	}
	
	```

3. 定位元素加入position:absolute，便可以使用top、bottom、left、right来进行偏移定位了。

	```
	#box2{
	    position:absolute;
	    top:20px;
	    left:30px;         
	}
	```

4. 组合使用
	
	```
	
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Title</title>
	    <style>
	        #d1 {
	            position: relative;
	            border: 1px solid red;
	            height: 50px;
	            width: 50px;
	        }
	
	        #d2 {
	            position: absolute;
	            top: 10px;
	            left: 10px;
	            border: 1px solid red;
	
	            height: 10px;
	            width: 10px;
	        }
	    </style>
	</head>
	<body>
	<div id="d1">
	    <div id="d2"></div>
	</div>
	</body>
	</html>
	
	```