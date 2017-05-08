### HTML+CSS

##### 1. HTML常用标签

块元素：div，ul，dl，ol，form，h1~h6，p，table

1. 总是在新行上开始；
2. 高度，行高以及外边距和内边距都可设置；
3. 宽度缺省是它的容器的100%，除非设定一个宽度；
4. 它可以容纳内联元素和其他块元素；

内联元素：span，a，img，input，label，textarea，b，em，i

1. 和其他元素都在一行上；
2. 高，行高及外边距和内边距不可改变；
3. 宽度就是它的文字或图片的宽度，不可改变；
4. 内联元素只能容纳文本或者其他内联元素；

##### 2. HTML语义化

1. 用正确的标签做正确的事情；
2. 让页面的内容结构化，便于对浏览器、搜索引擎解析；
3. 在没有样式CCS情况下也以一种文档格式显示，并且是容易阅读的；
4. 搜索引擎的爬虫依赖于标记来确定上下文和各个关键字的权重，利于 SEO；
5. 使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。

##### 3. DOCTYPE，什么是严格模式与混杂模式？

DOCTYPE是文档类型，一个文档类型标记是一种标准通用标记语言的**文档类型声明**，它的目的是要告诉标准通用标记语言解析器，它应该使用什么样的文档类型定义（DTD）来解析文档。Doctype还会对浏览器的渲染模式产生影响，不同的渲染模式会影响到浏览器对于 CSS 代码甚至 JavaScript 脚本的解析，所以Doctype是非常关键的，尤其是在 IE 系列浏览器中，由DOCTYPE 所决定的 HTML 页面的渲染模式至关重要。

1. 严格模式：让IE的行为更接近标准行为

	`<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"> `

2. 过渡模式(混杂模式)：混杂模式是一种比较宽松的向后兼容的模式。混杂模式通常模拟老式浏览器的行为，以防止老站点无法工作

	`<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  `

3. 两种模式间的差异
对于这两种模式之间的差异，最显著的一个例子与Windows上IE专有的盒模型有关。在IE 6出现时，在标准模式中使用的是正确的盒模型，在混杂模式中使用的则是老式的专有盒模型。为了维持对IE 5和更低版本的向后兼容性，Opera 7和更高版本也在混杂模式中使用有缺点的IE盒模型。
呈现方面的其他差异比较小，而且是与特定浏览器相关的，包括对于十六进制颜色值不需要#号、假设CSS中没有指定单位的长度的单位是像素，以及在使用关键字时将字号增加一级。

##### 4. 理解DOM结构

Document Object Module, 文档对象模型。我们通过JavaScript操作页面的元素，进行添加、移动、改变或移除的方法和属性, 都是DOM提供的。

一. 标准：W3C DOM 标准被分为 3 个不同的部分

1. 核心 DOM - 针对任何结构化文档的标准模型
2. XML DOM - 针对 XML 文档的标准模型
3. HTML DOM - 针对 HTML 文档的标准模型

二. 节点：HTML 文档中的所有内容都是节点

1. 整个文档是一个文档节点
2. 每个 HTML 元素是元素节点
3. HTML 元素内的文本是文本节点
4. 每个 HTML 属性是属性节点
5. 注释是注释节点

三. 节点的关系：父（parent）、子（child）和同胞（sibling）等术语用于描述这些关系，父节点拥有子节点，同级的子节点被称为同胞（兄弟或姐妹）:

1. 在节点树中，顶端节点被称为根（root）
2. 每个节点都有父节点、除了根（它没有父节点）
3. 一个节点可拥有任意数量的子
4. 同胞是拥有相同父节点的节点

##### 5. HTML5新增内容

1. 文件类型声明（<!DOCTYPE>）仅有一型：<!DOCTYPE HTML>。
2. 新的解析顺序：不再基于SGML(是一种定义电子文档结构和描述其内容的国际标准语言)。
3. 新的元素：section, video, progress, nav, meter, time, aside, canvas, command, datalist, details, embed, figcaption, figure, footer, header, hgroup, keygen, mark, output, rp, rt, ruby, source, summary, wbr。
4. input元素的新类型：date, email, url等等。
5. 新的属性：ping（用于a与area）, charset（用于meta）, async（用于script）。
6. 全域属性：id, tabindex, repeat。
7. 新的全域属性：contenteditable, contextmenu, draggable, dropzone, hidden, spellcheck。
8. 移除元素：acronym, applet, basefont, big, center, dir, font, frame, frameset, isindex, noframes, strike, tt。

