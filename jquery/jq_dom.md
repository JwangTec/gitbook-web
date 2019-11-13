# jquery dom操作

## 插入节点

#### 1. append，prepend()

说明append放在,在被选择的对象中去添加内容
prepend 在被选择的对象中去添加内容（添加在最前面）


```

<!DOCTYPE html>
<html>

<head>
    <meta http-equiv="Content-type" content="text/html; charset=utf-8" />
    <title></title>
    <script src="../../sources/jq/jq.js"></script>
    <style>
        .content {
            width: 300px;
        }
        .append{
            background-color: blue;
        }
    </style>
</head>
<body>
<h2>通过append添加元素</h2>
<button id="bt1">点击通过jQuery的append添加元素</button>
<div class="content"></div>
<script type="text/javascript">
    $("#bt1").on('click', function() {
        //.append(), 内容在方法的后面，
        //参数是将要插入的内容。
        $(".content").append('<div class="append">通过append方法添加的元素</div>')
    })
</script>
</body>
</html>

```

#### 2. before after

说明: 对比上面的操作,我们也可以使用 before 和after在标签前面或者后面添加内容

区别在于上面的方法是在 div中去添加内容 本方法是在div同级的上下去添加内容

```
<!DOCTYPE html>
<html>

<head>
    <meta http-equiv="Content-type" content="text/html; charset=utf-8" />
    <title></title>
    <script src="../../sources/jq/jq.js"></script>
    <style>
        .content {
            width: 300px;
        }
        .append{
            background-color: blue;
        }
    </style>
</head>
<body>
<h2>通过append添加元素</h2>
<button id="bt1">点击通过jQuery的append添加元素</button>
<div class="content"></div>
<script type="text/javascript">
    $("#bt1").on('click', function() {
        //.append(), 内容在方法的后面，
        //参数是将要插入的内容。
        $(".content").before('<div class="append">通过append方法添加的元素</div>')
    })
</script>
</body>
</html>


```

## 删除操作

#### 1. 删除节点 empty() remove

说明: 

1. empty的意思是清空节点,而不是删除节点,他会把节点里面的值全部给清空,但是节点本身还在
2. remove是把节点本身也删除掉

使用示例

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
</div>
<button>点击通过jQuery的empty移除元素</button>
<script type="text/javascript">
    $("button").on('click', function() {
        //通过empty移除了当前div元素下的所有p元素
        //但是本身id=test的div元素没有被删除
        $("#test").empty()
    })
</script>
</body>

</html>


```

## 遍历节点

#### 1. children()方法 find()方法

说明:

1. children  jQuery是一个合集对象，如果想快速查找合集里面的第一级子元素，此时可以用children()方法。这里需要注意：.children(selector) 方法是返回匹配元素集合中每个元素的所有子元素（仅儿子辈，这里可以理解为就是父亲-儿子的关系）
2. find 会把合集对象的后代都找出来,但是find必须给出一个符号来通配,如果选择所有给出 ```*```号

    ```
    $("#test").find('*').css('border','1px solid')
    ```
示例:

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
    </ul>
</div>
<button>点击通过jQuery的empty移除元素</button>
<script type="text/javascript">
    $("button").on('click', function() {
        //通过empty移除了当前div元素下的所有p元素
        //但是本身id=test的div元素没有被删除
        $("#test").children().css('border','1px solid')
    })
</script>
</body>

</html>

```

#### 2. parent parents方法

说明:

1. parent会查找元素的父级(只有一级)
2. parents会查找元素的父级(所有级)

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
    </ul>
</div>
<button>点击通过jQuery的empty移除元素</button>
<script type="text/javascript">
    $("button").on('click', function() {
        //通过empty移除了当前div元素下的所有p元素
        //但是本身id=test的div元素没有被删除
        $("li").parents().css('border','1px solid')
    })
</script>
</body>

</html>

```

#### next prev 

说明:

1. next匹配合集中每一个元素的下一个兄弟元素(只有一个)

2. prev匹配合集中每一个元素的上一个兄弟元素(只有一个)
3. siblings 所有相邻的元素都匹配出来

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
    </ul>
</div>
<button>点击通过jQuery的empty移除元素</button>
<script type="text/javascript">
    $("button").on('click', function() {
        //通过empty移除了当前div元素下的所有p元素
        //但是本身id=test的div元素没有被删除
        $("#li1").next().css('border','1px solid')
    })
</script>
</body>

</html>

```


