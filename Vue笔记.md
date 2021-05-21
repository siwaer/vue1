#                                 Vue.js

## 计时器

```js
<body>
    <div id = "app">
           <h2>当前计数：{{counter}}</h2>
           <button v-on:click="add">+</button>
           <button v-on:click="sub">-</button>
    </div>
    <script src="../vue.js"></script>
    <script>
     const app = new Vue({
         el:'#app',
         data:{
             counter:0
         },
         methods:{
             add:function(){
               this.counter++
             },
             sub:function(){
                this.counter--
             }
         }
     })
    </script>
```

## 计算属性:computed

```js
<body>
    <div id="app">
        <h2>{{TotalPrice}}</h2>
    </div>
    <script src="../vue.js"></script>
    <script>
        const app = new Vue({
            el: '#app',
            data: {
                books: [{
                    id: 001,
                    name: 'unix编程艺术',
                    price: 119
                }, {
                    id: 002,
                    name: 'unix编程艺术',
                    price: 105
                }, {
                    id: 003,
                    name: 'unix编程艺术',
                    price: 98
                }, {
                    id: 004,
                    name: 'unix编程艺术',
                    price: 90
                }, ]
            },
            computed: {
                TotalPrice: function() {
                    let result = 0
                    for (let i = 0; i < this.books.length; i++) {
                        result += this.books[i].price
                    }
                    return result
                }
            }
        })
    </script>
</body>
```

## 登录切换案例

```js
<body>
    <div id="app">
        <span v-if="isuser">
        <label for="username">用户账号</label>
        <input type="text" id="username" placeholder="用户帐号" key="username">
        </span>
        <span v-else>
            <label for="email">用户邮箱</label>
            <input type="text" id="email" placeholder="用户邮箱" key="email">
        </span>
        <button @click="isuser=!isuser">切换类型</button>
    </div>
    </div>
    <script src="../vue.js"></script>
    <script>
        const app = new Vue({
            el: '#app',
            data: {
                isuser: true
            }
        })
    </script>
</body>

```

## 书籍表单

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="style.css">
</head>

<body>
    <div id="app">
        <div v-if="books.length">
            <table>
                <thead>
                    <tr>
                        <th></th>
                        <th>书籍名称</th>
                        <th>出版日期</th>
                        <th>价格</th>
                        <th>购买数量</th>
                        <th>操作</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(item,index) in books">
                        <td>{{item.id}}</td>
                        <td>{{item.name}}</td>
                        <td>{{item.data}}</td>
                        <td>{{item.price | showPrice}}</td>
                        <td>
                            <button @click='sub(index)' v-bind:disabled="item.count<=1">-</button> {{item.count}}
                            <button @click='add(index)'>+</button>
                        </td>
                        <td><button @click="remove">移除</button></td>
                    </tr>
                </tbody>
            </table>
            <h2>总价格:{{totalprice}}</h2>
        </div>
        <h2 v-else>购物车为空</h2>
    </div>
    <script src="../vue.js"></script>
    <script src="main.js"></script>
</body>

</html>
```



```js
//main.js模块
const app = new Vue({
    el: '#app',
    data: {
        books: [{
                id: 1,
                name: '《算法导论》',
                data: '2006-9',
                price: 85.00,
                count: 1
            },
            {
                id: 2,
                name: '《unix编程艺术》',
                data: '2006-2',
                price: 59.00,
                count: 1
            },
            {
                id: 3,
                name: '《编程珠玑》',
                data: '2006-7',
                price: 39.00,
                count: 1
            },
            {
                id: 4,
                name: '《JAVA EE》',
                data: '2006-5',
                price: 78.00,
                count: 1
            },
        ]
    },
    methods: {
        add(index) {
            this.books[index].count++
        },
        sub(index) {
            this.books[index].count--
        },
        remove(index) {
            this.books.splice(index, 1)
        }
    },
    computed: {
        totalprice() {
            let totalprice = 0
            for (let i = 0; i < this.books.length; i++) {
                totalprice += this.books[i].price * this.books[i].count
            }
            return totalprice
        }
    },
    filters: { //过滤器
        showPrice(price) {
            return '￥' + price.toFixed(2)
        }
    }
})
```

css模块

```css
table {
    border: 1px solid #e9e9e9;
    border-collapse: collapse;
    border-spacing: 0;
}

th,
td {
    padding: 8px 16px;
    border: 1px solid #e9e9e9;
    text-align: left;
}

th {
    background-color: #f7f7f7;
    color: #5c6b77;
    font-weight: 600;
}
```

## 模块化开发

```js
//使用common.js的模块化规范
const { add, mul } = require('./mathUtil')
console.log(add(20, 30));
console.log(mul(20, 30));
//使用ES6的模块化的规范
import { name, age, height } from "./info";
console.log(name);
console.log(age);
console.log(height);
```

webpack下载插件：npm install --save-dev file-loader【插件名】@3.0.1【版本号】

npm install --save-dev vue-loader@15.4.2 vue-template-compiler@2.5.21

## 箭头函数

const ccc=(参数列表) =>{

}

两个参数

eg:const sum=(num1,num2)=>{

return num1+num2

}

一个参数：可以省略参数括号

const power=num1=>{

return num1+num2

}

函数代码块中只有一行代码

const sum=(num1,num2)=>num1+num2

## 后端路由

后端处理URL和页面之间的映射关系

服务器根据路由来渲染不同的页面

前端路由：vue-router

映射组件的渲染JS代码

cli3以上输npm run serve

以下是npm run dev

## router-link

<router-link to="/home">首页<router-link>

<router-link to="/home" tag="li">首页<router-link>

<router-link to="/home" replace>首页<router-link>

1、to,用于指定跳转的路径

2、tag:可以指定渲染成什么组件

3、replace：不会留下history记录，后健不能返回上一个页面中

通过代码如何实现页面跳转：

 this.$router.push('/home')

## 路由懒加载

当打包构建应用时，javascript包会变的非常大，影响页面加载。

把不同路由对应的组件分割成不同的代码块，然后当路由被访问的时候才加载对应组件，这样更加高效。

路由懒加载：

const routes =[

{

path:'/home',

component ()=>import('../compnents/home')

},

{

path:'/about',

compnent ()=>import('../components/about')

},

];

直接加载:

import home from '../compnents/home'

import about from '../compnents/about'

Vue.use(VueRouter);

const routes=[

{

path:'/home',

component: home

},

{

path:'/about',

compnent:about

}

]



cd ~/.ssh进入.ssh文件

git连接仓库时，先git init,再复制github里面的路径

vscode 连接github不成功时，产生原因：一般是这是因为服务器的SSL证书没有经过第三方机构的签署，所以才报错

参考网上解决办法：解除ssl验证后，再次git即可

git config --global http.sslVerify "false"

```
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:siwaer/learngit1.git
git push -u origin main
```

git branch -M main

//....修改文件以后需要做的操作

git add .
git commit -m "提示消息"
push -u origin main

出错：
! [rejected] master -> master (fetch first) error: failed to push some refs to ' 。。。'

出现这个问题是因为github中的README.md文件不在本地代码目录中，可以通过如下命令进行代码合并

git pull --rebase origin main

#### 项目步骤

1、目录划分

2、引用两个css文件

## GitHub 单个文件下载

[DownGit](https://minhaskamal.github.io/DownGit)

## style和js引用区别

style引用资源时，要用@import,在js里面引用资源时，要用import