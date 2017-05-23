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
    ```
	var foo = 1;
    function aa(){
    	//相当于省略了var foo;
        console.log(foo);
        var foo = 2;
        console.log(foo);
    }
    aa();     //结果：undefined和2
	```
    ```
	var foo = 1;
    function aa(){
        console.log(foo);
        foo = 2;     //相当于全局变量
        console.log(foo);
    }
    aa();     //结果：1和2
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

    3. 原型链的方式添加属性

	```
	function Parent(){

    };
    Parent.prototype.name="李小龙";
    Parent.prototype.age="30";
    Parent.prototype.lev=lev;
    var x =new Parent();
    alert(x.name);
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

28. 闭包：就是能够在外部访问函数内部的函数。在本质上，闭包就是将函数内部和函数外部连接起来的一座桥梁。用途：读取函数内部的变量；使变量的值始终保持在内存中

	```
	function a(){
    	var i = 0;
        function b(){
        	alert(++i);
        }
        return b;
    }
    var c = a();
    c();
    //a执行完之后，并不会被被垃圾回收机制回收，因为b需要依赖a中的变量。
	```

	下面这个ul，如何点击每一列的时候alert其index?

    ```
    <ul id=”test”>
        <li>这是第一条</li>
        <li>这是第二条</li>
        <li>这是第三条</li>
    </ul>

	// 方法一：
    var lis=document.getElementById('2223').getElementsByTagName('li');
    for(var i=0;i<3;i++)
    {
        lis[i].index=i;
        lis[i].onclick=function(){
            alert(this.index);
        };
    }

    //方法二：
    var lis=document.getElementById('2223').getElementsByTagName('li');
    for(var i=0;i<3;i++)
    {
        lis[i].index=i;
        lis[i].onclick=(function(a){
            return function() {
                alert(a);
            }
        })(i);
    }
	```

29. JavaScript是一门什么样的语言，它有哪些特点？

	JavaScript 是一种脚本语言；动态的；不需要编译就可以由解释器直接运行；变量松散定义，属于弱类型语言；面向对象的（把数据及对数据的操作方法放在一起，作为一个相互依存的整体）。

30. 强类型与弱类型的区别：

    区分大小写，需要实现申明类型外,一个重要的区别是,弱类型的语言的东西没有明显的类型,他能随着环境的不同,自动变换类型，而强类型则没这样的规定,不同类型间的操作有严格定义,只有相同类型的变量才能操作,虽然系统也有一定的默认转换,当绝没有弱类型那么随便

31. 如何判断某变量是否为数组数据类型？

	```
    if(typeof Array.isArray==="undefined")
    {
      Array.isArray = function(arg){
            return Object.prototype.toString.call(arg)==="[object Array]"
        };
    }
	```

32. 已知ID的Input输入框，希望获取这个输入框的输入值

	`document.getElementById(“ID”).value`

33. 希望获取到页面中所有的checkbox怎么做？

	```
	var domList = document.getElementsByTagName(‘input’)
    var checkBoxList = [];
    var len = domList.length;　　//缓存到局部变量
    while (len--) {　　//使用while的效率会比for循环更高
      if (domList[len].type == ‘checkbox’) {
          checkBoxList.push(domList[len]);
      }
    }
	```

34. 设置一个已知ID的DIV的html内容为xxxx，字体颜色设置为黑色

	```
	var dom = document.getElementById(“ID”);
    dom.innerHTML = “xxxx”
    dom.style.color = “#000”
	```

35. 看下列代码输出为何？解释原因。

	```
	var a;
    alert(typeof a); // undefined，在使用var声明变量但并未对其赋值进行初始化时，这个变量的值就是undefined
    alert(b); // 报错，而b由于未声明将报错。注意未申明的变量和声明了未赋值的是不一样的。
	```

    ```
	var a = null;
	alert(typeof a); //object，null是一个只有一个值的数据类型，这个值就是null。表示一个空指针对象，所以用typeof检测会返回”object”。
	```

