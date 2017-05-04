### 关于JavaScript的基本知识点
1. 一切变量，函数名和操作符都区分大小写。
2. 标识符：是指变量，函数，属性的名字，或者函数的参数，可以是一个或多个字符。

 	1. 其规则是：第一个字符必须是一个字母，下划线或一个美元符号，其他字母可以是字母，下划线，美元符号或数字，一般用驼峰大小写格式（即第一个字母小写，其余每个有意义的单词首字母大写，例doSomethingImportant）
 	2. 关键字，保留字，true，false和null不能用作标识符。

3. 引用方式：两种

   第一种：直接写在HTML的script标签里。

   第二种：通过script标签的src属性外部引用，通常放在/body后面。

4. 输出：

   `document.write("hello")     //结果：你好`

    ```
	<p id="name">你好</p>     //结果：改变文案内容
    <script>document.getElementByID("name").innerHTML="改变文案内容"</script>
	```

5. 语法：按照编写顺序依次执行；标识符；空格；代码换行；关键字；

6. 注释：

    `//单行注释`

    ` /* 多行注释 */`

7. 语句：语句以分号结尾，无论是一条语句还是多条语句，一般使用代码块的形式{}
8. 变量：
    ```
    var a = "hello";
    function check(){
        var a = "hi";
        return a;
    }
    check();     //结果：“hi”。函数体内局部变量优先级高于同名的全局变量
    ```
    ```
    function test(){
        var a = "hi";
    }
    test();
    alert(a);	//结果：“undefined”。局部变量
    ```
    ```
    var a = "hi";
    function test(){
      test();
    }
    alert(a);   //结果：“hi”。全局变量
    ```
    ```
    var a = "hi";
    function test(){
    }
    test();
    alert(a);   //结果：“hi”。全局变量
    ```
    ```
    function test(){
      a = "hi";     //不用var声明的全局变量，要调用才有结果
    }
    test();
    alert(a);   //结果：“hi”。全局变量可以不写var
    ```

9. 数据类型：Undefind,Null,Boolean,Number和String五种基本数据类型，Object（包括数组和函数）一种复杂数据类型。五种基本数据类型是原始值，不可更改，值相等时他们才相等，比较两个单独字符串时，当且仅当长度相等且每个索引的字符都等时，他们才等。对象是可变的，值是可修改的，对象即便包含同样属性和相同值，或是各个索引完全相等，那他们也不等。
    ```
     var a = {x=1},b = {x=1};  //a,b不全等，两个单独对象永不相等。
     var a = [],b = [];  //a,b不全等，两个单独数组永不相等。
     var a = [],b = a;b[0] = 1;a[0];a===b;  //a,b全等，ab引用同一个数组
    ```
     1. typeof:检测给定变量的数据类型。
     2. Boolean:只有true（转数值1）和false（转数值0），区分大小写，所以True只是标识符。
     3. number：float浮点数值；NaN非数值；范围在负无穷到正无穷；
     4. Undefined和Null都表示为空。
    ```
    null == undefind;   //结果：true
    null === undefind;   //结果：false
    typeof null == typeof undefind;   //结果：false
    ```
    | Undefined | Null |
    |--------|--------|
    |  结果返回undefined，表示未定义，不存在      |   结果返回Null，表示无值    |
    |  “无”时转为NaN      |   “无”时转为0     |
    |  变量被声明了但没赋值，就等于undefind;调用函数时应该提供的参数没有提供；对象没有赋值的属性，该属性值为undefind;函数没有返回值时，默认返回undefined     |   作为函数参数，表示该参数不是对象     |

