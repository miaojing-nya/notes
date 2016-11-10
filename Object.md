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

    2.reverse():末尾追加元素

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