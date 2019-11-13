# css选择器的权重

## 概述

如果我们在使用css选择器的时候,有两个选择器同时选中了一个标签修改样式,那么css会决定使用哪一个选择器定义的样式呢？

这就涉及到了我们的选择器权重计算,css会以最高的权重来作为样式的展现

例子:

>下面两个选择器都选中了 id为html1的标签 那么css会采用哪个值作为展示呢?
  
   ```

        #ol1 > #html1 {
            color: #73d44d;
            background-color: #68aed4;
        }

        #html1 {
            color: #73d44d;
            background-color: #93c1d4;
        }

    
   ```


## 权重计算值

#### 概述

其实css会计算权重(相加),每种选择器都有不同的权重值,相加得到的权重值,就会比较出哪个大的采用哪个

#### 1. 行内的权重值

1000

```
<a style="xxx">
```

#### 2. id选择器的权重值

100

```
#test{
...
}
```

#### 3.class和伪类(其实都是类)

10

```

.test{
...
}

```

#### 标签选择器

1

```
a{
...
}
```

#### !important 最高权重

10000

>使用 !important可以最大化权重,使他比行内还要高,但是important只能定义其中的一个样式,并且在写在样式里面
```
       #html1 {
            color: #73d44d !important;
            background-color: #93c1d4;
        }
```

## 计算结果

   ```

        #ol1 > #html1 {
            color: #73d44d;
            background-color: #68aed4;
        }
        
        上面的权重值为 200

        #html1 {
            color: #73d44d;
            background-color: #93c1d4;
        }
        
        上面的权重值为 100
        
        #html1 > a {
            color: #73d44d;
            background-color: #93c1d4;
        }
        
        上面的权重值为 101

    
   ```

## 注意事项

1. 每种权重值的最大值只能叠加9次

	>不管有多少id权重器在里面 最大的权重就是 900

   ```

        #ol1 > #html1 > #html1> #html1> #html1> #html1> #html1> #html1> #html1> #html1{
            color: #73d44d;
            background-color: #68aed4;
        }
        
        上面的权重值为 900


    
   ```
   
   所以说最大的权重值是 999 所以在外面定义的权重值比不过行内就是这个原因
   
2. 如果两个地方定义的权重一样的话,那么就按照最后定义的权重为准,这个原则使用于 ```<style>```和 ```<link>```混合来使用



扩展阅读 https://blog.csdn.net/jane617_min/article/details/48370507