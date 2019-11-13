# js 对象
## 概述

对象（object）是JavaScript的核心概念，也是最重要的数据类型。JavaScript的所有数据都可以被视为对象。简单说，所谓对象，就是一种 **无序** 的数据集合，由若干个“ **键值对** ”（key-value，亦称属性名值对、成员等）构成。

JavaScript支持面 **向对象编程** ，虽然不同于传统的面向对象编程语言，但是JavaScript具有很强的面向对象编程能力。“面向对象编程”（Object Oriented Programming，缩写为OOP）是目前主流的编程范式。它的核心思想是将真实世界中各种复杂的关系，抽象为一个个对象，然后由对象之间的分工与合作，完成对真实世界的模拟。

传统的过程式编程（procedural programming）由一系列函数或一系列指令组成，而面向对象编程的程序由一系列对象组成。每一个对象都是功能中心，具有明确分工，可以完成接受信息、处理数据、发出信息等任务。因此，面向对象编程具有灵活性、代码的可重用性、模块性等特点，容易维护和开发，非常适合多人合作的大型软件项目。

那么，“对象”（object）到底是什么？我们从两个层次来理解。

- **“对象”是单个实物的抽象。**

  一本书、一辆汽车、一个人都可以是“对象”，一个数据库、一张网页、一个与远程服务器的连接也可以是“对象”。当实物被抽象成“对象”，实物之间的关系就变成了“对象”之间的关系，从而就可以模拟现实情况，针对“对象”进行编程。

- **“对象”是一个容器，封装了“属性”（property）和“方法”（method）。**

  所谓“属性”，就是对象的状态；所谓“方法”，就是对象的行为（完成某种任务）。比如，我们可以把动物抽象为animal对象，“属性”记录具体是那一种动物，“方法”表示动物的某种行为（奔跑、捕猎、休息等等）。

## 创建对象

#### 1.1、原始模式

```javascript
// 1、原始模式，Object构造函数方式
var obj = new Object();
obj.name = 'Petter';
obj.age  =  28;
obj.showName = function() { alert(this.name); }

// 2、原始模式，对象字面量方式
var obj = {
    name: 'Petter',
  	age: 28,
  	showName: function() {
        alert(this.name);
    }
}
```

> 优势：创建单一对象时比较快捷方便。
>
> 缺陷：当我们要创建批量对象时，代码过于冗余。脱离对象原型。

#### 1.2、工厂模式

```javascript
function createPerson(name, age) {
	var obj = new Object();
	obj.name = name;
	obj.age  = age;
	obj.showName = function() {
		alert(obj.name);
	}
	return obj;
}

var obj1 = createPerson('Admin', 22);
var obj2 = createPerson('Petter', 28);
```

> 优势：批量化生产，便捷方便。
>
> 缺陷：脱离对象原型。

#### 1.3、构造函数

```javascript
function Person(name, age) {
	this.name = name,
	this.age  = age,
	this.showName = function() {
		alert(this.name);
	}
}
var per1 = new Person("李强", 24);
var per2 = new Person("李伟", 28);
```

上面代码中，**Person** 就是构造函数，它提供模板，用来生成对象实例。为了与普通函数区别，构造函数名字的第一个字母通常大写。

构造函数的特点有两个。

- 函数体内部使用了 `this` 关键字，代表了所要生成的对象实例。
- 生成对象的时候，必需用 `new` 命令调用 `Person` 函数。

> 优势：对象实例拥有对象原型（ `constructor` ）
>
> ```javascript
> console.log(per1.constructor === Person); // true
> console.log(per2.constructor === Person); // true
> ```
> 缺陷：内存浪费

Javascript还提供了一个`instanceof` 运算符，验证原型对象与实例对象之间的关系。

```javascript
console.log(per1 instanceof Person); // true
console.log(per2 instanceof Person); // true
```

#### 1.4、原型模式

Javascript规定，每一个构造函数都有一个 `prototype` 属性，指向另一个对象。**这个对象的所有属性和方法，都会被构造函数的实例继承**。意味着，我们可以把那些不变的属性和方法，直接定义在`prototype`对象上。

```javascript
// 1、原型模式，直接定义prototype属性
function Person () {}
Person.prototype.name = 'Henrry Lee';
Person.prototype.age = 26;
Person.prototype.showName = function () { alert(this.name); };

// 2、原型模式，字面量定义方式
function Person () {}
Person.prototype = {
    name: 'Jack',
    age: 18,
    showName: function () { alert(this.name); }
};
var p1 = new Person(); //name='Jack'
var p2 = new Person(); //name='Jack'
```

> 提示：这里需要注意的是原型属性和方法的共享，即所有实例中都只是引用原型中的属性方法，任何一个地方产生的改动会引起其他实例的变化，因为它们指向同一块内存。



## 属性与方法

#### 2.1、属性

在对象中，变量被认为是属性。属性向我们描述对象，正如一部车的品牌、颜色或车型。定义属性的方法如下：

```javascript
// 1、直接使用 key : value 对形式创建属性
var car = {
	brand: "Benz",
	color: "black",
	model: "E200"
}
// 2、直接使用标识符作为属性(点语法)
var car = new Object();
car.brand = "Benz";

```

  **访问对象属性**，主要有两种方法：

- 点语法，其语法形式为：`Obj.property`，如  `person.name`
- 下标法，其语法形式为：`Obj["property"]`，如  `person["name"]`

#### 2.2、方法

在对象中，函数被认为是方法。方法代表和对象相关的任务。例如一部车可以加速或减速行驶。

```javascript
let car = {
	// 属性
	brand: "Benz",
	color: "black",
	model: "E200",
	// 方法
	speedUp: function() {
		console.log("正在加速！");
	},
	slowDown: function() {
		console.log("正在减速！");
	}
}
```

  **访问对象方法**，直接通过点语法即可访问，其语法形式：`Obj.function_name()`，如  `car.speedUp()`

## 对象操作

对于数据操作来讲，无非就是四种操作“增、删、改、查”。对于对象来讲，“**增**” 就是为一个对象新增一个之前不存在的属性名，然后进行赋值；“**改**” 就是对对象已经存在的属性名进行重新赋值，达到一个修改原始对象的效果；而 “**查**” 就是简单地通过对象的属性名访问即可。这些我们之前都讲解过，但对于 “**删**”来讲稍微有些特殊，需要用到关键字 “`delete`” 进行操作，为了说明问题，我们还是对这些操作进行回顾并在其中列出delete的使用方式。原对象如下：

```javascript
var phone = {
	brand:   "iPhone"
	model:   "iPhone7 Plus",
	pubDate: "2016-09-10",
	company: "Apple"
}
```

#### 3.1、对象操作（增）

```javascript
phone.color = 'black';
```

#### 3.2、对象操作（删）

```javascript
delete phone.company; // true
```

#### 3.3、对象操作（改）

```javascript
phone.pubDate = '2016-09-11';
```

#### 3.4、对象操作（查）

```javascript
phone.brand; // "iPhone"
phone.model; // "iPhone7 Plus"	
```

