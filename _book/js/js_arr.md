# js数组
## 概述

所谓集合，就是存储数据的容器。我们可以把教室理解为一个集合，而学生作为存储在集合里面的数据，叫做元素。

JavaScript集合类型主要使用数组，数组为一个特殊对象。ES6新增了Set数据结构，也用于表示一个集合。下面将主要介绍数组相关的知识点。

数组是有序排列的一组值的集合，这些值被包含在一对方括号内，里面的这些值称作数组元素。每个数组内的值都会有一个键名，这些键名其实就是一个从0开始依次计 数的下标，每个数组都会有一个“**length**”属性，表示数组元素的个数，所以数组内元素最大的下标值为**“length - 1”**。

数组内的值可以是JavaScript允许的任何类型的值，甚至可以是数组自身，像这样数组内包含另外一个数组的数组被称作二维数组任然继续包含数组，这样的数组就会形成“多维数组”。数组的基本表现形式如下：

```javascript
var arr1 = [1, 2, 3],               // 数组元素为数值
    arr2 = ["1", "2", "3"],         // 数组元素为字符串
    arr3 = [true, false],           // 数组元素为布尔值
    arr4 = [function(){}],          // 数组元素为函数
    arr5 = [{name:"Henrry Lee"}],   // 数组元素为对象
    arr6 = [[1, 2], [3, 4], 5];     // 数组元素为数组
```

> 提示：数组虽然有很多独立的特性，但它的数据类型仍然为对象型（object）。

## 创建数组

```javascript
// 1、字面量方法(优先使用)
var arr1 = [1, 2, 3];
// 2、对象构造方法
var arr2 = new Array(1, 2, 3);

// 3、数组也可以先声明后赋值
var arr3 = [];
arr3[0] = "Petter";
arr3[1] = "Tom";
arr3[3] = "Lily"
// ["Petter", "Tom", undefined x 1, "Lily"]

var arr4 = new Array();
arr4[0] = "Petter";
arr4[1] = "Tom";
arr4[3] = "Lily"
// ["Petter", "Tom", undefined x 1, "Lily"]
```

## 访问/修改数组元素

  访问数组元素通过**下标**访问，下标从**‘0’**开始，最后一个元素的下标为**length-1**，如果超出下标返回获取到的值为**undefined**。其语法形式为：`arr[idx]`。获取到数组元素之后即可修改数组元素。

```javascript
var arr = ['HTML', 'CSS', 'JavaScript'];

// 1、访问数组元素
console.log(arr[0]); // "HTML"
console.log(arr[1]); // "CSS"
console.log(arr[2]); // "JavaScript"

console.log(arr[3]); // undefined

// 2、修改数组元素
arr[2] = 'jQuery';
console.log(arr[2]); // "jQuery"
```

  你可以通过**Object**的 `keys()` 方法去获取一个数组的“键名”，即元素下标：

```javascript
var arr = ["HTML", "CSS", "JavaScript"]

console.log(Object.keys(arr)); // ["0", "1", "2"]
```

  你也可以通过如下方式去获取数组元素：

```javascript
var arr = ["HTML", "CSS", "JavaScript"]

arr["0"]; // "HTML"
arr["1"]; // "CSS"
arr["2"]; // "JavaScript"
```

  需要注意的是，数组虽然也是对象，但实际上下面这些获取数组元素的方法都是不合法的。

```javascript
console.log(arr.0);    // Uncaught SyntaxError: Unexpected number
console.log(arr."0");  // Uncaught SyntaxError: Invalid or unexpected token
console.log(arr.[0]);  // Uncaught SyntaxError: Invalid or unexpected token
console.log(arr.["0"]);// Uncaught SyntaxError: Invalid or unexpected token
```

# # 数组空位

  检查某个键名是否存在使用运算符 `in`，适用于对象，也适用于数组。该运算符用于检测数组元素的某个位置是否存在元素，返回的是一个布尔值。当通过下标访问的这个位置的值为undefined或该位置不存在，那么它返回的值就为false，否则就为true。

```javascript
var arr = ["HTML", ,"CSS", ,"JavaScript"];

0 in arr; // true
1 in arr; // false
2 in arr; // true
8 in arr; // false

arr[0]; // "HTML"
arr[1]; // undefined
arr[2]; // "CSS"
arr[8]; // undefined
```

  需要在这里进行补充说明的是，上例中下标为1和3的地方没有值，称作“**空位**（hole）”，它返回的值为undefined，但仍然会被计入数组的长度属性“length”中。而length的值是由数组中最后一个元素的下标+1决定的，我们来看一个示例：

