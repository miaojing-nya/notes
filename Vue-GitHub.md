### 使用Vue.js从零构建GitHub项目浏览器
1. ==**++vue-cli的概念++**==：我们使用vue.js时虽然只是通过script标签引入vue.js就可以了，但是真正一个项目是需要用到很多的工具的，比如：模块化，预处理器，热模块加载(运行时动态注入修改内容，又不中断APP正常运行)，代码校验(保存时检查代码)和测试等等，所以vue-cli就是这样的一个工具，用简单的命令行来快速构建一个强大的Vue.js项目。
2. ==**++webpack的概念++**==：是一款模块加载器兼打包工具，能把各种资源，例如JS，样式，图片等都作为模块来使用和处理。
3. ==**++开发环境搭建++**==(vue-cli有五个模板，现用webpack-simple举例)：

    `npm install vue-cli -g     //insatll安装；-g是--全局global的缩写`

    发现报错“Error: EACCES: permission denied“,没有权限的意思，所以遇到该情况时都在前面加上sudo，变成超级管理员

    `sudo npm install vue-cli -g     //sudo可以查看隐藏的文件或文件夹`

    这时会出现paddword让你输入开机密码，然后等待安装
4. ==**++创建第一个Vue应用：++**==

	**重新编译是control加c；**

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

    **更改默认端口：**默认启动的端口为8080，端口容易冲突。修改配置文件package.json，更换端口为8090

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
