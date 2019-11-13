# js dom操作


## 获取元素

#### 1.通过属性值 name来获取  document.getElementsByName(name)

1. 说明:
	通过元素的 name 属性查询元素,比如所有name=password的标签
	
2. 注意:
    
    因为文档中的 name 属性可能不唯一，所有 getElementsByName() 方法返回的是元素的数组，而不是一个元素
    
    和数组类似也有length属性，可以和访问数组一样的方法来访问，从0开始。

3. 使用方式

	```
	<!DOCTYPE HTML>
	<html>
	<head>
	    <script type="text/javascript">
	
	            let mynode=document.getElementsByName('myt');
	            document.write(mynode.length)
	
	    </script>
	</head>
	<body>
	<input name="myt" type="text" value="1">
	<input name="myt" type="text" value="2">
	<input name="myt" type="text" value="3">
	<input name="myt" type="text" value="4">
	<input name="myt" type="text" value="5">
	<input name="myt" type="text" value="6">
	
	<br>
	</body>
	</html>
	```
	
#### 2. 获取标签的名称来获取 getElementsByTagName()

1. 说明 通过标签名称来获取节点

2. 使用方式

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script>

    </script>
</head>
<body>
<ol>
    <li>test</li>
    <li>test</li>
    <li>test</li>
</ol>

</body>
</html>

```

consle

```
document.getElementsByTagName('li')
```

#### 3. 通过标签中的id来获取 getElementByID


1. 说明 通过id来获取元素节点
2. 注意 只能获取到一个不是数组

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script>

    </script>
</head>
<body>
<ol>
    <li id="test">test</li>
    <li>test</li>
    <li>test</li>
</ol>

</body>
</html>

```

## 元素的属性操作

#### 1. 通过属性名称来获取 getAttribute()

1. 说明: 上面的方式是获取元素,那么我们获取到元素之后,还想获取到元素中属性的值 比如```input```中的 ``` value```属性

2. 区别:
    上面的方法是用来获取元素的,这个方法是使用获取到的元素来获取元素中的属性
    
	```
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Title</title>
	
	</head>
	<body>
	<input value="rimi" id="input1">
	<script>
	    var input1 = document.getElementById('input1');
	    var values = input1.getAttribute('value');
	    document.write(values);
	</script>
	</body>
	</html>
	```
	
#### 2. 设置元素的的属性值 elementNode.setAttribute(name,value)

1. 说明
 
	1. name: 要设置的属性名。
   2. value: 要设置的属性值。


2. 用法

	```
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Title</title>
	
	</head>
	<body>
	<input value="rimi" id="input1">
	<script>
	    var input1 = document.getElementById('input1');
	    input1.setAttribute('value','rimi123');
	</script>
	</body>
	</html>
	
	```
	
## 节点操作(查询)

#### 当我们找到了一个节点之后,就能像css那样 去通过本节点找到或者操作更多的节点的,学习方式:想着css的选择器来学习

#### 1. 访问子节点childNodes

	```
	
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Title</title>
	
	</head>
	<body>
	<ol>
	    <li>
	        test1
	    </li>
	    <li>
	        test2
	    </li>
	    <li>
	        test3
	    </li>
	</ol>
	<script>
	    let o1 = document.getElementsByTagName('ol')[0];
	    let o1_childs= o1.childNodes;
	</script>
	</body>
	</html>
	
	```
	
#### 2. 访问子节点的第一和最后项

1. firstElementChild
2. lastElementChild

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

</head>
<body>
<ol>
    <li>
        test1
    </li>
    <li>
        test2
    </li>
    <li>
        test3
    </li>
</ol>
<script>
    let o1 = document.getElementsByTagName('ol')[0];
    console.log(o1. firstElementChild);
    console.log(o1. firstElementChild);
</script>
</body>
</html>

```

#### 3. 获取父节点 parentNode

1. 说明: 获取这个节点之上的父级节点

2. 用法

```

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>