##### 6. 盒模型(box-sizing)

想象成一个盒子，它有四个属性：外边距（margin）、边框（border）、内边距（padding）、内容（content）。ie低于版本8的浏览器的盒子模型中的width包括内边距和边框。

1. 盒模型默认的值是content-box

   `Width = width + padding-left + padding-right + border-left + border-right`

   `Height = height + padding-top + padding-bottom + border-top + border-bottom`

2. border-box

   `Width = width(包含padding-left + padding-right + border-left + border-right)`

   `Height = height(包含padding-top + padding-bottom + border-top + border-bottom)`

3. padding-box

   `Width = width(包含padding-left + padding-right) + border-top + border-bottom`

   `Height = height(包含padding-top + padding-bottom) + border-top + border-bottom`

4. margin叠加：只有块元素的垂直外边距才会发生外边距叠加。行内框、浮动框或绝对定位框之间的外边距不会叠加。折叠结果遵循下列计算规则：
   1. 两个相邻的外边距都是正数时，折叠结果是它们两者之间较大的值。
   2. 两个相邻的外边距都是负数时，折叠结果是两者绝对值的较大值。
   3. 两个外边距一正一负时，折叠结果是两者的相加的和。

##### 7. CSS定位方式

1. display属性：block，inline和inline-block，不常用的是table-cell(标签元素以表格单元格的形式呈现)。
2. position属性：relative，absolute，fixed(固定定位)设置了固定定位之后，元素相对的偏移的参考是可视窗口，即使页面滚动，元素仍然会在固定位置。

##### 8. 书写顺序

1. 位置属性(position, top, right, z-index, display, float等)
2. 大小(width, height, padding, margin)
3. 文字系列(font, line-height, letter-spacing, color- text-align等)
4. 背景(background, border等)
5. 其他(animation, transition等)

##### 9. div+css的布局较table布局有什么优点？

1. table布局：布局快，兼容性好，但改动不便。
2. div+css布局：布局灵活，改动方便，但兼容性较差，更符w3c标准，html和css分开存储，有利于搜索排名提升。
3. 常用的几种方式布局：float浮动布局；position属性+display属性；响应式布局flex;设为Flex布局以后，子元素的float、clear和vertical-align属性将失效ie10+。

##### 10. strong：粗体，多用于文本；em：斜体；b：粗体，多用于标题

##### 11. 渐进增强和优雅降级

1. 渐进增强：保证低版本的基本功能，再针对高级浏览器更好的体验。
2. 优雅降级：保证完整功能的同时，再针对低版本进行兼容。

##### 12. CSS选择器权重，即优先级

1. 解析顺序：从右到左进行查找。
2. 选择器权重(优先级)：内联样式（标签内style形式） > style标签 > link标签，凡是属性值后加上了!important，则优先级最高，不可被替代。
3. 权重的计算：id选择器 > 类，属性选择器和伪类选择器 > 元素和伪元素
4. id选择器（#ID），类选择器（.className），属性选择器（input[type="button"]），伪类选择器（:first-child），元素选择器（p），伪元素选择器（:before）

##### 13. CSS3新增特性

1. @Font-face特性：加载字体样式，而且它还能够加载服务器端的字体文件，让客户端显示客户端所没有安装的字体。
2. CSS3的渐变效果，CSS3的阴影，
3. Transforms：指拉伸，压缩，旋转，偏移等等一些图形学里面的基本变换。
4. Animation动画

##### 14. src和href的区别

1. src：引入，表示来源地址，img，script等。
2. href：引用，表示超文本，link，a等

##### 15. 有哪项方式可以对一个DOM设置它的CSS样式？

1. 外部样式表，引入一个外部css文件
2. 内部样式表，将css代码放在head标签内部
3. 内联样式，将css样式直接定义在 HTML 元素内部
4. 除了css以外，还可以用jq或是原生js，例如：
`$("div").css("color","#FF0000");`
`obj.style.display="none";`

##### 16. CSS中可以通过哪些属性定义，使得一个DOM元素不显示在浏览器可视范围内？

1. display:none隐藏对应的元素但不挤占该元素原来的空间，即HTML元素（对象）的宽度、高度等各种属性值都将“丢失”;。
2. visibility:hidden隐藏对应的元素并且挤占该元素原来的空间，即HTML元素（对象）仅仅是在视觉上看不见（完全透明），而它所占据的空间位置仍然存在。

##### 17. 超链接访问过后hover样式就不出现的问题是什么？如何解决？