10. 操作符：

     1. 一元加即转换成正数，一元减表示负数。
     2. 按位与（&）都是1才1，有一个0就是0；按位或（|）有一个1就是1，都是0时才0；按位异或（^）有一个1时才1，有两个1或两个0时才0。
     3. 递增++ 和 递减--。

        ```
         var a = 2;
         var b = 20;
         var c = --a+b;   //结果：21（--放在前面的减完再执行）
         var d = a+b;   //结果：21（使用递减后的值为现值）
        ```
        ```
         var a = 2;
         var b = 20;
         var c = a-- +b;   //结果：22（--放在后面的执行完再减）
         var d = a+b;   //结果：21（使用递减后的值为现值）
        ```
     4. 布尔操作符

         逻辑非！(求反) | 逻辑与&& | 逻辑或 &vert;&vert;
         -------------|---------|---------
         对象返回false；null，NaN，undefined，空字符串返回true；非空字符串返回false；数值0返回true；任意非0数值包括infinity，返回false|有null就返回null；有NaN就返回NaN；有undefined就返回undefined；第一个是对象或者两个都是对象，则返回第二个操作数；若第二个操作数是对象，则只有在第一个是true时才返回第二个对象|第一个操作数是对象则返回第一个；第一个结果是false则返回第二个；两个都是对象返回第一个；两个都是null返回null；都是NaN返回NaN；都是undefined返回undefined

    5. 一个=是赋值，两个=是相等，三个=是全等，！=不相等，！==不全等

        `var a = ("55" == 55)  //true,因为转换后相等`

        `var a = ("55" === 55)  //false,不同的数据类型不相等`
    6. 条件操作符:

        `var max = (a > b) ? a : b;   //若a>b,则a复制给max,a<=b,则b值返回给max`


11. 数组的写法：

       ```
        //第一种写法：
        var arr = [1,2,"你好“,4,5];

        //第二种写法：用new声明一个对象
        var arr = new Array(1,2,"你好“,4,5);

        //第三种写法：虚拟一个对象后再赋值
        var arr = new Array（）;
        arr[0] = 1;
        arr[1] = 2;
        arr[2] = "你好";

        document.write(arr[0]);     //结果：1
       ```

12. 声明变量的方式和构造函数的方式：

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
13. 创建对象有几种方式？

	1. 基于Object对象

    ```
    var person = new Object();
    person.name = 'My Name';
    person.age = 18;
    person.getName = function(){
        return this.name;
    }
    ```

    2. 对象字面量方式（比较清楚的查找对象包含的属性及方法）

    ```
    var person = {
        name : 'My name',
        age : 18,
        getName : function(){
            return this.name;
        }
    }
    ```

14. JSON：作用，设计结构：json是一种轻量级的数据交换格式，体积小,传输快，主要用于传送数据；易于阅读和编写，同时也易于机器解析和生成；客户端操纵XML的时候需要创建ActiveX对象，JSON则完全就是一个JS对象，不需要创建DOM。

    ```
    var languages = {
        cn: {
            lang: 'zh_cn',
            name: '中文'
        },
        en: {
            lang: 'us_en',
            name: '英文'
        }
    };
    ```

    ```
	{
    "root": [
        {
            "workDay": "1",
            "productType": "ZT4",
            "customBatch": "",
            "destination": "020"
        },
        {
             "workDay": "7",
             "productType": "ZT4",
             "customBatch": "",
             "destination": "020"
         }]
    }
	```
15. 遍历：
	json数据
	```
	var myCost = [
	{
		'costtype': {
			'type': '1',
			'value': '衣服a'
		},
		'pay': 10
	},
	{
		'costtype': {
			'type': '2',
			'value': '裤子'
		},
		'pay': 20
	},
	{
		'costtype': {
			'type': '3',
			'value': '裙子'
		},
		'pay': 30
	},
	{
		'costtype': {
			'type': '1',
			'value': '衣服b'
		},
		'pay': 40
	}
	];
	```
    遍历总花销：

    ```
	var prize = 0;
    for (var i = 0; i < myCost.length; i++) {
        var cost = myCost[i];
        prize += cost.pay;
        console.log(prize);
    }
	```

    遍历type为1的衣服的花销：

    ```
	var prize = 0;
    for (var i = 0; i < myCost.length; i++) {
        var cost = myCost[i];
        var type = cost.costtype.type;
        if (type == 1) {
            prize += cost.pay;
            console.log(cost.pay);
        }
    }
    console.log("总共:" + prize);
	```

16. 遍历的两种方式：

	```
    function(val){

      var result = '';

      for(var t = 0;t < orderList.length;t++){

        if(orderList[t].value == val){
          result = orderList[t].text;
        }

      }

      return result;
    }
    ```

    ```
    function(val){

      var result = '';

      orderList.forEach(function(item,index){

        if(item.value == val){
          result = item.text;
        }

      });

      return result;
    }
    ```