```javascript
var arr = [1, , 2, 3, 4];
arr.length; // 5

arr[100] = 5;
arr.length; // 101
```

 针对这样的情况，需要进行一个额外的说明，就是“for-in循环遍历”和“Object.keys()”方法运行的原理都类似于一个单进程的指针，所以数组中的空位（即值为undefined的数组元素）都会被跳过，但通过“length”属性去进行“for循环”的时候，这些空位都不会被跳过。

# # 数组方法

## 4.1、数组判断

判断某个对象是否是一个数组使用 `Array.isArray()` 方法，如果是，则返回**true**，否则返回**false**。

```javascript
Array.isArray([]); // true
Array.isArray(''); // false
Array.isArray({}); // false
Array.isArray(function(){}); // false
```

## 4.2、添加数组元素

添加数组元素的方法比较多，主要有以下种：

- `push()`：在数组的末端添加一个或多个元素，并返回添加新元素后的数组长度*（ 改变原数组）*。
- `unshift()`：在数组的开始位置添加一个或多个元素，并返回添加新元素后的数组长度*（ 改变原数组）*。
- `apply()`：合并数组（只能合并两个）*（ 改变原数组）*
- `concat()`：合并数组（允许合并多个数组） *（ 不改变原数组）*
- `arr[idx]`：下标法添加数组元素

```javascript
// 1、首尾添加数组元素
var arr = [];
arr.push(1); // [1]
arr.unshift(0); // [0, 1]

// 2、下标法添加数组元素(高效，建议使用)
var arr = [1];
arr[arr.length] = 2; // [1, 2]
arr[0] = 0;  // [0, 1, 2]

// 3、合并数组
var arr1 = [1, 2],
    arr2 = [3, 4];
var aLeng = Array.prototype.push.apply(arr1, arr2);
// aLeng = 4, arr1 = [1, 2, 3, 4]

// 4、合并数组
var arr1 = [1, 2],
    arr2 = [3, 4],
    newArr = [].concat(arr1, arr2);
console.log(newArr); // [1, 2, 3, 4]
```

## 4.3、删除数组元素

删除数组元素的方法如下：

- `pop()`：删除数组最后一个元素*（ 改变原数组）*。
- `shift()`：删除数组第一个元素*（ 改变原数组）*。
- `splice()`：范围删除*（ 改变原数组）*。

```javascript
var arr = [1, 2, 3, 4];
arr.pop();   // [1, 2, 3]
arr.shift(); // [2, 3]
```

> 提示：以上两种方法在删除数组元素时只能一个一个删除。

删除数组元素中 *splice* 方法最为灵活，不仅可以范围删除数组元素，还可以实现数组元素的插入和替换。该方法语法形式为：

```
splice(location, count, items...)
```

该方法中的第一个参数是删除的起始位置，第二个参数是被删除的元素个数。如果后面还有更多的参数，则表示这些就是要被插入数组的新元素。

```javascript
var arr = [1, 2, 3, 4, 5];
arr.splice(1, 2); // 删除元素：2，3
console.log(arr); // [1, 4, 5]

arr.splice(1, 1, 'HTML', 'JavaScript'); // 删除元素：4，并追加'HTML', 'JavaScript'
console.log(arr); // [1, "HTML", "JavaScript", 5]
```

另外，该方法的第一个参数可以为负数（但是第二个不能，因为它表示长度），表示从数组末端开始计数，开始计数的值为“**-1**”。

```javascript
var arr = [1, 2, 3, 4, 5];

arr.splice(-3, 2); // 删除元素：3，4
console.log(arr);  // [1, 2, 5] 
```

利用该方法的原理可以达到向指定位置插入数组元素的效果。第一个参数仍然是表示开始下标，第二个参数设为0，这样后续设置的参数就会出现在第一个参数下标位置之前：

```javascript
var arr = [1, 3, 4];
arr.splice(1, 0, 2);
console.log(arr); // [1, 2, 3, 4]
```

和以往的数组操作一样，该方法同样可以省略第二个参数，这样一来删除的数组就会从给定的参数位置开始一直删除到末尾。通过获取该方法返回的值和原数组，可以实现分割数组的目的。

```javascript
var arr = [1, 2, 3, 4, 5, 6];
newArr = arr.splice(3);

console.log(arr);   // [1, 2, 3]
console.log(newArr);// [4, 5, 6]
```

## 4.4、截取数组元素

截取数组元素与字符串截取类似，使用 *slice* 方法，该方法语法形式如下：