原因是将a:hover和a:visited的顺序放错了，关于a标签的四种状态排序问题，有个简单好记的原则，叫做love hate原则，即l（link）ov（visited）e h（hover）a（active）te。

##### 18. px和em的区别

em它会继承父级元素的字体大小，因此并不是一个固定的值。1em=16px。

##### 19. 描述一个”reset”的CSS文件并如何使用它，与normalize.css有什么不同之处？

1. reset：重置浏览器的css默认属性，浏览器的品种不同，样式不同，然后重置，让他们统一。可以直接在style标签里重置，也可以link标签引用css。例如：`*{padding:0;margin:0;}`等等。
2. Normalize：相比于传统的CSS reset，Normalize.css是一种现代的、为HTML5准备的优质替代方案。Normalize.css支持包括手机浏览器在内的超多浏览器，同时对HTML5元素、排版、列表、嵌入的内容、表单和表格都进行了一般化，保护有用的浏览器默认样式而不是完全去掉它们。

##### 20. 什么是hack技术

为了解决IE浏览器6，7，8兼容的一种方式。

```
.box{
    background-color:#f1ee18;/*所有识别*/
    .background-color:#00deff\9; /*IE6、7、8识别*/
    +background-color:#a200ff;/*IE6、7识别*/
    _background-color:#1e0bd1;/*IE6识别*/
}
```

##### 21. rgba()和opacity的区别

rgba()和opacity都能实现透明效果，但最大的不同是opacity作用于元素，以及元素内的所有内容的透明度，而rgba()只作用于元素的颜色或其背景色。（设置rgba透明的元素的子元素不会继承透明效果！）

##### 22. css中可以让文字在垂直和水平方向上重叠的两个属性是什么？

1. 垂直方向：line-height
2. 水平方向：letter-spacing（可以用于消除inline-block元素间的换行符空格间隙问题。）

##### 23. 知道的网页制作会用到的图片格式有哪些？

png-8，png-24，jpeg，gif，svg，WebP

##### 24. 一次js请求一般情况下有哪些地方会有缓存处理？

dns缓存，cdn缓存，浏览器缓存，服务器缓存。

##### 25. 一个页面上有大量的图片（大型电商网站），加载很慢，你有哪些方法优化这些图片的加载，给用户更好的体验。

1. 图片懒加载，在页面上的未可视区域可以添加一个滚动条事件，判断图片位置与浏览器顶端的距离与页面的距离，如果前者小于后者，优先加载。
2. 如果为幻灯片、相册等，可以使用图片预加载技术，将当前展示图片的前一张和后一张优先下载。
3. 如果图片为css图片，可以使用CSSsprite，SVGsprite，Iconfont、Base64等技术。
4. 如果图片过大，可以使用特殊编码的图片，加载时会先加载一张压缩的特别厉害的缩略图，以提高用户体验。
5. 如果图片展示区域小于图片的真实大小，则因在服务器端根据业务需要先行进行图片压缩，图片压缩后大小与展示一致。

##### 26. 如何垂直居中一个img?

```
img
{
    display:table-cell;
    text-align:center;
    vertical-align:middle;
}
```

##### 27. 为什么利用多个域名来存储网站资源会更有效？

1. CDN缓存更方便
2. 突破浏览器并发限制
3. 节约cookie带宽
4. 节约主域名的连接数，优化页面响应速度
5. 防止不必要的安全问题

##### 28. 描述一下cookies，sessionStorage和localStorage的区别？

1. cookies：数据的生命期一般由服务器生成，可设置失效时间。如果在浏览器端生成Cookie，默认是关闭浏览器后失效；存放数据大小4K左右；与服务器端通信：每次都会携带在HTTP头中，如果使用cookie保存过多数据会带来性能问题；易用性：需要程序员自己封装，源生的Cookie接口不友好。
2. localStorage和sessionStorage：存放数据大小：一般为5MB；与服务器端通信：仅在客户端（即浏览器）中保存，不参与和服务器的通信；易用性：源生接口可以接受，亦可再次封装来对Object和Array有更好的支持；但是数据的生命期：localStorage除非被清除，否则永久保存，sessionStorage仅在当前会话下有效，关闭页面或浏览器后被清除

##### 29. XMLHttpRequest，怎样完整地执行一次GET请求、怎样检测错误

当页面全部加载完毕后，客户端通过该对象向服务器请求数据，服务器端接受数据并处理后，向客户端反馈数据。XMLHttpRequest 对象提供了在网页加载后与服务器进行通信的方法。

