### Object
1. 创建对象的方法，例如结果都是：我的名字是苗婧我的年龄是27

	```
	people = new Object;
    people.name = "苗婧";
    people.age = "27";
    document.write("我的名字是"+people.name+"我的年龄是"+people.age);
	```

    ```
	people = {"name":"苗婧","age":"27"};
    document.write("我的名字是"+people.name+"我的年龄是"+people.age);
	```

    ```
	function people(name,age){
      this._name = name;     //要用this索引才能有结果，否则出错
      this._age = age;     //_name和_age可以省掉_,只是自己定义的变量而已
    }
    sum = new people("苗婧","27");
    document.write("我的名字是"+sum._name+"我的年龄是"+sum._age);
	```

2. Array数组对象：

	1.concat():数组合并

	```
	var a=["name","age"];
    var b=["苗婧","27"];
    var c=a.concat(b);
    document.write(c);     //结果：name,age,苗婧，27
	```

    2.sort():排序

	```
	var a=["1","6","2"];
    document.write(a.sort());     //结果：1,2,6  升序的
	```

    ```
	var a=["1","6","2"];
    document.write(a.sort(function(a,b){
    	return b-a;
    }));     //结果：6,2,1  降序的
    ```

    2.push():末尾追加元素

	```
	var a=["1","2"];
    a.push("3")
    document.write(a);     //结果：1,2,3
    ```

    3.reverse():用于颠倒数组中元素的顺序

	```
	var a=["1","2"];
    document.write(a.reverse());     //结果：2,1
    ```

3. 字符串对象

	1.length:长度

	```
	var str = "Hello"
    document.write(str.length);     //结果：5
	```

    2.indexOf():可返回某个指定的字符串值在字符串中首次出现的位置。从0开始，区分大小写，如果要检索的字符串值没有出现，则该方法返回 -1。

	```
	var str = "Hello World"
    document.write(str.indexOf("Hello"));     //结果：0   从第0个开始
	```

	```
	var str = "Hello World"
    document.write(str.indexOf("World"));     //结果：6   算上空格
	```

 	3.match():内容匹配，字符串内检索指定的值，或找到一个或多个正则表达式的匹配。如果存在就匹配出来，如果不存在就返回null。

	```
	var str = "Hello World"
    document.write(str.match("World"));     //结果：World
	```

	4.replace():替换内容,需要两个参数，原始参数和替换后的新参数

	```
	var str = "Hello World"
    document.write(str.replace("World","苗婧"));     //结果：Hello 苗婧
	```

    5.toUpperCase()转换大写和toLowerCase()转换小写

    ```
	var str = "Hello World"
    document.write(str.toUpperCase());     //结果：HELLO WORLD
	```

    6.split():字符串转换为数组

    ```
	var str = "hello,苗婧,你好美";
    var s = str.split(",");     //前提是用什么分开的，逗号空格竖线等都ok
    document.write(s[1]);     //改变数组的第几个     结果：苗婧
	```

4. Date日期对象：

	```
	function startTime(){
      var today = new date();
      var h = today.getHours();
      var m = today.getMinutes();
      var s = today.getSeconds();
      m = checkTime(m);
      s = checjTime(s);
      document.getElementByID("timetext").innerHTML = h+":"+m+":"+s;
      t = setTimeout(function(){
      	startTime();
      },1000);     //每隔1秒自动刷新
    }

    function checjTime(i){
      if(i<10){     //一位数字时前面加个0占位
        i="0"+i;
      }
      return i;
    }

    //在body元素里加载onload("startTime()")
	```

5. Math对象：用来计算一些算数任务。

	1.round():四舍五入。

	`document.write(Math.round(2.6));     //结果：3`

	2.random（）：随机数0-1。

	`document.write(Math.random());     //结果：刷新一次就新得到一个0-1的数字`

    `document.write(Math.random()*10);     //结果：可以乘以`

    `document.write(parseInt(Math.random());     //结果：整数`

	3.max():最大值和min():最小值：

	`document.write(Math.max(1,2,3,4));     //结果：4`

    4.abs():绝对值：

	`document.write(Math.abs(-10));     //结果：10`



### 函数

	```
	function demo(){
    	var a = 10;
        var b= 20;
    	var sum = a+b;
        alert(sum);     //结果：30
    }
    demo();     //必须调用后才有效果，或者在HTML内部调用，onclick=“demo()”
	```

	```
	function demo(a,b){     //参数用逗号隔开，可以是任意多个
    	var sum = a+b;
        return sum;
    }
    var v1 = demo(10,20);     //要对应传递两个参数
    alert(v1);     //结果：30
	```

	```
	function demo(name,age){
    	alert("我的名字是"+name+"我的年龄是"+age);
    }
    demo("苗婧",27);     //结果：我的名字是苗婧我的年龄是27
    ```

    ```
	function demo(){
    	return "hello";
    }
    var a = demo()+"苗婧"
    alert(a);     //结果：hello苗婧
    ```

    ```
	function demo(a,b){
    	if(a>b){
        	return("a比较大");
        }else{
        	return("b比较大");
        }
    }
    demo(200,20);     //a比较大
    ```

    ```
	function demo(a,b){
    	if(a>b){
        	return("a比较大");
        }else{
        	return("b比较大");
        }
    }
    var v=demo(200,20);
    alert(v);     //a比较大
    ```

### 函数