36. 输出今天的日期，以YYYY-MM-DD的方式，比如今天是2014年9月26日，则输出2014-09-26

	```
	var d = new Date();
    // 获取年，getFullYear()返回4位的数字
    var year = d.getFullYear();
    // 获取月，月份比较特殊，0是1月，11是12月
    var month = d.getMonth() + 1;
    // 变成两位
    month = month < 10 ? '0' + month : month;
    // 获取日
    var day = d.getDate();
    day = day < 10 ? '0' + day : day;
    alert(year + '-' + month + '-' + day);
	```
37. `foo = foo||bar`相当于`if(!foo) foo = bar;`如果foo存在，值就是foo，否则值是bar。

38. 用js实现随机选取10–100之间的10个数字，存入一个数组，并排序。

	```
	var iArray = [];
    funtion getRandom(istart, iend){
            var iChoice = istart - iend +1;
            return Math.floor(Math.random() * iChoice + istart;
    }
    for(var i=0; i<10; i++){
            iArray.push(getRandom(10,100));
    }
    iArray.sort();
	```

39. clientWidth = width + padding

    clientHeight = height + padding

    offsetWidth = width + padding + border

    offsetHeight = height + padding + border

40. slice()方法 和splice 方法的区别

	splice() 方法 用于插入、删除或替换数组的元素；

    1. splice 的参数 ：splice (start, deleteCount, [item1[, item2[, . . . [,itemN]]]])

    2. 数组从 start下标开始，删除deleteCount 个元素，并且可以在这个位置开始添加 n个元素

	3. 当start ,deleteCount 均为0 的时候，也就是在数组的最前面插入新的元素。

	4. 当参数只有start，deleteCount 就是从start 下标开始删除deleteCount 个数组的元素，

	5. 当参数只有start参数时，就是删除 从start下标起至最后的元素，当参数 为负的时 则该参数规定的是从数组元素的尾部开始算起的位置 （-1 指的是 数组中倒数第一个元素， -2 指的是，数组中倒数第二个元素。）

	slice() 方法 可提取字符串的某个部分，并以新的字符串返回被提取的部分。

    1. 对于数组对象来说，slice 方法提取 从 start下标起 以end下标 为结尾的 一段元素（但不包括end下标的元素），然后返回新的数组，对原数组没有任何是影响，

	2. 当参数为负时 则该参数 是从 数组的末尾 索引 开始算起，（-1 指的是 数组中倒数第一个元素， -2 指的是，数组中倒数第二个元素。）

	3. 当参数为一个参数，当为一个参数时，提取是以 start下标起至末尾的部分元素。

	4. 当start为0时，等于说是克隆一个新的数组，克隆后两个数组进行各自的操作，都互不影响，var clone = array.slice(0)；

	```
	var array = new Array(1,2,3,4,5,6);
	array.slice(1,3)     //第一个起第三个止，不包括第三个
    结果：[2,3]     //array仍然是[1,2,3,4,5,6], 不改变原数组
	```

    ```
	var array = new Array(1,2,3,4,5,6);
	array.splice(1,3)     //两个参数时：删除第一个起的三个参数
    结果：[2,3,4]     //array变成[1,5,6], 改变原数组
	```

    ```
	var array = new Array(1,2,3,4,5,6);
	array.splice(1,3,0,8)     //多个参数时：删除第一个起的三个参数，并在此处插入0，8
    结果：[2，3，4]     //array变成[1，0，8，5，6], 改变原数组
	```

    ```
	var array = new Array(1,2,3,4,5,6);
	array.splice(2)     //一个参数时：删除第一个起到最后一个止的数组
    结果：[3，4，5，6]     //array变成[1，2], 改变原数组
	```

