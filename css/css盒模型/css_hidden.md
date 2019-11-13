# css 可见性

## CSS Display(显示) 与 Visibility（可见性）

#### visibility:hidden

可以隐藏某个元素，但隐藏的元素仍需占用与未隐藏之前一样的空间。也就是说，该元素虽然被隐藏了，但仍然会影响布局。

#### display:none

可以隐藏某个元素，且隐藏的元素不会占用任何空间。也就是说，该元素不但被隐藏了，而且该元素原本占用的空间也会从页面布局中消失。


```

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        div{
            background-color: #8bd400;
        }

        #a2:hover{
            display:none;

        }

    </style>
</head>
<body>

<div id="a1">

    test1
</div>
<div id="a2">

    test2
</div>

<div id="a3">

    test2
</div>

</body>
</html>


```