1. 声明变量的方式和构造函数的方式：

    ```
    var person = {     //var; 变量名；=；大括号
		name:"张三",      //字符串要有引号，结束用逗号
        age:20,     //数字不需要引号
        eat:function(){
        	alert("你好")
        }
    }
    alert(person.name);     //结果：张三
    alert(person.age);     //结果：20
    alert(person.eat());     //结果：你好
    ```

	```
    function person(){
				           //创建函数当作类使用，也可以在里初始化变量
    }
    person.prototype = {     //prototype是添加属性
		name:"张三",
        age:20,
        eat:function(){
        	alert("你好")
        }
    }
    var p = new person();     //用new创建对象
    alert(p.name);     //得到相同结果
    ```

2. 继承父类：

	```
	function People(){}
    People.prototype.say = function(){     //创建一个say的方法
    	alert("你好");
    }

    function Student(){}
    Student.prototype = new People();
    var s = new Student();
    s.say();     //结果：你好
	```

3. 覆写父类：

	```
	function People(){}
    People.prototype.say = function(){
    	alert("你好");
    }

    function Student(){}
    Student.prototype = new People();
    Student.prototype.say = function(){     //覆写父类
    	alert("Stu-你好");
    }

    var s = new Student();
    s.say();     //覆盖父类的结果，结果：Stu-你好
	```

4. 调用父类：
    ```
	function People(){}
    People.prototype.say = function(){
    	alert("你好");
    }

    function Student(){}
    Student.prototype = new People();
    var Ssay = Student.prototype.say;     //创建子类的一个对象
    Student.prototype.say = function(){
    	Ssay.call(this);
        alert("S-你好")
    }
    var s = new Student();
    s.say();     //结果：你好；S-你好；
	```

5. 传递和调用参数：

    ```
	function People(name){     //父类里添加一个参数
    	this._name = name;     //用this进行索引
    }
    People.prototype.say = function(){
    	alert("peo-hello"+ this._name);     //可以直接使用索引
    }

    function Student(name){     //子类里也添加一个参数
    	this._name = name;     //用this进行索引
    }
    Student.prototype = new People();
    var Ssay = Student.prototype.say;
    Student.prototype.say = function(){
    	Ssay.call(this);
        alert("stu-hello"+this._name);     //可以直接使用索引
    }
    var s = new Student("张三");     //要传递一个参数
    s.say();     //结果：peo-hello张三；stu-hello张三；
	```

6. 封装：对信息起到一个隐藏的作用：

    ```
	（function(){
         //小括号，function(){},把信息放在function里边
    }）     //用一个()来进行自己执行
	```

    ```
	（function(){
    	var n = "李四";     //定义一个属性n，但是封装后就调用不到了，在起内部可以引用，出了People这个函数后就调用不到了
         function People(name){
            this._name = name;
        }
        People.prototype.say = function(){
            alert("peo-hello"+ this._name);
        }
    });     //结尾要加一个分号

    function Student(name){     //子类里也添加一个参数
    	this._name = name;     //用this进行索引
    }
    Student.prototype = new People();
    var Ssay = Student.prototype.say;
    Student.prototype.say = function(){
    	Ssay.call(this);
        alert("stu-hello"+this._name);     //可以直接使用索引
    }
    var s = new Student("张三");     //要传递一个参数
    s.say();     //结果：peo-hello张三；stu-hello张三；

	function lisi(){
    	alert(n);
    }
    lisi();     //结果：报错，未定义，因为封装后，信息隐藏，调用不到
	```

    ```
    var n = "李四";     //定义一个属性n，没有被封装，所以后面随便使用都能被调用到
     function People(name){
        this._name = name;
    }
    People.prototype.say = function(){
        alert("peo-hello"+ this._name);
    }

    function Student(name){     //子类里也添加一个参数
    	this._name = name;     //用this进行索引
    }
    Student.prototype = new People();
    var Ssay = Student.prototype.say;
    Student.prototype.say = function(){
    	Ssay.call(this);
        alert("stu-hello"+this._name);     //可以直接使用索引
    }
    var s = new Student("张三");     //要传递一个参数
    s.say();     //结果：peo-hello张三；stu-hello张三；

	function lisi(){
    	alert(n);
    }
    lisi();     //结果：peo-hello张三；stu-hello张三；李四
	```

7. 封装后如何对其进行引用

	```
	(function(){
    	var n = "李四";
         function People(name){
            this._name = name;
        }
        People.prototype.say = function(){
            alert("peo-hello"+ this._name);
        }
        window.People = People     //对外部公开一个接口
    });

   (function(){
        function Student(name){
            this._name = name;
        }
        Student.prototype = new People();
        var Ssay = Student.prototype.say;
        Student.prototype.say = function(){
            Ssay.call(this);
            alert("stu-hello"+this._name);
    	}
        window.Student = Student;
    });

    var s = new Student("张三");    //要传递一个参数
    s.say();     //结果：peo-hello张三；stu-hello张三；

	function lisi(){
    	alert(n);
    }
    lisi();     //结果：peo-hello张三；stu-hello张三；李四
	```

8. 通过对象赋值的方式进行继承：

	```
	function Person(){
      var _this = {};     //创建一个新对象
      _this.sayHello = function(){    //创建一个sayHello的方法
        alert("你好");
      }
      return _this;     //要返回当前的this
    }

	//如何继承
    function Teacher(){
    	var _this = Person();     //把Person赋值给当前this
        return _this;
    }

    var t = Teacher();
    t.sayHello();     //结果：你好
	```
    注：同理覆写，传参和封装
