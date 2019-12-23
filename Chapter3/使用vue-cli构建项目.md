# 第2节：使用vue-cli构建项目

使用命令行构建项目

```
vue init webpack 项目名
```

一系列配置后，构建完成。

再使用

```
npm run dev
```

启动项目



------



下面是 element UI 的引入：

需要先安装

```
npm install element-ui --save
```

然后在main.js文件中添加

```
import ElementUI from 'element-ui'
import 'element-ui/lib/theme-chalk/index.css'

Vue.use(ElementUI)
```

之后即可在具体的vue页面中使用。



------



如果想在全局引入css页面的话，可以在main.js中添加

```
import './assets/css/common.css' //自己的css文件
```