```javascript
arr.slice(startIdx, endIdx);
```

它的第一个参数为起始位置（从下标0开始），第二个参数为终止位置（不包括该位置）。如果省略第二个参数，则一直返回到原数组的最后一个成员。

```javascript
var arr = [1, 2, 3, 4, 5, 6];
arr.slice(0, 3);  // [1, 2, 3]
arr.slice(3, -1); // [4, 5]
arr.slice(3); // [4, 5, 6]
arr.slice(3, 1); // []
```

除此之外，该方法还可以利用原型链中的 `call()` 方法将一个类似数组转化成真正的数组，其语法形式为：

```javascript
Array.prototype.slice.call(obj);
```

将一个类似数组转换为真正的数组的意义在于，类似数组不具有数组的方法，直接对一个类似数组使用数组的方法浏览器会报错，而很多时候我们的操作只有通过使用数组的方法才能完成，或用数组的方法完成才是最佳的选择。

## 4.5、数组排序

`sort()`  方法对数组成员进行升序排序，默认是按照**ASC II**码顺序排序，在ASC II码中，大写字母靠前。排序后，原数组将被改变。需要注意的是，该方法对数组元素的排序的初始依据是数组元素中的第一个字符，当第一个字符一样时，会对数组元素中的第二个字符进行比较，以此类推。也就是说当对一个数组如 `[90,100,130,300]` 进行排序，得到的结果会是 `[100,130,300,90]`，而并不是字面上数字大小的关系。若要对这样对数组实现数值大小的排序（实际项目中更多地是需要这样的结果），可以通过给sort()方法配置一个函数参数来实现，函数中需要配置两个参数，使该方法能实现一个差值排序的算法。用一个参数减去第二个参数，得到的是一个升序数组；用第二个参数减去第一个参数，得到的是一个降序的数组。如例：

```javascript
var nums = [1, 8, 13, 30]; 

// 1、升序
var ascending = nums.sort(function(a1, a2) {
	return a1 - a2;
});
console.log(ascending); // [1, 8, 13, 30]


// 2、降序
var descending = nums.sort(function(a1, a2) {
	return a2 - a1;
})
console.log(descending); // [30, 13, 8, 1]
```

通过示例可以发现，得出的排序结果已经不再是按照ASC II中首字符的前后顺序来排序了，而是按照数学中数字的大小来进行的排序。而且当sort()方法内的函数的两个参数在执行差值运算的位置发生变化后，得出结果的排序升降关系也不一样。但若要实现一个稍微复杂一点的排序，如对数组元素是对象的数组进行排序，这个方法能否办到呢，我们先来做这样一个尝试，让数组元素对象按照学生成绩进行排序。

```javascript
var stus = [
    {stuNum: 1101, name: '张三', score: 95},
    {stuNum: 1102, name: '李四', score: 50},
    {stuNum: 1103, name: '王五', score: 65},
    {stuNum: 1104, name: '赵二', score: 70}
];

stus.sort();
stus.forEach(val => console.log(val));
// Object {stuNum: 1101, name: "张三", score: 95}
// Object {stuNum: 1102, name: "李四", score: 50}
// Object {stuNum: 1103, name: "王五", score: 65}
// Object {stuNum: 1104, name: "赵二", score: 70}
```

通过访问遍历数组元素可以发现，数组内这四个对象的位置完全没有发生改变。其实要实现这个需求也是有办法的，就是同样需要给“sort()”方法配置一个函数作为参数来实现，实现思路和对数组排序时配置函数一致。

```javascript
var stus = [
    {stuNum: 1101, name: '张三', score: 95},
    {stuNum: 1102, name: '李四', score: 50},
    {stuNum: 1103, name: '王五', score: 65},
    {stuNum: 1104, name: '赵二', score: 70}
];

stus.sort((obj1, obj2) => obj1.score - obj2.score);
stus.forEach(stu => {
	console.log(`姓名：${stu.name} 成绩：${stu.score}`);
});
// 姓名：李四 成绩：50
// 姓名：王五 成绩：65
// 姓名：赵二 成绩：70
// 姓名：张三 成绩：95
```

  该方法通过和下面会讲到的“reverse()”方法配合，可以实现一个简单的升序、降序排列的功能。

## 4.6、数组元素倒序

`reverse()`  方法的作用是将已有数组倒序排列，并返回改变后的数组。该方法同样会改变原数组。