```
<script type="text/javascript">
    var xmlhttp;
    function loadXMLDoc(url){
        xmlhttp = null;
        if(window.XMLHttpRequest){    //code for all new browsers
            xmlhttp=newXMLHttpRequest();
        }elseif(window.ActiveXObject){    //code for IE5 and IE6
            xmlhttp=newActiveXObject("Microsoft.XMLHTTP");
        }
        if(xmlhttp!=null){
            xmlhttp.onreadystatechange=state_Change;
               xmlhttp.open("GET",url,true);
            xmlhttp.send(null);
        }else{
            alert("Your browser does not support XMLHTTP.");
        }
}

function state_Change(){
    if(xmlhttp.readyState==4){    //4 = "loaded"
        if(xmlhttp.status==200){    //200 = OK
            //...our code here...
        }else{
            alert("Problem retrieving XML data");
        }
    }
}
</script>
```

##### 30. audio和video的支持格式

audio是音频，支持mp3 4 wmv等，video标签才支持视频，mp4 flv webm ogv mpg等。

##### 31.对Web标准的理解

web标准简单来说可以分为结构(html)、表现(css)和行为(js)。web标准一般是将该三部分独立分开，使其更具有模块化。对于结构要求：（标签规范可以提高搜索引擎对页面的抓取效率，对SEO很有帮助），对于css和js来说，尽量使用外链css样式表和js脚本，样式尽量少用行间样式表，使结构与表现分离，标签的id和class等属性命名要做到见文知义，标签越少，加载越快，用户体验提高，代码维护简单，便于改版。

##### 32.浏览器内核差异

1. 浏览器可以分为两部分，shell+内核。其中shell的种类相对比较多，内核则比较少。Shell是指浏览器的外壳：例如菜单，工具栏等。主要是提供给用户界面操作，参数设置等等。它是调用内核来实现各种功能的。内核才是浏览器的核心。内核是基于标记语言显示内容的程序或模块。它主要的功能是解释网页中的语法并渲染网页。所以渲染引擎决定了浏览器如何显示网页内容以及页面的格式信息。不同的浏览器内核对网页语法的解释不尽相同，这就导致了不同浏览器渲染出的网页可能有一些差异。

2. 目前主流的浏览器有IE、Mozilla、FireFox、Opera、Safari、Chrome、Netscape等。

3. Tridend内核：它就是IE的核心引擎，代表：搜狗、360、遨游、世界之窗。Gecko内核代表：这个是火狐firefox御用内核，Webkit内核代表：苹果Safari浏览器的和google的浏览器使用的是该内核，它的优点是快速解析javascript

##### 33.浮动元素：怎么使用它们、它们有什么问题以及怎么解决这些问题？

1. float:left;左浮动，float:right;右浮动

2. 父元素的高度无法被撑开，影响与父元素同级的元素；与浮动元素同级的非浮动元素会跟随其后；若非第一个元素浮动，则该元素之前的元素也需要浮动，否则会影响页面显示的结构

3. 使用CSS中的clear:both;属性来清除元素的浮动可解决2、3问题，对于问题1，添加如下样式，给父元素添加clearfix样式：

	`.clearfix:after{content: ".";display: block;height: 0;clear: both;visibility: hidden;}`

    `.clearfix{display: inline-block;}  /* for IE/Mac */`

##### 34.HTML5，XHTML之间有什么区别？
个人理解：xhtml是HTML的规范版，XHTML 元素必须被正确地嵌套；XHTML 元素必须被关闭；标签名必须用小写字母；XHTML 文档必须拥有根元素。所以也严重制约其发展的问题，使其应用不广泛。

##### 35.元素居中的方式

1. 水平居中的text-align:center 和 margin:0 auto，这两种方法都是用来水平居中的，垂直居中是line-height

2. 已知元素宽高时，top:50%;left:50%以及margin-top:一半的height值的的负数;margin- left:一半的weight值的负数。

3. 未知元素宽高时（只支持IE9+的浏览器），position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);

4. position:absolute;left:0;right:0;top:0;bottom:0;margin:auto;（不支持IE7以下的浏览器）

5.js的方式：

	```
	var div = document.getElementById('box');
	var clientW = document.documentElement.clientWidth;
	var clientH = document.documentElement.clientHeight;
	var iW = div.offsetWidth;
	var iH = div.offsetHeight;

	div.style.left = (clientW - iW)/2+'px';
	div.style.top = (clientH- iH)/2+'px';
	```