17. ++和--的区别：

	```
	var a = [1,2,3,4];

    for(var i=0; i < a.length; i++){
      if(i == 2){
        a.splice(i,1)     //去掉数组的第2个索引的1个值
      }
    }

    console.log(a)     //结果：[1,2,4]
	```

	如果去掉好几个值，那么i的值就变了，接下来的操作就都不再准确，这时就用--

    ```
	var a = [1,2,3,4];

    for(var i=0; i < a.length; i++){
      if(i == 1){
        a.splice(i,2)     //去掉数组的第1个索引的2个值
      }
    }

    console.log(a)     //结果：[1,4]     4原来是3的值，现在变成1的值了
	```

    ```
	var a = [1,2,3,4];

    for(var i=a.length; i < = 0; i--){
      if(i == 1){
        a.splice(i,2)
      }
    }

    console.log(a)     //结果：[1,4]
	```

18. 数字1-10求和：

	```
	var a = 0;
    for(var i=0;i<10;i++){
      a+=i;
    }
    console.log(a);
	```

19. 求6,56,888,77,5543,999的和：

	```
	var a = 0;
    var arry = [6,56,888,77,5543,999];
    for(i=0;i<arry.length;i++){
      a+=arry[i];
    }
    console.log(a);
	```

20. 作用域：作用域就是变量与函数的可访问范围，变量的作用域有全局作用域和局部作用域两种。

	1. 全局作用域：最外层函数和在最外层函数外面定义的变量拥有全局作用域；所有末定义直接赋值的变量自动声明为拥有全局作用域；所有window对象的属性拥有全局作用域，例如window.name、window.location、window.top等等。
	2. 局部作用域：在函数内声明的变量具有函数作用域，局部变量优先级高于全局变量。

21. 作用域链：就是一个变量解析的过程，第一个对象中没有名为x的属性，js会继续查找链上的下一个对象。如果第二个对象依然没有名为x的属性，则会继续查找下一个，以此类推。with语句主要用来临时扩展作用域链，将语句中的对象添加到作用域的头部。

	```
	person={name:"yhb",age:22,height:175,wife:{name:"lwy",age:21}};
with(person.wife){
    console.log(name);
}
//with语句将person.wife添加到当前作用域链的头部，所以输出的就是：“lwy"
	```

22. 引用类型：.运算优先级高于=运算符

	```
	var a = {n:1};
    var b = a;
    a.x = a = {n:2};

    alert(a.x);// --> undefined
    alert(b.x);// --> [object Object]
	```

23. 类型转换：
    1. 比较时候的转换的原则:

        一个是number一个是string时，会尝试将string转换为number
        尝试将boolean转换为number，0或1
        尝试将Object转换成number或string，取决于另外一个对比量的类型

    2. 运算过程的转换原则：

        字符串与数字相加，变成字符串
        字符串与数字相减，变成数字

24. 写一个function，清除字符串前后的空格。(兼容所有浏览器)

    ```
	if (!String.prototype.trim) {
     String.prototype.trim = function() {
     return this.replace(/^\s+/, "").replace(/\s+$/,"");
     }
    }

    // test the function
    var str = " \t\n test string ".trim();
    alert(str == "test string"); // alerts "true"
    ```

25. 如何消除一个数组里面重复的元素？

	`myArray.filter(function(elem, pos,self){return self.indexOf(elem)== pos;})`

26. ES6中的箭头函数

	```
	var odds = evens.map(function (v) {
      return v + 1;
    });

    //相当于
	var odds = evens.map(v => v + 1);
	```

    ```
	var nums = evens.map(function (v, i) {
      return v + i;
    });

    //相当于
    var nums = evens.map((v, i) => v + i);
	```

    ```
	nums.forEach(function (v) {
      if (v % 5 === 0) fives.push(v);
    });

    //相当于
    nums.forEach(v => {
      if (v % 5 === 0)
        fives.push(v);
    });
	```

27. 原型链：因为每个对象和原型都有原型，对象的原型指向原型对象，而父的原型又指向父的父，这种原型层层连接起来的就构成了原型链。

	```
	function Person(name, age){
        this.name = name;
        this.age = age;
      }
    Person.prototype.MaxNumber = 9999;
    Person.__proto__.MinNumber = -9999;
    var will = new Person("Will", 28);
    console.log(will.MaxNumber); // 9999
    console.log(will.MinNumber); // undefined
	```

    当查找一个对象的属性时，JavaScript 会向上遍历原型链，直到找到给定名称的属性为止，到查找到达原型链的顶部（也就是 Object.prototype），如果仍然没有找到指定的属性，就会返回 undefined。在这个例子中分别给”Person.prototype “和” Person.proto”这两个原型对象添加了”MaxNumber “和”MinNumber”属性，这里就需要弄清”prototype”和”proto”的区别了。