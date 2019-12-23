# 第3节：如何使用mockjs模拟数据

首先需要先安装mockjs和axios。可以通过node直接安装

```
npm install mockjs --save
```

```
npm install axios --save
```

安装完后，可以在src目录下新建mock.js文件，可以单建一个文件，也可以建文件夹后再新建，看个人习惯。

之后在mock.js文件中键入代码：

```
import { Random as _Random, mock } from 'mockjs' // 获取mock对象
const Random = _Random // 获取random对象，随机生成各种数据，具体请翻阅文档
const domain = 'http://mockjs.com/api' // 定义默认域名，随便写
const code = 200 // 返回的状态码

// 随机生成文章数据
const postData = req => {
  // console.log(req) // 请求体，用于获取参数

  //  courserecommendList
  let courserecommendList = [] // 用于存放课程数据的数组
  let courserecommendTabList = []

  for (let i = 0; i < 7; i++) {
    let post = {
      title: Random.csentence(8, 16),
      img: Random.dataImage('375x208', '课程封面'),
      schoolico: Random.dataImage('100x100', '学校logo'),
      schoolname: Random.cname(),
      visits: Random.natural(10000, 10000000),
      desc: Random.csentence(10, 25),
      courseUrl: Random.url()
    }

    courserecommendList.push(post)
  }
  for (let j = 0; j < 7; j++) {
    let post = {
      title: Random.csentence(12, 20),
      img: Random.dataImage('375x208', '课程封面'),
      schoolico: Random.dataImage('100x100', '学校logo'),
      schoolname: Random.cname(),
      visits: Random.natural(10000, 10000000),
      desc: Random.sentence(10, 25),
      courseUrl: Random.url()
    }

    courserecommendTabList.push(post)
  }

  // 返回状态码和文章数据posts
  return {
    code,
    courserecommendList,
    courserecommendTabList
  }
}

// 定义请求链接，类型，还有返回数据
mock(`${domain}/gets/course`, 'get', postData)

//  post data
let mycourse = [] // 用于存放文章数据的数组

for (let i = 0; i < 10; i++) {
  let post = {
    title: Random.csentence(10, 25), // 随机生成长度为10-25的标题
    icon: Random.dataImage('300x250', '课程封面'), // 随机生成大小为250x250的图片链接
    author: Random.cname(), // 随机生成名字
    date: Random.date() + ' ' + Random.time(), // 随机生成年月日 + 时间
    courseid: Random.natural(10000, 10000000), // 随机生成一个课程编号，长度在5位数到9位数之间
    courseUrl: Random.url()
  }

  mycourse.push(post)
}
let allcourse = [] // 用于存放文章数据的数组

for (let i = 0; i < 10; i++) {
  let post = {
    title: Random.csentence(10, 25), // 随机生成长度为10-25的标题
    icon: Random.dataImage('300x250', '课程封面'), // 随机生成大小为250x250的图片链接
    author: Random.cname(), // 随机生成名字
    date: Random.date() + ' ' + Random.time(), // 随机生成年月日 + 时间
    courseid: Random.natural(10000, 10000000), // 随机生成一个课程编号，长度在5位数到9位数之间
    courseUrl: Random.url()
  }

  allcourse.push(post)
}
mock(`${domain}/posts/search`, 'post', {// 这里的url地址其实可以换成一个字段，比如msg,下边请求时候对应就可以
  mycourse,
  allcourse
})

```

上面是一个大概的例子，这是我的项目中新建的mock数据，然后在main.js中引入：

```
import mock from './mock/mock' // 刚刚手写的mock.js文件
import axios from 'axios' // axios http请求库

axios.defaults.baseURL = 'http://mockjs.com/api' // 设置默认请求的url
Vue.prototype.$http = axios
```

最后，就是在具体的vue文件中调用了，直接写在mounted方法中：

```
this.$http.get('/gets/course').then(res => {
      this.courserecommendList = res.data.courserecommendList
      this.courserecommendTabList = res.data.courserecommendTabList
    })
```

mock就是这样使用的，下面是mock的文档介绍，具体使用时可以查阅：

[https://github.com/nuysoft/Mock/wiki/]

