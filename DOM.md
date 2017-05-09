### 一.DOM属性
属性是节点（HTML 元素）的值，您能够获取或设置。
##### A.HTML属性作为Element的属性：
1. a标签定义一个超链接，用href属性。
2. img标签查询一张图片url，用src属性。
3. form表单设置类型属性或值属性等。
4. 元素的class和id属性。
5. 规定样式的style属性。

##### B.获取和设置非标准HTML属性：
1. getAttribute():查询属性(不返回数值，布尔值或对象)。
2. setAttribute():设置属性。
3. hasAttribute():检测属性是否存在。
4. removeAttribute():完全删除属性。
  ``` js
  var image = document.images[0];
  var width = parseInt(image.getAttibute("width"));
  image.setAttribute("class","thumbnail");
  ```

##### C.数据集属性：
1. 在HTML5文档中，任意以data-为前缀的小写的属性名字都是合法的，这些数据集属性不会对元素表现产生影响。
2. HTML5还在Element对象上定义了dataset属性。该属性指代一个对象，它的各个属性对应去掉前缀的data-属性，所以dataset.x应保存data-x属性的指，带连字符的属性对应于驼峰命名法属性名：data-jquery-testx属性就变成dataset.jqueryTest属性。
3. dataset属性是元素的data-属性的实时，双向接口。设置或删除dataset的一个属性就等同于设置或移除对应元素的data-属性。

##### D.作为Attr节点的属性：
1. Node类型定义了attributes属性，针对非Element对象的任何节点，该属性为null。针对Element对象，该属性是只读的类数组对象，代表元素的所有属性。
2. 当索引attributes对象时得到的值是Attr对象，Attr对象一类特殊的Node，不像Node一样去用。
3. Attr的name和value属性返回该属性的名字和值。

  ``` js
  document.body.attributes[0]     //用数字索引访问：body元素的第一个属性
  document.body.attributes.bgcolor     //可以枚举元素的所有属性：body元素的bgcolor属性
  document.body.attributes["onload"]     //可以用属性名索引：body元素的onload属性
  ```

##### E.常用的一些属性：

1. childNodes：返回当前元素所有子元素的数组。
1. firstChild：返回当前元素的第一个下级子元素
1. lastChild：返回当前元素的最后一个子元素。
1. nextSibling：返回紧跟在当前元素后面的元素。
1. nodeValue：指定表示元素值的读/写属性。
1. parentNode：返回元素的父节点。
1. previousSibling：返回紧邻当前元素之前的元素。

### 二.DOM方法
方法是我们可以在HTML元素上执行的动作。
##### 常用方法：
1. getElementById()：获取有指定惟一ID属性值文档中的元素素。

  ``` js
  var element=document.getElementById("intro");     //获取id值为intro的元素
  ```

1. getElementsByTagName()：返回包含带有指定标签名称的所有元素的节点列表（集合/节点数组）。
1. appendChild()：把新的子节点添加到指定节点。
1. removeChild()：删除子节点。
1. replaceChild()：替换子节点。
1. insertBefore()：在指定的子节点前面插入新的子节点。
1. createAttribute()：创建属性节点。
1. createElement()：创建元素节点。
1. createTextNode()：创建文本节点。
1. getAttribute()：返回指定的属性值。
1. setAttribute()：把指定属性设置或修改为指定的值。
1. createElement(tagName)：文档对象上的createElement方法可以创建由tagName指定的元素。如果以串div作为方法参数，就会生成一个div元素。
1. createTextNode(text) 文档对象的createTextNode方法会创建一个包含静态文本的节点。
1. insertBefore(newNode, targetNode)将节点newNode作为当前元素的子节点插到targetNode元素前面。
1. removeChild(childNode) 这个方法从元素中删除子元素childNode。
1. replaceChild(newNode, oldNode) 这个方法将节点oldNode替换为节点newNode。
1. hasChildnodes() 这个方法返回一个布尔值，指示元素是否有子元素。