41. addEventListener()与removeEventListener()的用法

	`element.addEventListener(type,listener,useCapture)
`

	1. 其中element是要绑定函数的对象。
	2. type是事件名称，要注意的是"onclick"要改为"click","onblur"要改为"blur",也就是说事件名不要带"on"。
	3. listener当然就是绑定的函数了，记住不要跟括号。
	4. 最后一个参数是个布尔值，表示该事件的响应顺序，值参数是true，表示在捕获阶段调用事件处理程序；如果是false，表示在冒泡阶段调用事件处理程序。
	5. 移除时传入的参数与添加处理程序时使用的参数相同。这也意味着通过addEventListener()添加的匿名函数无法移除。

    ```
	var btn = document.getElementById("myBtn");
	btn.addEventListener("click", function () {
    	alert(this.id);
	}, false);
	btn.removeEventListener("click", function () {  //无效！
    	alert(this.id);
	}, false);
	```

    ```
	var btn = document.getElementById("myBtn");
	var handler = function () {
        alert(this.id);
    };
	btn.addEventListener("click", handler, false);
	btn.removeEventListener("click", handler, false);  //有效！重写后的这个例子没有问题，是因为在addEventListener()和removeEventListener()
	```

    ```
	<input id="info"  type="button" value="Click Me!" />
    function myhandler(){
        console.log("I have been clicked!");
              		document.getElementById('info').removeEventListener('click',myhandler,false);
            }
        var target=document.getElementById('info');
           target.addEventListener('click',myhandler,false);
	```
42. JavaScript定时器

    `window.setTimeout("function",time)；//设置一个超时对象，只执行一次,无周期`

    `window.setInterval("function",time)；//设置一个超时对象，周期＝'交互时间'`

    停止定时：

    `window.clearTimeout(对象) 清除已设置的setTimeout对象`

   ` window.clearInterval(对象) 清除已设置的setInterval对象`

43. Vue事件处理器

	1. 事件监听

    ```
	<div id="example-1">
      <button v-on:click="counter += 1">增加 1</button>
      <p>这个按钮被点击了 {{ counter }} 次。</p>
    </div>
    data: {
        counter: 0
      }
	```

    2. 方法事件

    ```
	<button v-on:click="greet">Greet</button>
    methods: {
        greet: function (event) {
          alert('Hello')
        }
      }
	```

    3. 内联处理器方法

    ```
	<button v-on:click="say('hi')">Say hi</button>
  	<button v-on:click="say('what')">Say what</button>
    methods: {
        say: function (message) {
          alert(message)
        }
      }
	```

    4. 常见方法

	```
	<!-- 阻止单击事件冒泡 -->
    <a v-on:click.stop="doThis"></a>
    <!-- 提交事件不再重载页面 -->
    <form v-on:submit.prevent="onSubmit"></form>
    <!-- 修饰符可以串联  -->
    <a v-on:click.stop.prevent="doThat"></a>
    <!-- 只有修饰符 -->
    <form v-on:submit.prevent></form>
    <!-- 添加事件侦听器时使用事件捕获模式 -->
    <div v-on:click.capture="doThis">...</div>
    <!-- 只当事件在该元素本身（而不是子元素）触发时触发回调 -->
    <div v-on:click.self="doThat">...</div>

	```

44. 什么是WebPack？

	WebPack可以看做是模块打包机，它做的事情是，分析你的项目结构，找到JavaScript模块以及其它的一些浏览器不能直接运行的拓展语言（Scss，TypeScript等），并将其打包为合适的格式以供浏览器使用。

	WebPack和Gulp相比有什么特性：Gulp是一种能够优化前端的开发流程的工具，而WebPack是一种模块化的解决方案。

	Grunt和Gulp的工作方式是：在一个配置文件中，指明对某些文件进行类似编译，组合，压缩等任务的具体步骤，这个工具之后可以自动替你完成这些任务。

	Webpack的工作方式是：把你的项目当做一个整体，通过一个给定的主文件（如：index.js），Webpack将从这个文件开始找到你的项目的所有依赖文件，使用loaders处理它们，最后打包为一个浏览器可识别的JavaScript文件。

	模块化：
	1. 提供两个工具处理样式表，css-loader 和 style-loader，css-loader使你能够使用类似@import 和 url(...)的方法实现 require()的功能,style-loader将所有的计算后的样式加入页面中，二者组合在一起使你能够把样式表嵌入webpack打包后的JS文件中。
	2. CSS modules，通过CSS模块，所有的类名，动画名默认都只作用于当前模块。
	3. webpack-pulgins：插件（Plugins）是用来拓展Webpack功能的，它们会在整个构建过程中生效。loaders是在打包构建过程中用来处理源文件的（JSX，Scss，Less..），一次处理一个，而插件并不直接操作单个文件，它直接对整个构建过程其作用，要使用某个插件，我们需要通过npm安装它。

