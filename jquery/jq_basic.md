# JQuery 选择器

## 1. 基本的选择器选择器

#### 概述

1. 所有的

#### 1.jQuery id选择器

使用说明: ```$('#id')```,来选择,基本上所有的Jquery选择器都会以 ```$()```开头,就像我们的css选择器一样

	```
	
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Title</title>
	    <script src="../sources/jq/jq.js"></script>
	</head>
	<body>
	<p id="html1">jQuery is good</p>
	
	<script>
	    $('#html1').css('border','1px solid');
	</script>
	</body>
	</html>
	
	
	```
	
> jquery的使用方式和我们dom操作不一样,他是封装了dom操作的,所以要按照他的方式去修改属性

练习: 回忆一下,如果使用dom操作,我们应该怎么写?

#### 类选择器

使用说明: ```$('.class')```

```


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="../sources/jq/jq.js"></script>
</head>
<body>
<p class="c1">jQuery is good</p>
<p class="c1">jQuery is good</p>
<p class="c1">jQuery is good</p>
<script>
    $('.c1').css('border','1px solid');
</script>
</body>
</html>

```

> 使用类选择器,我们直接去操作所有选中的元素,不用像dom一样去遍历之后才行

练习: 使用dom操作去完成上面的代码

#### 元素选择器

使用说明: ```$('element')```

```

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="../sources/jq/jq.js"></script>
</head>
<body>
<p class="c1">jQuery is good</p>
<p class="c1">jQuery is good</p>
<p class="c1">jQuery is good</p>
<script>
    $('p').css('border','1px solid red');
</script>
</body>
</html>

```

同理,元素选择器可以直接操作所有选中的标签,不用我们去使用遍历的方式

#### 全选择器

如同我们的css代码一样 * {padding: 0; margin: 0;}

```
$("*").css('border','1px solid red')
```


#### 层级选择器

我们可以在Jquery中使用层级选择器来代替css中的几种层级选择器

| 选择器  |  css |  jquery | 
|---|---|---|
|  子选择器  |  p>c | ```$('p > c')```  | 
|  后代选择器选择器  | p c | ```$('p  c')```  | 
|  相邻选择器  |  p+c | ```$('p + c')```  | 
|  子选择器  |  p~c | ```$('p ~ c')```  |

```

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="../sources/jq/jq.js"></script>
</head>
<body>
<p class="c1">jQuery is good</p>
<p class="c1">jQuery is good</p>
<span>test1</span>
<span>test1</span>
<p class="c1">jQuery is good</p>
<script>
    $('body p').css('border','1px solid');
    $('body>p').css('border','1px solid');
    $('p+span').css('border','1px solid');
    $('p~span').css('border','1px solid');
</script>
</body>
</html>

``` 

练习: 使用css选择器来完成上面的代码

## 高级的选择器

#### 概述:

类似于css中的高级选择器,jquery也有选择第一个元素,选择下最后一个元素等,但是他扩展了更多的选择器给我们使用,比css原生的有更多的扩展

#### 伪类选择器

1. ```(':first')``` 匹配第一个元素

2. ```(':last')``` 匹配第一个元素

3. ```(':eq(index)')``` 等于某几个元素的索引

4. ```(':gt(index)')``` 大于某个元素的索引

5. ```(':lt(index)')``` 小于于某个元素的索引

6. ```(':last')``` 匹配第一个元素

7. ```(':even')``` 选择偶数元素

8. ```(':odd')``` 选择奇数元素

9. ```(':header')``` 匹配h(x）的元素

...

#### 内容选择器

1. ```$(":contains(text)")``` 包含指定文本的元素

2. ``` $(":parent") ```  包含子元素或者文本的标签

3. ``` $(":empty") ```  不包含子元素或者文本的标签
4. ``` $("has(selector)") ```  选择元素中至少包含指定的元素

```

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="../sources/jq/jq.js"></script>
</head>
<body>
<p class="c1">jQuery is good</p>
<p class="c1">jQuery is good</p>
<span>test1</span>
<span>test2</span>
<p class="c1">jQuery is good</p>
<section></section>
<section>i love js</section>
<ol>
    <li></li>
</ol>
<ol></ol>
<script>
    $("span:contains('test1')");
    $("section:parent");
    $("section:empty");
    $("ol:has('li')");
</script>
</body>

```
>使用console查看


#### 子元素选择器

|选择器|描述|
|---|---|
|```$(':first-child')```|第一个子元素|
|```$(':last-child')```|最后一个子元素|
|```$(':nth-child')```|选择第n个|

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="../sources/jq/jq.js"></script>
</head>
<body>
<p class="c1">jQuery is good</p>
<p class="c1">jQuery is good</p>
<div>
<span>test1</span>
<span>test2</span>
</div>
<p class="c1">jQuery is good</p>
<section></section>
<section>i love js</section>
<ol>
    <li></li>
</ol>
<ol></ol>
<script>

    $('span:nth-child(2)').css('border','1px solid red');
    $('p:first-child').css('border','1px solid red');


</script>
</body>
</html>
```

#### 表单元素选择器

jQuery内置了很多方法帮助我们去操控表单,我们可以以很简单的方式获取到表单的元素


|选择器|描述|
|---|---|
|```$(":input")```|选择所有的input框|
|```$(":text")```|选择所有的文本框|
|```$(":password")```|选择所有的密码框|
|```$(":radio")```|选择所有的单选框|
|```$(":checkbox")```|选择所有的复选框框|
|```$(":submit")```|选择所有的提交框|
|```$(":image")```|选择所有的图片区域|
|```$(":reset")```|选择所有的重置按钮|
|```$(":button")```|选择所有的提交按钮|
|```$(":file")```|选择所有的文本提交框|
|```$(":checked")```|被选取的input元素|