### 三.DOM事件
##### A.表单事件：
1. 提交表单和重置表单时，会触发submit和reset事件。
1. 当用户和按钮（包括复选框）交互时，会发生click事件。
1. 输入文字，选择选项或选择复选框来改变相应表单状态时，会触发change事件。
1. 当得到和失去焦点时，分别触发focus和blur事件。

##### B.Window事件：
1. load：当文档和其所有外部资源完全加载并显示给用户时触发。
1. unload：当用户离开当前文档转向其他文档时触发。（可以保存用户的状态，但不能用于取消用户转向其他地方）
1. beforeunload：能提供询问用户是否确定离开当前页面的机会。（若程序返回字符串，则在新页面加载前，字符串会出现在展示给用户确认的对话框上，用户则有机会取消跳转而留在当前页面）
1. resize：用户调整浏览器窗口大小。
1. scroll：滚动时触发。

##### C.鼠标事件：
1. click：鼠标在元素上按下并释放时触发。
1. dblclick：双击鼠标时触发。
1. mousedown：鼠标指针移动到元素上并按下鼠标时，不需松开即可发生。
1. mouseup：当在元素上放松鼠标按键时发生。
1. mousemove：当鼠标指针在元素上移动时触发。
1. mouseout：鼠标指针从元素上移开时触发。（无论鼠标指针离开备选元素还是任何子元素都会触发）
1. mouseover：鼠标指针位于元素上时触发。（无论鼠标指针穿过位于备选元素还是任何子元素都会触发）

##### D.键盘事件：
1. keyup：当按钮被松开时触发。
1. keydown：键盘按下时触发。（捕获除了PrScrn外所有的按键）
1. keypress：键盘按下时触发。（捕获数字，字母，读取字符）

##### E.冒泡事件:
1. getElementsByTagName()：返回包含带有指定标签名称的所有元素的节点列表（集合/节点数组）。
1. getElementsByClassName()：返回包含带有指定类名的所有元素的节点列表。
1. appendChild()：把新的子节点添加到指定节点。
1. removeChild()：删除子节点。
1. replaceChild()：替换子节点。
1. insertBefore()：在指定的子节点前面插入新的子节点。
1. createAttribute()：创建属性节点。
1. createTextNode()：创建文本节点。
1. getAttribute()：返回指定的属性值。
1. setAttribute()：把指定属性设置或修改为指定的值。
1. createElement(tagName)：文档对象上的createElement方法可以创建由tagName指定的元素。如果以串div作为方法参数，就会生成一个div元素。
1. createTextNode(text) 文档对象的createTextNode方法会创建一个包含静态文本的节点。
1. insertBefore(newNode, targetNode)将节点newNode作为当前元素的子节点插到targetNode元素前面。
1. removeChild(childNode) 这个方法从元素中删除子元素childNode。
1. replaceChild(newNode, oldNode) 这个方法将节点oldNode替18. hasChildnodes() 这个方法返回一个布尔值，指示元素是否有子元素。

##### 作用：
1. 事件冒泡允许多个操作被集中处理（把事件处理器添加到一个父级元素上，避免把事件处理器添加到多个子级元素上），它还可以让你在对象层的不同级别捕获事件。（ 集中处理的例子）
1. 以下事件不冒泡：blur、focus、load、unload。
1. 阻止时间冒泡：
  ```
  event.stopPropagation();     //事件冒泡
  ```

  ```
  event.preventDefault();     //事件捕获
  ```

##### F.捕获事件:
  与事件冒泡相反，事件会从最外层开始发生，直到最具体的元素。如果时间冒泡发生顺序是：p -> div -> body -> html -> document，那么事件捕获是：document -> html -> body -> div -> p

##### G.怎样添加、移除、移动、复制、创建和查找节点

[http://blog.csdn.net/qi1271199790/article/details/53869508](http://)