45. 面向对象三大特性：

	1. 封装: 把相关的信息（无论数据或方法）存储在对象中的能力
    2. 继承: 由另一个类（或多个类）得来类的属性和方法的能力
    3. 多态: 编写能以多种方法运行的函数或方法的能力

46. 封装的常用方式：

	1. 生成实例对象的原始模式：这就是最简单的封装了，把两个属性封装在一个对象里面。但是，这样的写法有两个缺点，一是如果多生成几个实例，写起来就非常麻烦；二是实例与原型之间，没有任何办法，可以看出有什么联系。

        ```
        var Cat = {
            name : '',
            color : ''
        }
        var cat1 = {}; // 创建一个空对象
        cat1.name = "大毛"; // 按照原型对象的属性赋值
        cat1.color = "黄色";
        var cat2 = {}; // 生成两个实例
        cat2.name = "二毛";
        cat2.color = "黑色";
        ```

    2. 调用函数的方式

        ```
		function Cat(name,color) {
            return {
              name:name,
              color:color
            }
          }
          var cat1 = Cat("大毛","黄色");
        var cat2 = Cat("二毛","黑色");
        ```

    3. 构造函数的模式：this，new

		```
		function Cat(name,color){
            this.name=name;
            this.color=color;
        }
        var cat1 = new Cat("大毛","黄色");
        var cat2 = new Cat("二毛","黑色");
　　     alert(cat1.name); // 大毛
　　     alert(cat1.color); // 黄色
		```

        ```
		alert(cat1.constructor == Cat); //true
        alert(cat2.constructor == Cat); //true
        //constructor返回的是引用的谁
		```

		```
        alert(cat1 instanceof Cat); //true
        alert(cat2 instanceof Cat); //true
        //instanceof运算符，验证原型对象与实例对象之间的子类关系。
		```

    4. Prototype模式

		```
		function Cat(name,color){
            this.name = name;
            this.color = color;
        }
        Cat.prototype.type = "猫科动物";
        Cat.prototype.eat = function(){alert("吃老鼠")};
        var cat1 = new Cat("大毛","黄色");
        var cat2 = new Cat("二毛","黑色");
　　     alert(cat1.type); // 猫科动物
　　     cat1.eat(); // 吃老鼠
		```

    5. object.create()方式

        ```
		 var Person = {
        	name: 'pawn',
        	sayHello: function() {
            	console.log(this.name);
        	}
    	}
    	var p = Object.create(Person);
    	p.sayHello();
        ```

47. 继承的常用方式：

	1. 构造函数绑定：使用call或apply方法，将父元素的构造函数绑定在子对象上，即在子对象上加一行apply

	```
	function Cat(name,color){
　　　　Animal.apply(this, arguments);
　　　　this.name = name;
　　　　this.color = color;
　　}
　　var cat1 = new Cat("大毛","黄色");
　　alert(cat1.species); // 动物
	```

48. 跨域问题：只要协议、域名、端口有任何一个不同，都被当作是不同的域。http://www.cnblogs.com/2050/p/3191744.html

49. 处理错误的几种方式

    1. try...catch...

        ```
		function message()
        {
        try
           {
           adddlert("Welcome guest!")
           }
        catch(err)
           {
             txt="本页中存在错误。\n\n"
             txt+="点击“确定”继续查看本页，\n"
             txt+="点击“取消”返回首页。\n\n"
             if(!confirm(txt))
                 {
                 document.location.href="/index.html"
                 }
           }
        }
		```

    2. throw
    3. onerror

