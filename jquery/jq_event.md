# js事件

## 鼠标事件


#### 1. 概述


#### 2. 使用方式

##### 1. click 被鼠标点击

```
<!DOCTYPE html>
<html>

<head>
    <meta http-equiv="Content-type" content="text/html; charset=utf-8" />
    <title></title>
    <script src="../../sources/jq/jq.js"></script>
    <style>
        div {
            background: #bbffaa;
            width: 300px;
        }
    </style>
</head>

<body>
<h2>通过empty移除元素</h2>
<div id="test">
    <p>p元素1</p>
    <p>p元素2</p>
    <ul>

        <li>
            sdfa
        </li>
        <li>
            dsaf
        </li>
        <li id="li1">
            dsaf
        </li>
        <li>
            dsaf
        </li>
        <li>
            dsaf
        </li>
        <li>
            dsaf
        </li>
    </ul>
</div>
<button>点击通过jQuery的empty移除元素</button>
<script type="text/javascript">
    $("button").on('click', function() {
        //通过empty移除了当前div元素下的所有p元素
        //但是本身id=test的div元素没有被删除
        $("#li1").siblings().css('border','1px solid')
    })
</script>
</body>

</html>

```
##### 2. mouseover与mouseout事件  鼠标移动和移出事件 可以实现hover的效果

```

<!DOCTYPE html>
<html>

<head>
    <meta http-equiv="Content-type" content="text/html; charset=utf-8" />
    <title></title>
    <script src="../../sources/jq/jq.js"></script>
    <style>
        div {
            background: #bbffaa;
            width: 300px;
        }
    </style>
</head>

<body>
<h2>通过empty移除元素</h2>
<div id="test">
    <p>p元素1</p>
    <p>p元素2</p>
    <ul>

        <li>
            sdfa
        </li>
        <li>
            dsaf
        </li>
        <li id="li1">
            dsaf
        </li>
        <li>
            dsaf
        </li>
        <li>
            dsaf
        </li>
        <li>
            dsaf
        </li>
    </ul>
</div>
<button>点击通过jQuery的empty移除元素</button>
<script type="text/javascript">
    $("button").mouseover(function() {
        //通过empty移除了当前div元素下的所有p元素
        //但是本身id=test的div元素没有被删除
        $("#li1").siblings().css('border','1px solid')
    })

    $("button").mouseout(function() {
        //通过empty移除了当前div元素下的所有p元素
        //但是本身id=test的div元素没有被删除
        $("#li1").siblings().css('border','')
    })
</script>
</body>

</html>

```

##### 3.hover

说明: 使用hover 就可以不用写两个函数

```

    $("button").hover(function() {
        //通过empty移除了当前div元素下的所有p元素
        //但是本身id=test的div元素没有被删除
        $("#li1").siblings().css('border','1px solid')
    },function() {
        //通过empty移除了当前div元素下的所有p元素
        //但是本身id=test的div元素没有被删除
        $("#li1").siblings().css('border','')
    })
```
##### 4. 焦点 focusin focusout

说明:和css中的一样 当获取到焦点的时候jquery也可以捕捉到这个时间(input框)

使用示例:

```

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <script src="../../sources/jq/jq.js"></script>
    <title>Title</title>
</head>
<body>
<h2>.focusin()方法</h2>
<div class="left">
    <div class="aaron">
        点击聚焦：<input type="text" />
    </div>
</div>
<div class="right">
    <div class="aaron1">
        点击聚焦并传递参数：<input type="text" id="input1" />
    </div>
</div>

<script>
    $(":input").focusin(function() {
        $(this).css('border','2px solid red');
        $(this).attr('value','test');
    });
    $(":input").focusout(function() {
        $(this).css('border','1px solid')
    })

</script>
</body>
</html>
```