```javascript
var nums = [1, 2, 3, 4]
nums.reverse();
console.log(nums); // [4, 3, 2, 1]
```

  需要注意的是该方法不具备**sort()**方法那样对数组排序的能力，它只是单纯地将当前的数组的元素进行先后顺序地调转而已。所以，在对一个有序（已经完成升序或降序排序）的数组进行反向排序的时候，会比**sort()**方法通过配置函数的参数，再对函数的参数进行位置调整来计算差值这种方式的性能要高很多。

## 4.7、操作数组元素

 **map**方法对数组的所有成员依次调用一个函数，根据函数结果返回一个新数组。该方法不会改变原来的数组。

```javascript
let nums = [1, 2, 3, 4];

/*
var newArr = nums.map(function(num){
	return num * 2;
});
*/

// es6 箭头函数表示
var newArr = nums.map(num => num * 2);
console.log(newArr); // [2, 4, 6, 8]
```

  上例中，**map**方法内有一个箭头函数，函数内有一个参数“**num**”，这个参数的名称是自定义的（只要不是关键字和保留字），这个参数在函数运行的时候通过一次内部的遍历指向数组内对应的元素。

  **map**方法内的函数，最多可以接受3个参数。：第1个，就是上面例子中出现的参数，它表示数组内每个元素的本身；第2个，表示数组内元素的下标位置；第3个，表示数组本身，即：`function(item, idx, arr){...}`，箭头函数表示法为：`（item, idx, arr） => {...}`

```javascript
var nums = [1, 2, 3];
nums.map((num, idx, arr) => {
	console.log(`idx = ${idx}, num = ${num}, arr = ${arr}`);
});

// idx = 0, num = 1, arr = 1,2,3
// idx = 1, num = 2, arr = 1,2,3
// idx = 2, num = 3, arr = 1,2,3
```

  该方法和**“for-in遍历循环”**语句有一个相似之处，即当数组元素中存在空位的时候，该函数是不会去执行的，但只要有明文的值，哪怕是遇到undefined、null、NaN等特殊的“无值”的值，该方法仍然能够执行。我们来看这样一个例子就明白了。

```javascript
var arr = [1, , "", undefined, null, , 'China'];
console.log(arr.length);

let count = 0; // 7
arr.forEach((val) => {
	count++;
});
console.log(count); // 5
```

## 4.8、数组遍历

- `for` 循环遍历数组元素
- `for-in` 循环遍历数组元素
- `forEach()` 方法遍历数组元素

```javascript
var arr = ["HTML", "CSS", "JavaScript"]

// 1、for 循环遍历
for(let idx = 0; idx < arr.length; idx++) {
  console.log(arr[idx]);
}

// 2、for-in 遍历
for (let idx in arr) {
  console.log(arr[idx]);
}

// 3、forEach() 遍历
arr.forEach(function (item, curIdx, arr) {
    console.log(item);
});

// HTML
// CSS
// JavaScript
```

**forEach**方法与**map**方法很相似，也是遍历数组的所有成员元素，执行某种操作，但是**forEach**方法一般不返回值，只用来操作数据。如果需要有返回值，一般使用**map**方法。**forEach**方法的参数与**map**方法一致，也是一个函数，数组的所有元素会依次执行该函数。它接受三个参数，分别是当前位置的值、当前位置的下标和整个数组。

```javascript
var lang = ["HTML", "CSS", "JavaScript"];

lang.forEach((val, idx, arr) => {
	console.log(`idx = ${idx}, val = ${val}`);
    return `${val}.`;
});

// idx = 0, val = HTML
// idx = 1, val = CSS
// idx = 2, val = JavaScript
```

  上例中函数内的“`console.log()`”方法得到执行，但关键字“**return**”后续的内容却没有生效，说明**forEach2**方法是不会执行返回值操作的。另外，该方法可以有第二个参数（并不是值函数内部的参数，而是指forEach()方法本身的参数），第二个参数用于“告诉”函数内部的“this”关键字的指向。

```javascript
var person = {
	name: 'Henrry Lee',
	profession: 'Lecturer',
	skill: ['iOS', 'web', 'sqlite'],
	print: function() {
		this.skill.forEach(() => console.log(this.profession), this);
	}
}
person.print();
// Lecturer
// Lecturer
// Lecturer
```

  同样地，由于**forEach**方法和**map**方法相比，不会去执行返回值的表达式的计算，实际使用起来性能会更加的优秀。所以，现在很多在重视性能的类库在封装类似的方法的时候，更多地是采用forEach()方法，而不是功能与之相近的map()方法。

## 4.9、过滤数组元素