50. Promise，就是ES6原生提供的一个对象，用来传递异步操作的消息。特点：Promise 对象代表一个异步操作，有三种状态：Pending（进行中）、Resolved（已完成，又称 Fulfilled）和 Rejected（已失败）。但是，无法取消 Promise，一旦新建它就会立即执行，无法中途取消。其次，如果不设置回调函数，Promise 内部抛出的错误，不会反应到外部。

51. vue1.0和vue2.0的区别：

	1. 根元素： 在2.0中template下需要有一个根元素，否则会报错；
	2. 在1.0中的ready已经被mounted取代；
	3. api和生命周期的变化

52. 检测数据类型的几种方式：

	1. typeof：返回字符串，但是不适合检测引用数据类型。

		```
        var a = "iamstring.";
        var b = 222;
        var c= [1,2,3];
        var d = new Date();
        var e = function(){alert(111);};
        var f = function(){this.name="22";};


        alert(typeof a)   ------------> string
        alert(typeof b)   ------------> number
        alert(typeof c)   ------------> object
        alert(typeof d)   ------------> object
        alert(typeof e)   ------------> function
        alert(typeof f)   ------------> function
        其中typeof返回的类型都是字符串形式，需注意，例如：
        alert(typeof a == "string") -------------> true
        alert(typeof a == String) ---------------> false
        另外typeof 可以判断function的类型；在判断除Object类型的对象时比较方便。
		```

    2.  instanceof和constructor：某一个实例是否属于某个类，但instanceof在类的原型继承中，我们最后检测出来的结果未必准确，不适合检测基本类型，constructor能检测基本数据类型

		```
		alert(c instanceof Array) ---------------> true
        alert(d instanceof Date)
        alert(f instanceof Function) ------------> true
        alert(f instanceof function) ------------> false
        注意：instanceof 后面一定要是对象类型，并且大小写不能错，该方法适合一些条件选择或分支。
        ```

        ```
		alert(c.constructor === Array) ----------> true
        alert(d.constructor === Date) -----------> true
        alert(e.constructor === Function) -------> true
        注意： constructor 在类继承时会出错
        eg：
              function A(){};
              function B(){};
              A.prototype = new B(); //A继承自B
              var aObj = new A();
              alert(aobj.constructor === B) -----------> true;
              alert(aobj.constructor === A) -----------> false;
        而instanceof方法不会出现该问题，对象直接继承和间接继承的都会报true：
              alert(aobj instanceof B) ----------------> true;
              alert(aobj instanceof B) ----------------> true;
        言归正传，解决construtor的问题通常是让对象的constructor手动指向自己：
              aobj.constructor = A; //将自己的类赋值给对象的constructor属性
              alert(aobj.constructor === A) -----------> true;
              alert(aobj.constructor === B) -----------> false; //基类不会报true了;
		```

    3. jquery.type()

		```
		如果对象是undefined或null，则返回相应的“undefined”或“null”。
        jQuery.type( undefined ) === "undefined"
        jQuery.type() === "undefined"
        jQuery.type( window.notDefined ) === "undefined"
        jQuery.type( null ) === "null"
        如果对象有一个内部的[[Class]]和一个浏览器的内置对象的 [[Class]] 相同，我们返回相应的 [[Class]] 名字。 (有关此技术的更多细节。 )
        jQuery.type( true ) === "boolean"
        jQuery.type( 3 ) === "number"
        jQuery.type( "test" ) === "string"
        jQuery.type( function(){} ) === "function"
        jQuery.type( [] ) === "array"
        jQuery.type( new Date() ) === "date"
        jQuery.type( new Error() ) === "error" // as of jQuery 1.9
        jQuery.type( /test/ ) === "regexp"
        其他一切都将返回它的类型“object”。
		```

    4.  Object.prototype.toString.call();

53. jquery动画和css3的区别：css3是基于css的，不需要任何语言，效率高，但兼容性差，当有复杂事件且兼容性要求高的时候用jquery。

54. vue.js实现双向绑定的原理

	1. http://www.cnblogs.com/kidney/p/6052935.html?utm_source=gold_browser_extension
	2. http://www.jb51.net/article/99129.htm