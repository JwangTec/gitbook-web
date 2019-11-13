# 递归算法

## 1+...+99+100

```
    function plus(n) {
        n = Number(n);
        if(n===1){
            return 1
        }else{
            return n + plus(n-1)
        }

    }
```



## 斐波那契数

```
    function fab(n) {
        n = Number(n);
        if(n === 1 || n === 2){
            return 1
        }else{
            return fab(n-1) + fab(n-2)
        }

    }
```



## 汉罗塔

```

    function hano(n,a,b,c) {
        if(n === 1){
            let res = "move--->" + a + "<---to--->" + c;
            document.write(res + '<br>')
        }else{
            hano(n-1,a,c,b);
            hano(1,a,b,c);
            hano(n-1,b,a,c);
        }
    }

    hano(5,'a','b','c')
    
```
