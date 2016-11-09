### 使用Vue.js从零构建GitHub项目浏览器
1. vue-cli的概念：我们使用vue.js时虽然只是通过script标签引入vue.js就可以了，但是真正一个项目是需要用到很多的工具的，比如：模块化，预处理器，热模块加载(运行时动态注入修改内容，又不中断APP正常运行)，代码校验(保存时检查代码)和测试等等，所以vue-cli就是这样的一个工具，用简单的命令行来快速构建一个强大的Vue.js项目。
2. webpack的概念：是一款模块加载器兼打包工具，能把各种资源，例如JS，样式，图片等都作为模块来使用和处理。
3. 开发环境搭建(vue-cli有五个模板，现用webpack-simple举例)：

    `npm install vue-cli -g     //insatll安装；-g是--全局global的缩写`

    发现报错“Error: EACCES: permission denied“,没有权限的意思，所以遇到该情况时都在前面加上sudo，变成超级管理员

    `sudo npm install vue-cli -g     //sudo可以查看隐藏的文件或文件夹`

    这时会出现paddword让你输入开机密码，然后等待安装。
4. 创建第一个Vue应用：

   重新编译是control加c；

    `vue init webpack-simple github-file-explorer`

    `//init初始化；webpack-simple模板；github-file-explorer项目名`

    回车后会出现Project name，让你输入项目名称，起个名字，但是不可以大写和-，可以使用下划线。

    `Project description     //项目描述`

    `Author     //作者`

    `ls 回车     //可以查看下目录`

    `cd github-file-explorer     //然后找到所在目录`

    `npm insatll     //下载一个叫node_modules的文件夹，任何时候都不需要上传的`

    `npm run dev`

    这样浏览器就自动打开了http://localhost:8080的页面。

5. 项目结构：如下图

6. 更改默认端口：默认启动的端口为8080，端口容易冲突。修改配置文件package.json，更换端口为8090。

    我们先看下package.json页面的代码：

    ```
	{
      "name": "vue_github",     //Project name
      "description": "simple",     //Project description
      "author": "nya",     //Author
      "private": true,
      "scripts": {
        "dev": "cross-env NODE_ENV=development webpack-dev-server --open --inline --hot",     //npm run dev其实跑的就是这段--open打开--hot自动加载
        "build": "cross-env NODE_ENV=production webpack --progress --hide-modules"
      },
    }

   ```

    `cross-env NODE_ENV=development webpack-dev-server --open --inline --hot --port 8090`

    `可以在后面加--port端口，但是要重新跑下npm run dev,那么浏览器就自动打开了http://localhost:8090的页面`

7. 热重载：就是不用再按F5来手动刷新，它会自动加载浏览器，保存秒级更新。

8. 引入资源：在index.html中引入资源，采用jsdelivr CDN加速。

	`<!-- Bootstrap -->`

    `<link rel="stylesheet" href="https://cdn.jsdelivr.net/bootstrap/3.3.6/css/bootstrap.min.css">`

    `<!-- Octicons -->`

    `<link rel="stylesheet" href="https://cdn.jsdelivr.net/octicons/3.5.0/octicons.css"> `

   1. CDN:是一个服务端的静态资源加速服务，每一次都不会访问真实的静态资源，访问专门的cdn服务器，然后资源就会缓存，解决 Internet网络拥挤的状况，降低流量，提高用户访问速率

   2. jsdelivr:是一个开源的CDN解决方案，用于帮助开发者和站长。包含JavaScript插件，CSS框架，字体等Web上常用的静态资源。

9. 常用的简单Vue指令：

   1. v-model：表单控件绑定。用于创建双向绑定

	```
	<span>Message is: {{ message }}</span>
	<br>
	<input type="text" v-model="message" placeholder="edit me">
    //结果：span里自动更新input输入的内容
	```

   2. v-if 根据表达式的值的真假条件渲染元素。
   3. v-for 列表渲染。将元素或模板块重复数次，遍历用到v-for。特定语法是：

	```
	<ul id="example-1">
      <li v-for="item in items">
        {{ item.message }}
      </li>
    </ul>
	```

	```
	var example1 = new Vue({
      el: '#example-1',
      data: {
        items: [
          { message: 'Foo' },
          { message: 'Bar' }
        ]
      }
    })
	```

   4. @click 是v-on:click的简写，绑定事件监听。

	```
	<div id="example">
      <button v-on:click="greet">Greet</button>
    </div>
	```

    ```
	var vm = new Vue({
      el: '#example',
      data: {
        name: 'Vue.js'
      },
      // 在 `methods` 对象中定义方法
      methods: {
        greet: function (event) {
          // 方法内 `this` 指向 vm
          alert('Hello ' + this.name + '!')
          // `event` 是原生 DOM 事件
          alert(event.target.tagName)
        }
      }
    })

    // 也可以在 JavaScript 代码中调用方法
    vm.greet() // -> 'Hello Vue.js!'
	```

10. 计算属性：computed

	`{{fullName}}`

    ```
	data () {
      return {
        firstName: 'John',
        lastName: 'Smith',
      }
   }
	```

    ```
	computed: {
      fullName() {
        return (this.firstName + ' ' + this.lastName);
      }
    },
	```

11. 组件：components

	`import Hello from './components/globle.vue';`

    `components: {Hello}`

12. :class=“”可以加值，加函数，加任何，比如：两种写法

	```
	<input type="text" v-model="content" :class="{ 'border-none': content=='', 'border-red': content!='' }">
	```

    ```
	<input type="text" v-model="content" :class="element()">

    element: function () {
        if(this.content==''){
          return;
        }else{
          return "border-red";
        }
      }
	```

13. 实际操作代码：如下图
