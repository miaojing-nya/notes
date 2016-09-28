# 一.DOM事件
#### A.表单事件：
###### 1.提交表单和重置表单时，会触发submit和reset事件。
###### 2.当用户和按钮（包括复选框）交互时，会发生click事件。
###### 3.输入文字，选择选项或选择复选框来改变相应表单状态时，会触发change事件。
###### 4.当得到和失去焦点时，分别触发focus和blur事件。
#### B.Window事件：
###### 1.load：当文档和其所有外部资源完全加载并显示给用户时触发。
###### 2.unload：当用户离开当前文档转向其他文档时触发。（可以保存用户的状态，但不能用于取消用户转向其他地方）
###### 3.beforeunload：能提供询问用户是否确定离开当前页面的机会。（若程序返回字符串，则在新页面加载前，字符串会出现在展示给用户确认的对话框上，用户则有机会取消跳转而留在当前页面）
###### 4.resize：用户调整浏览器窗口大小。
###### 5.scroll：滚动时触发。
#### C.鼠标事件：
###### 1.click：鼠标在元素上按下并释放时触发。
###### 2.dblclick：双击鼠标时触发。
###### 3.mousedown：鼠标指针移动到元素上并按下鼠标时，不需松开即可发生。
###### 4.mouseup：当在元素上放松鼠标按键时发生。
###### 5.mousemove：当鼠标指针在元素上移动时触发。
###### 6.mouseout：鼠标指针从元素上移开时触发。（无论鼠标指针离开备选元素还是任何子元素都会触发）
###### 7.mouseover：鼠标指针位于元素上时触发。（无论鼠标指针穿过位于备选元素还是任何子元素都会触发）
#### D.键盘事件：
###### 1.keyup：当按钮被松开时触发。
###### 2.keydown：键盘按下时触发。（捕获除了PrScrn外所有的按键）
###### 3.keypress：键盘按下时触发。（捕获数字，字母，读取字符）
#### E.冒泡事件:
在一个对象上触发某类事件，事件到达事件目标之后不会结束，会逐层向上冒泡，向这个对象的父级对象传播，从里到外，直至它被处理（父级对象所有同类事件都将被激活），直至document对象。
###### 1.作用：
1）事件冒泡允许多个操作被集中处理（把事件处理器添加到一个父级元素上，避免把事件处理器添加到多个子级元素上），它还可以让你在对象层的不同级别捕获事件。（ 集中处理的例子）

```html
<style>
#outSide{
    width:100px;
    height:100px;
    background:#000;
    padding:50px;
}
#inSide{
    width:100px;
    height:100px;
    background:#CCC;
}
</style>

<div onclick="eventHandle(event)" id="outSide">
  <div id="inSide"></div>
</div>

<script>
//本例子只在外面盒子定义了处理方法，而这个方法一样可以捕获到子元素点击行为并处理它。假设有成千上万子元素要处理，难道我们要为每个元素加“onclick="eventHandle(event)"”？显然没有这种集中处理的方法来的简单，同时它的性能也是更高的。
function eventHandle(e){
    var e=e||window.event;

    var obj=e.target||e.srcElement;

    alert(obj.id+' was click')
}
</script>

```

2）让不同的对象同时捕获同一事件，并调用自己的专属处理程序做自己的事情，就像老板一下命令，各自员工做自己岗位上的工作去了。（同时捕获同一事件的例子）

```html
<style>
#outSide{
	width:100px;
    height:100px;
    background:#000;
    padding:50px;
}
#inSide{
	width:100px;
    height:100px;
    background:#CCC;
}
</style>

<div onclick="outSideWork()" id="outSide">
	<div onclick="inSideWork()" id="inSide"></div>
</div>

<script type="text/javascript">
function outSideWork(){
    alert('My name is outSide,I was working...');
}

function inSideWork(){
    alert('My name is inSide,I was working...');
}

//因为下面程序自动激活单击事件，有些浏览器不允许，所以请单击灰色盒子，从这里开始下命令，这样因为冒泡的原因，黑色大盒子也会收到单击事件，并调用了自己的处理程序。如果还有更多盒子嵌套，一样道理。
/*
function bossOrder(){
  document.getElementById('inSide').click();
}
bossOrder();
*/
</script>

```
3）以下事件不冒泡：blur、focus、load、unload。
###### 2.阻止时间冒泡：

``` js
event.stopPropagation();
```
#### F.捕获事件:
与事件冒泡相反，事件会从最外层开始发生，直到最具体的元素。如果时间冒泡发生顺序是：p -> div -> body -> html -> document，那么事件捕获是：document -> html -> body -> div -> p
# 二.DOM属性
