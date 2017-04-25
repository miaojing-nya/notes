### 关于JavaScript的基本知识点
1. 一切变量，函数名和操作符都区分大小写。
2. 标识符：是指变量，函数，属性的名字，或者函数的参数，可以是一个或多个字符。

 	1. 其规则是：第一个字符必须是一个字母，下划线或一个美元符号，其他字母可以是字母，下划线，美元符号或数字，一般用驼峰大小写格式（即第一个字母小写，其余每个有意义的单词首字母大写，例doSomethingImportant）
 	2. 关键字，保留字，true，false和null不能用作标识符。

3. 注释：

    `//单行注释`

    ` /* 多行注释 */`

4. 语句：语句以分号结尾，无论是一条语句还是多条语句，一般使用代码块的形式{}
5. 变量：
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

6. 数据类型：Undefind,Null,Boolean,Number和String五种基本数据类型，Object（包括数组和函数）一种复杂数据类型。五种基本数据类型是原始值，不可更改，值相等时他们才相等，比较两个单独字符串时，当且仅当长度相等且每个索引的字符都等时，他们才等。对象是可变的，值是可修改的，对象即便包含同样属性和相同值，或是各个索引完全相等，那他们也不等。
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

7. 操作符：

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

8. 创建对象有几种方式？

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

9. JSON：作用，设计结构：json是一种轻量级的数据交换格式，体积小,传输快，主要用于传送数据；易于阅读和编写，同时也易于机器解析和生成；客户端操纵XML的时候需要创建ActiveX对象，JSON则完全就是一个JS对象，不需要创建DOM。

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

