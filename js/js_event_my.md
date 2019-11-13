# js的事件

## 概述

  事件是一种异步编程的实现方式，本质上是程序各个组成部分之间的通信。DOM支持大量的事件。

  事件是可以被 JavaScript 侦测到的行为。网页中的每个DOM元素都可以产生某些可以触发JavaScript函数的事件。简单的说，就是当用户对页面的元素进行操作的时候，页面发生的一些可见或不可见的变化。

  传统的页面交互是通过CSS实现的，不过CSS只能实现一些临时的、视觉上的简单交互。但随着互联网技术的发展，只停留在页面上的这些简单交互早已不能满足时代发展的要求了。这个时候JavaScript事件的出现很大程度地提升了界面的可交互性，这种交互不仅是停留在视觉上的，还可以是数据上的交互，可以临时的，通过和服务器端的配合也可以实现永久的页面样式和数据改变，从而更大程度地提升了用户体验。

  JavaScript的事件主要包括鼠标事件、键盘事件、表单事件、文档事件及这些事件提供的一系列处理机制，在HTML5规范确立的过程中又出现了触摸事件、拖拽事件、进度事件等一系列，本章的主要内容就是对这些事件进行介绍。

## 事件添加

  事件一定要添加在某个页面元素后才会生效，包括window对象和document对象。事件的添加主要有以下几种形式：

- 1）、直接将代码写在HTMl上，在页面标签元素的 “*on-*” 属性上添加

  ```html
  <button type="button" onclick="alert('Hello, world!')">确定</button>
  ```

  代码少的还勉强可以，代码多的话你就会觉得有点打脑壳了。可能你会想着封装一个函数来触发：

  ```html
  <form>
  	<input type="text" oninput="validate()">
  	<button type="button" onclick="formSubmit()">提交</button>
  </form>
  ```

  ```javascript
  function validate() {
      // 事件处理部分
      // ...
      alert("处理input事件！");
  }
  function formSubmit() {
      // 事件处理部分
      // ... 
      alert("处理click事件！");
  }
  ```

    这种做法简化了代码量，但违背结构层和行为层分离的原则，除非是用于测试，在实际开发环境中并不被推荐。

- 2）、通过DOM元素添加

  直接通过document对象下的Element对象进行事件绑定，如例：

```html
<form>
	<input type="text">
	<button type="submit">提交</button>
</form>
```

```javascript
document.getElementsByTagName('input')[0].oninput = function() {
    // 事件处理
    // ...
    alert("处理input事件！");
}
document.getElementsByTagName('button')[0].onclick = function() {
    // 事件处理
    // ...
    alert("处理click事件！");
}
```

  这种做法代码可读性不高，而且不利于DOM元素的重复读取和事件绑定的设置，也不被推荐。

- 3）、通过实例化过后的Element对象添加

```html
<input type="text" onchange="validate()">
<button type="submit" onclick="submit()">登录</button>
```

```javascript
var ipt = document.getElementsByTagName('input')[0];
var btn = document.getElementsByTagName('button')[0];

ipt.onchange = function() {
    // 事件处理
    // ...
    alert("处理input事件！");
}
btn.onclick = function() {
    // 事件处理
    // ...
    alert("处理click事件！");
}
```

  这种做法看似比前两种方式多了一些代码，但由于将Element实例化为了一个对象存储于内存内，每次的访问和事件的绑定设置都是从内存去读取，无需再对DOM进行查询，很大程度上提高了代码的运行效率。而且在需要单元素多事件绑定的情况下，这种写法反而可以让代码更加的精简，节省了很多次对DOM查询消耗的代码字节。所以，这种方式在实际项目中是被大量使用的，也是比较推荐的一种方式。

- 4）、对实例化过后的Element对象进行监听

  这种方式和上面一种方式的形式一样，同样是对实例化的Element对象进行事件绑定，但这种绑定的方式一般叫做添加 “监听函数”，需要使用 Element 的 `addEventListener()` 方法，而且事件名称不需要前缀 “`on`”。表示方法如下：

```html
<form>
	<input type="text">
	<button type="submit">登录</button>
</form>
```

```javascript
var ipt = document.getElementsByTagName('input')[0];
var btn = document.getElementsByTagName('button')[0];

ipt.addEventListener('input', function() {
    // 事件处理部分
    // ... 
    alert("处理input事件！");
}, false);
btn.addEventListener('click', function() {
    // 事件处理部分
    // ... 
    alert("处理click事件！");
}, false);
```

## 事件响应

#### 鼠标单击事件( onclick ）

onclick是鼠标单击事件，当在网页上单击鼠标时，就会发生该事件。同时onclick事件调用的程序块就会被执行，通常与按钮一起使用。

	```
	
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Title</title>
	</head>
	<body>
	
	
	<button onclick="add()">点击</button>
	<script>
	
	    function add(){
	        alert('test')
	    }
	</script>
	</body>
	</html>
	
	```

#### 鼠标经过事件（onmouseover）

鼠标经过事件，当鼠标移到一个对象上时，该对象就触发onmouseover事件，并执行onmouseover事件调用的程序。

相当于 hover

	```
	
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Title</title>
	</head>
	<body>
	
	
	<button onmouseover="add()">点击</button>
	<script>
	
	    function add(){
	        alert('test')
	    }
	</script>
	</body>
	</html>
	
	```
	
#### 鼠标移开事件（onmouseout）

1.说明: 同上 不过是鼠标移开才有这个事件

```

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>


<button onmouseout="add()">点击</button>
<script>

    function add(){
        alert('test')
    }
</script>
</body>
</html>

```

#### 光标聚（失）焦事件（onfocus onblur）

1. 说明:
    当在输入框有了光标之后,我们就可以认为有聚焦事件
    onblur事件与onfocus是相对事件，当光标离开当前获得聚焦对象的时候，触发onblur事件，同时执行被调用的程序。
    
	```
	
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Title</title>
	</head>
	<body>
	
	<input onfocus="add()">
	<button onmouseout="add()">点击</button>
	<script>
	
	    function add(){
	        alert('test')
	    }
	</script>
	</body>
	</html>
	
	```
	
#### 内容选中事件（onselect）

1. 选中事件，当文本框或者文本域中的文字被选中时，触发onselect事件，同时调用的程序就会被执行。
	
	```
	
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Title</title>
	</head>
	<body onload="msg1()">
	
	<script>
	
	    function add(){
	        alert('test')
	    }
	
	    function msg1() {
	        alert('加载中')
	    }
	</script>
	</body>
	</html>
	```
	
#### 加(卸)载事件（onload）

事件会在页面加载完成后，立即发生，同时执行被调用的程序。
注意：

1. 加载页面时，触发onload事件，事件写在<body>标签内

```

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body onload="msg1()">

<form>

    
</form>

<script>


    function msg1() {
        alert('加载中')
    }
</script>
</body>
</html>
```

2. onunload 当关闭浏览器发生的事情,不过要看浏览器的支持程度





