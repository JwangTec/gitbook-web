# jquery使用方式

#### 1.设置css样式

说明:不同于js设置样式和css设置样式的方式,jquery有自己设置样式的方式,它使用 .css()来设置css样式

使用示例:

>单个样式的设置方式

```
$('p:nth-child(2n-1)').css('border','1px solid red');
```

> 同时设置多个样式要使用类似dict的方式

```
$('p:nth-child(2n-1)').css({'border':'1px solid red','color':'red'});
```

#### 2. 待文档加载完成后调用函数

说明: 因为js代码一般要等文件加载完成后才能有完整的dom树,所以说jquery一样也有这样的方式去让文档加载完才去调用一个函数


>使用示例,告诉jquery在页面加载完成后再去执行

```

$(document).ready(function () { 
...
});
```

#### 3. 设置标签里面的值

说明: jquery含有可以去设置标签里面的值的功能,不过有多种,我们需要区分一下

 1. html()读取和修改一个元素的HTML内容
 2. text()读取和修改一个元素的文本内容
 3. val()读取和修改一个表单元素的value字段值(获取密码值等使用value来获取)

	 ```
	 $('p:nth-child(2)').text('<a>aa</a>');
	 text 会把标签一起作为文本输出
	
	 $('p:nth-child(2)').html('<a>aa</a>');
	 html会加入标签
	
	 $('p:nth-child(2n-1)').val('已修改');
	 只能修改元素中含有value里面的值,比如Input
	 
	 ```
 
#### 4.操作属性(prop)

说明: jquery可以像js一样去侦测属性并且操作属性值,但是只需要使用简单的prop方法即可

1. prop 获取属性或者设置属性

>设置checkbox的值为true(被选中)
```
$(":checkbox").prop("checked", true);
```
2. removeProp 删除某个属性

#### 5.操作属性(attr)

说明:每个元素都有一个或者多个特性，这些特性的用途就是给出相应元素或者其内容的附加信息。如：在img元素中，src就是元素的特性，用来标记图片的地址。

1. attr

    1. attr(传入属性名)：获取属性的值
    2. attr(属性名, 属性值)：设置属性的值
    3. attr(属性名,函数值)：设置属性的函数值
    4. attr(attributes)：给指定元素设置多个属性值，即：{属性名一: “属性值一” , 属性名二: “属性值二” , … … }
    
2. removeAttr
	删除属性
	
#### 6. attr 和 prop的区别

1. 通常在获取或者设置checked，selected，readonly，disabled等的时候使用prop效果更好，减少了访问dom属性节点的频率
2. 另外，用prop来设置属性名，html结构是不会发生变化的。而用attr来设置属性名，html结构是会发生变化的。

参考资料:https://www.cnblogs.com/jiajia123/p/6539326.html
 
 

 

