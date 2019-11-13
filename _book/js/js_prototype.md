## 1. 构造函数

### 1.什么是构造函数

> codes/js原型函数实例代码/01_constructor.html

1. 创建变量的两种方式

	1. 对象字面量

		```
		 //字面量创建对象
	    let person3 = {
	        name:"test",
	        age:20
	    }
		
		```
	
	2. 使用new表达式
	
		```
		
		function Perosn() {
          this.name = 'test';
          this.age = 20;
    	}
    	//通过new创建
    	person1 = new Perosn();
		```
		
	
	
	
2. 什么是构造函数

	当被使用new关键字申明表变量的函数我们称为构造函数
	
	```javascript
	
	    function Perosn() {
	        this.name = 'test';
	        this.age = 20;
	    }
	
	    person1 = new Perosn();
	
	```
	
3. 为什么要使用构造函数

	类似于像python的类一样,我们可以在构造函数中初始化变量,就不用每次都去定义了
	
	```javascript
	
	    function Perosn() {
	        this.name = 'test';
	        this.age = 20;
	    }
	
	    person1 = new Perosn();
	    person2 = new Perosn();
	    person1.name
	    person2.name
	
	```
	
4. 为什么我们可以使用构造函数中的初始化变量(构造函数的创建过程解析)

	1. 构造函数在初始化的时候,隐式的做了一个return this,所以我们可以接收到他的变量

		```
		
		function PerosnThis() {
	       this.name = 'test';
	       this.age = 20;
	       //return this
	   }
		
		```
	
	2. 最好不要在构造函数中去加入其它的return,因为他会毁掉你的环境变量

		```
		
		    function PersonnThis1() {
	           this.name = 'test';
	           this.age = 20;
	           return {}
	    	 }
	    	
	    	person4 = new PersonnThis1();
	
	   	    document.write(person4.name)
		
		```
		
5. 对象中使用constuctor可以去帮助我们找到构造函数

    ```
    
    function PersonnThis1() {
        this.name = 'test';
        this.age = 20;
        //return {}
    }

	 person4 = new PersonnThis1();	
	 document.write(person4.constructor === PersonnThis1);
    
    ```
    
# 普通对象和函数对象

> codes/js原型函数实例代码/02_objects.html

1. 首先来看一个栗子

	function的我们称为函数对象,object的我们称为普通对象
	
	```
	
	 var o1 = {};
    var o2 = new Object();
    var o3 = new f1();

    function f1(){};
    var f2 = function(){};
    var f3 = new Function('str','console.log(str)');

    console.log(typeof Object); //function
    console.log(typeof Function); //function

    console.log(typeof f1); //function
    console.log(typeof f2); //function
    console.log(typeof f3); //function

    console.log(typeof o1); //object
    console.log(typeof o2); //object
    console.log(typeof o3); //object
	
	```
	
2. 函数对象 vs 普通对象

    函数对象: 通过 function来创建的对象就是函数对象
    普通对象: 其他
    

# 原型对象

>codes/js原型函数实例代码/03_prototype_brief.html

1. 原型对象的意义

	在 JavaScript 中，每当定义一个对象（函数也是对象）时候，对象中都会包含一些预定义的属性。其中每个函数对象都有一个__proto__ 属性（预定义进去的 不需要去手工创建），这个属性指向函数的原型对象。
	
	那么其实原型对象不是什么高深的东西,就是一个对象而已,固定为prototype
	
	```
	
	
	 function Person() {

        this.name = 'canvas'

    }

    Person.prototype.sayName = function () {
        alert(this.name);
    };
    
    
    let person11 = new Person();
    document.write(person11.__proto__ === Person.prototype) //true
	
	```
	
2. 原型对象是干什么用的？

	我们上面说的对象有继承功能,其实就是在原型对象里面去定义变量方法,然后我们的对象就可以去继承这些变量方法
	
	```
	document.write(person11.name);
	```
	
	用法就是如果你想让对象去继承你的方法,那么在prototype中去定义
	
3. \__proto__ 的用法

	1. 这个方法,会自动的取指向构建函数的prototype属性


		```
		
		  let person1 = new Person();
	     document.write(person1.__proto__ === Person.prototype); //true
	
	
	    //prototype.constructor属性会自动的指向本Person
	    document.write(Person.prototype.constructor === Person);
	
	    document.write(person1.constructor === Person);
	
	    let person3 = {};
	
	    document.write(person1.__proto__ === Person.prototype);
	    document.write(person3.__proto__ === Object.prototype);
		
		```
	
	2. 每个prototype里面 带有constructor 方法 可以指向、__proto__的属性的对象

		```
		
		    let person3 = {};
		    document.write(person3.__proto__ === Object.prototype);
		    document.write(person3.__proto__.constructor === Object)
		
		```
	
	3. 调用 constructor的原理

		其实调用 constructor 调用的是prototype里面的constructor,我们前面说过,他prototype是用于给对象继承东西用的
		
		```
		
		document.write(Person.prototype.constructor === Person);

      document.write(person1.constructor === Person);
		
		
		
      ```
      
  4. this 指向哪里？
  
      其实我们的this表示的是本对象
      
  5. typeof vs instanceof

  	  1. typeof 变量的类型
  	  2. instanceof 查看是否在原型链上面(后面讲到)
  	  
      
  6. prototype到底是什么研究

      ```
      
      function Person(){}
      console.log(typeof Person.prototype); //Object
      console.log(typeof Function.prototype); // Function，这个特殊
      console.log(typeof Object.prototype); // Object
      console.log(typeof Function.prototype.prototype);
    
      ```
      
      我们说到 prototype是个对象,但是Function.prototype是个特殊 他是一个function，其余是object

  
		
# 构造器
>codes/js原型函数实例代码/05_constuctor.html

其他的 Array Date都是function类型

```
    document.write(typeof Date);//function
    document.write(typeof Array);
    document.write(typeof Function);

    document.write(typeof String);
```


# 练习:

> codes/js原型函数实例代码/06_anwsers.html

person1.__proto__ 是什么？
Person.__proto__ 是什么？
Person.prototype.__proto__ 是什么？
Object.__proto__ 是什么？
Object.prototype__proto__ 是什么？


```
	 var animal = function(){};
	 var dog = function(){};
	
	 animal.price = 2000;
	 dog.prototype = animal;
	 var tidy = new dog();

```


# new对象的创建过程

```
创建空对象； 
　　var obj = {};
设置新对象的constructor属性为构造函数的名称，设置新对象的_proto_属性指向构造函数的prototype对象； 
　　obj._proto_ = ClassA.prototype;

使用新对象调用函数，函数中的this被指向新实例对象： 
　　ClassA.call(obj);　　//{}.构造函数();

将初始化完毕的新对象地址，保存到等号左边的变量中

```


	
	

	

