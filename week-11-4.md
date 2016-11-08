### 周报 16-11-4
##### Vue.js实践操作案例总结
1. 需求：点击“查看详情”后跳转到地图页

    ```
	//第一步：新建一个rodemap文件夹，包括index.vue和index.js，然后在route.js页仿照其他格式配置路由
    const RouterConfig = {
      "/basic": {
        title: "填写基本信息",
        name: "view:service.basic",
        component(resolve){
          require(["./../pages/RequirementBasic"], resolve)
        }
      },
      "/roadmap":{
        title:"小型会务办公流程",
        name:"view:roadmap",
        component(resolve){
          require(["../pages/Roadmap"],resolve)
        }
      },
      "/copy/:id": {
        title: "填写基本信息",
        name: "view:copy.service.basic",
        component(resolve){
          require(["./../pages/RequirementBasic"], resolve)
        }
      }
    };
    ```

    ```
	//第二步：加v-link跳转链接,引入路径
    <div v-link="{path:'/rodemap'}">查看详情</div>
    ```

    ```
	//第三步：在rodemap文件夹下的index页面输入地图页面内容
    ```
2. 想要弹出数字键盘，则在类型加上number

	` label="人均预算" name="budget" type="number"`

3. 入住时间默认填写开始时间

	`:start-time.sync="data.start_time"`

	```
    //定义在ready（）{}里
    dataFormat.start_time = this.requirement.start_time;
    ```

4. 默认设施是投影仪，3000-5000流明 

	```
	export default [
      { value: "320", text: "其他" },
      { value: "313", text: "投影仪" },
      { value: "327", text: "电子指示屏" },
      { value: "322", text: "背景板" },
      { value: "326", text: "横幅" }
    ]

    export const projector = [
      "酒店内投影仪3000流明以下",
      "酒店内投影仪3000-5000流明",
      "酒店内投影5000流明以上",
      "外带投影仪3000流明以下",
      "外带投影仪3000-5000流明",
      "外带投影仪5000流明以上"
    ];
	```

	`dataFormat.item_id = "313";     //313是投影仪的值`

    ```
    //写在methods里：
	onTypeChange(data, index){
        try {
          if (data.item_id !== this.requirement.utility_detail[index].item_id) data.note = data.item_id.value == 313 ? this.projector[1] : ''
        } catch (e) {
          data.note = data.item_id.value == 313 ? this.projector[1] : ''
        }
      }
    ```

5. 值不等于1或者不等于2时，用&&，而不是||，且（）代表有运算顺序

	`v-if="data.type && (data.type.value != 1 && data.type.value != 2)"`

6. 给当前页面的body加背景色

    ```
	<script>
      export default {
        created() {
          document.body.classList.add('bg--body')
        },

        destroyed() {
          document.body.classList.remove('bg--body');
        }
      }
    </script>
	```

##### JavaScript实践操作案例总结
1. 引用方式：两种

   第一种：直接写在HTML的script标签里。

   第二种：通过script标签的src属性外部引用，通常放在/body后面。

2. 输出：

   `document.write("hello")     //结果：你好`

    ```
	<p id="name">你好</p>     //结果：改变文案内容
    <script>document.getElementByID("name").innerHTML="改变文案内容"</script>
	```

3. 语法：按照编写顺序依次执行；标识符；空格；代码换行；关键字；

4. 数组的写法：

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

5. 声明变量的方式和构造函数的方式：

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

6. 继承父类：

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

7. 覆写父类：

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

8. 调用父类：
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

9. 传递和调用参数：

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

10. 封装：对信息起到一个隐藏的作用：

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

11. 封装后如何对其进行引用

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

12. 通过对象赋值的方式进行继承：

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

13. 遍历：
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

14. 遍历的两种方式：

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

15. ++和--的区别：

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

16. 数字1-10求和：

	```
	var a = 0;
    for(var i=0;i<10;i++){
      a+=i;
    }
    console.log(a);
	```

17. 求6,56,888,77,5543,999的和：

	```
	var a = 0;
    var arry = [6,56,888,77,5543,999];
    for(var i=arry.length; i>=0;i--){
      a+=arry[i];
    }
    console.log(a);
	```