</head>
<body>
<ol>
    <li>
        test1
    </li>
    <li>
        test2
    </li>
    <li>
        test3
    </li>
</ol>
<script>
    let o1 = document.getElementsByTagName('ol')[0];
    o1.parentNode
</script>
</body>
</html>

```

#### 访问兄弟节点

1. 说明:就像css一样 访问兄弟节点

2. 具体用法

	```
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Title</title>
	
	</head>
	<body>
	<ol>
	    <li>
	        test1
	    </li>
	    <li>
	        test2
	    </li>
	    <li>
	        test3
	    </li>
	</ol>
	<script>
	    let o1 = document.getElementsByTagName('ol')[0];
	    let li1 = o1.childNodes[1]
	
	</script>
	</body>
	</html>
	```

	1. 访问下一个节点nextSibling
	      nextElementSibling
	
		```
		
		li1.nextSibling
		
		```
	
	2. 访问上一个节点previousSibling
previousElementSibling
	
		```
		li1.previousSibling
		```

## 节点的增删改

#### 插入节点appendChild()

1. 说明: 我们可以在节点中添加值

2. 具体用法:

	```
	    let o1 = document.getElementsByTagName('ol')[0];
	    //创建一个节点
	    let li1 = document.createElement('li');
	    //在一个节点里面写入值 就像手写<li>我是后面添加的li元素</li>
	    li1.innerHTML = '我是后面添加的li元素';
	    o1.appendChild(li1);
	    
	```
3. 代码说明:

	我们插入节点的前提是首先要创建一个节点对象,然后再把对象添加进去
	
#### 在某个节点之间添加节点 insertBefore() 

1. 说明：上面的代码中,我们添加的节点是在最后添加节点,但是我们可以选择在某个节点之前去添加

2. 代码:

	```
	
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Title</title>
	
	</head>
	<body>
	<ol>
	    <li>
	        test1
	    </li>
	    <li>
	        test2
	    </li>
	    <li id="test3">
	        test3
	    </li>
	</ol>
	<script>
	    let o1 = document.getElementsByTagName('ol')[0];
	    //创建一个节点
	    let li1 = document.createElement('li');
	    //在一个节点里面写入值 就像手写<li>我是后面添加的li元素</li>
	    li1.innerHTML = '我是后面添加的li元素';
	
	    let li_test3 = document.getElementById('test3');
	    o1.insertBefore(li1,li_test3)
	
	
	</script>
	</body>
	</html>
	
	```
	
3. 代码说明:

 insertBefore(li1,li_test3) 第一个是要添加的新节点,第二个是在xxx节点之前去添加这个新节点
 

#### 删除节点removeChild()

1. 说明:
    可以使用这个方法去删除节点
    
    
2. 代码：

	```
	
	    let o1 = document.getElementsByTagName('ol')[0];
    let li_test3 = document.getElementById('test3');
    o1.removeChild(li_test3)
	```
	
3. 代码说明:

	和上面的一样,当你删除节点的时候,必须是一个节点对象才行
	
	
#### 其他方法

1. 替换节点 node.replaceChild (newnode,oldnew ) 

	```
		
		<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>Title</title>
	
	</head>
	<body>
	<ol>
	    <li>
	        test1
	    </li>
	    <li>
	        test2
	    </li>
	    <li id="test3">
	        test3
	    </li>
	</ol>
	<script>
	    let o1 = document.getElementsByTagName('ol')[0];
	    //创建一个节点
	    let li1 = document.createElement('li');
	    //在一个节点里面写入值 就像手写<li>我是后面添加的li元素</li>
	    li1.innerHTML = '我是替换的li元素';
	
	    let li_test3 = document.getElementById('test3');
	    li_test3.parentNode.replaceChild(li1,li_test3);
	
	
	</script>
	</body>
	</html>

	```
 









    