从方法名来看该方法的主要作用是过滤，它的参数是一个函数，所有数组成员依次执行该函数，返回结果为true的成员组成一个新数组返回。该方法不会改变原数组。

```javascript
// 示例1：过滤偶数
var arr = [1, 2, 3, 4, 5, 6],
    filArr = arr.filter(function (num) {
        return num % 2 == 0;
    });
console.log(filArr); // [2, 4, 6]
```

 和之前的**map**和**forEach**方法一样，该方法的函数仍旧支持3个参数，参数位和之前的这两个方法也是一样的，分别表示：数组元素、元素下标和原数组。

## 4.10、查询数组元素

- `indexOf()`  方法返回给定元素在数组中第一次出现的位置，如果没有出现则返回**-1**。
- `lastIndexOf()`  方法返回给定元素在数组中最后一次出现的位置，如果没有出现则返回-1。

```javascript
var arr = [1, 2, 3, 2, 5];
arr.indexOf(2);     // 1
arr.lastIndexOf(2); // 3
```

> 提示：该方法允许设置第2个参数指定开始查询的位置。

## 4.11、数组元素累加

```javascript
array.reduce(callbackfn[, initialValue])
```

对数组中的所有元素调用指定的回调函数。该回调函数的返回值为累积结果，并且此返回值在下一次调用该回调函数时作为参数提供。

| 参数             | 定义                                       |
| -------------- | ---------------------------------------- |
| *array*        | 必需。一个数组对象。                               |
| *callbackfn*   | 必需。一个接受最多四个参数的函数。对于数组中的每个元素，**reduce** 方法都会调用 *callbackfn* 函数一次。 |
| *initialValue* | 可选。如果指定 *initialValue*，则它将用作初始值来启动累积。第一次调用 *callbackfn* 函数会将此值作为参数而非数组值提供。 |

当满足下列任一条件时，将引发 **TypeError** 异常：

- *callbackfn* 参数不是函数对象。
- 数组不包含元素，且未提供 *initialValue*。

> 提示：
>
> 1、如果提供了 *initialValue*，则 **reduce** 方法会对数组中的每个元素调用一次 *callbackfn* 函数（按升序索引顺序）。如果未提供 *initialValue*，则 **reduce** 方法会对从第二个元素开始的每个元素调用 *callbackfn* 函数。
>
> 2、回调函数的返回值在下一次调用回调函数时作为 *previousValue* 参数提供。最后一次调用回调函数获得的返回值为 **reduce** 方法的返回值。
>
> 3、不为数组中缺少的元素调用该回调函数。

回调函数的语法如下所示：

```
function callbackfn(previousValue, currentValue, currentIndex, array)
```

可使用最多四个参数来声明回调函数。

下表列出了回调函数参数。

| 回调参数            | 定义                                       |
| --------------- | ---------------------------------------- |
| *previousValue* | 通过上一次调用回调函数获得的值。如果向 **reduce** 方法提供 *initialValue*，则在首次调用函数时，*previousValue* 为 *initialValue*。 |
| *currentValue*  | 当前数组元素的值。                                |
| *currentIndex*  | 当前数组元素的数字索引。                             |
| *array1         | 包含该元素的数组对象。                              |

**第一次调用回调函数**

在第一次调用回调函数时，作为参数提供的值取决于 **reduce** 方法是否具有 *initialValue* 参数。

如果向 reduce 方法提供 *initialValue*：

- *previousValue* 参数为 *initialValue*。
- *currentValue* 参数是数组中的第一个元素的值。

如果未提供 *initialValue*：

- *previousValue* 参数是数组中的第一个元素的值。
- *currentValue* 参数是数组中的第二个元素的值。

# # 链式使用

  在数组的方法中，除了可以实现数组操作方法的嵌套，若所用方法返回的仍旧是一个数组的话，还可以使用方法链来完成一个特定的功能。

```javascript
var arr = [1, 2, 3, 5, 4];
var res = arr.sort().reverse().map(function(item){
    return item * 2;
});
console.log(res);// [ 10, 8, 6, 4, 2 ]
```

# # 拓展

## 6.1、数组去重

```javascript
Array.prototype.removeDuplicate = function () {
    var json = {};
    var arr  = [];
    for(var i = 0, len = this.length; i < len; i++) {
        if(!json[this[i]]) {
            json[this[i]] = true;
            arr.push(this[i]);
        }
    }
    return arr;
}
var result = [1, 2, 3, 3, 4, 5].removeDuplicate();
console.log(result); // [1, 2, 3, 4, 5]
```



