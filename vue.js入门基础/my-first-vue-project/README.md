###1章 vuejs及相关工具介绍
```
本章节讲师将对vuejs的概念及相关工具进行简单的介绍，以及将对vuejs基础框架搭建和和相关知识的讲解。
```
-  1-1 vuejs课程简介及框架简介 (06:23)
```$xslt
vue双向绑定的演示  以及  一个列表小案例(代码100行左右)
```
- 1-2 vuejs开发环境搭建及热更新 (10:57)
```$xslt
node和git先安装好，
https://npm.taobao.org/ 将npm镜像切为cnpm
cnpm -v 查看当前cnpm的版本
cnpm install -g vue-cli全局安装脚手架
这时候再直接输入vue，vue就会变成一条命令，.....
vue init webapck XXX 新建文件夹xx
```
- 1-3 从.vue到页面 (02:16)
```$xslt

```
- 1-4 vue.js组件的重要选项 (10:45)
```$xslt
data数据，所有的数据都放在data中
methods方法
watch监听
模板指令
    模板指令-v-if和v-show，两者的区别，面试经常问：
        控制这个元素的显示还是隐藏，v-if不渲染这个元素，而v-show是通过display:none来进行隐藏，但是用v-show在代码里是能够看到的。
    模板指令-html和vue对象的粘合剂
        数据渲染：v-text、v-html、{{}} 
    模板指定-v-for
        渲染循环列表：v-for
    模板指令-v-on
        事件绑定：v-on 简写@
    模板指令-v-bind
        属性绑定：v-bind 简写：
小结：
. new一个vue对象的时候你可以设置它的属性，其中最重要的包括三个，分别是data,methods,watch。
. 其中data代表vue对象的数据，methods代表vue对象的方法，watch设置了对象监听的方法
. Vue对象里的设置通过html指令进行关联
. 重要的指令包括
    - v-text渲染数据
    - v-if控制显示
    - v-on绑定事件
    - v-for循环渲染 等
```
- 1-5 vuejs-学习基础框架代码 (08:34)
```$xslt
对vue-cli脚手架创建的初始项目的一个简单分析介绍
```
 
 ###2章 todolist项目学习
```$xslt
 通过 todolist 项目，学习 vuejs 提供的开发方法，功能接口，及对父组件与子组件之间传参进行了说细讲解。
```
- 2-1 使用vuejs做一个todolist1 (12:13)
```$xslt
<template>
  <div id="app">
    <!--<h1>{{title}}</h1>  -->
    <!--<h1 v-text="title"></h1>-->
    <h1 v-html="title"></h1>
    <div v-for="item in items" v-bind:class="{finished:item.isFinished}">  <!--v-bind绑定  finished的class 是否是存在的-->
      <!--数组的话可以同时渲染两个class   v-bind:class="[liclass,liclass2]"-->
      {{item.label}}
    </div>
  </div>
</template>

<script>
export default {
  data:function () {
    return{
      title:'<span>?</span>This is a todo list',
      items:[
        {
          label:'coding',
          isFinished:false
        },
        {
          label:'walking',
          isFinished:true
        },
      ],
      liClass:'ThisisLiClass'
    }
  }
}
</script>

<style>
  .finished{    /*finished的class，就会加上下划线*/
  text-decoration: underline;
  }
html{
  height:100%;
}
body{
  display:flex;
  align-items: center;
  justify-content: center;
  height:100%;
}
</style>

```
- 2-2 使用vuejs做一个todolist2 (14:23)
##改节还有一个问题：v-bind在绑定class属性的时候，在item.isfinished = !item.isFinished,每点击一下就会重新定义item.isFinished的状态是否为真，目前在效果为真的时候应该出现下划线，目前效果没有出来
```angular2html
<template>
  <div id="app">
    <!--<h1>{{title}}</h1>  -->
    <!--<h1 v-text="title"></h1>-->
    <h1 v-html="title"></h1>
    <input v-model="newItem" v-on:keyup.enter="addNew()">
    <div v-for="item in items" v-bind:class="{finished:item.isFinished}" v-on:click="toggleFinish(item)">
      <!--v-bind绑定  finished的class 是否是存在的-->
      <!--数组的话可以同时渲染两个class   v-bind:class="[liclass,liclass2]"-->
      {{item.label}}
    </div>
  </div>
</template>

<script>
  export default {
    data: function () {
      return {
        title: '<span>?</span>This is a todo list',
        newItem:'',
        items: [
         /* {
            label: 'coding',
            isFinished: false
          },
          {
            label: 'walking',
            isFinished: true
          },*/
        ],
        liClass: 'ThisisLiClass'
      }
    },
    methods: {
      toggleFinish: function (item) {
        /* console.log(item)*/
        item.isfinished = !item.isFinished
      },
      addNew:function () {
       /* console.log(this.newItem);*/
      /*  this.newItem=""*/
      this.items.push({
        label:this.newItem,
        isFinished:false
      })
        this.newItem=''
      }
    }
  }
</script>

<style>
  .finished { /*finished的class，就会加上下划线*/
    text-decoration: underline;
  }

  html {
    height: 100%;
  }

  body {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100%;
  }
</style>
```
- 2-3 使用localstorage来存储todolist (14:05)    需要好好看一下
##改节还有一个问题：v-bind在绑定class属性的时候，在item.isfinished = !item.isFinished,每点击一下就会重新定义item.isFinished的状态是否为真，目前在效果为真的时候应该出现下划线，目前效果没有出来
##与上面一样
```angular2html
<template>
  <div id="app">
    <!--<h1>{{title}}</h1>  -->
    <!--<h1 v-text="title"></h1>-->
    <h1 v-html="title"></h1>
    <input v-model="newItem" v-on:keyup.enter="addNew()">
    <div v-for="item in items" v-bind:class="{finished:item.isFinished}" v-on:click="toggleFinish(item)">
      <!--v-bind绑定  finished的class 是否是存在的-->
      <!--数组的话可以同时渲染两个class   v-bind:class="[liclass,liclass2]"-->
      {{item.label}}
    </div>
  </div>
</template>

<script>
  import Store1 from './store1';
  console.log(Store1);
  export default {
    data: function () {
      return {
        title: '<span>?</span>This is a todo list',
        newItem:'',
        // items: [
         /* {
            label: 'coding',
            isFinished: false
          },
          {
            label: 'walking',
            isFinished: true
          },*/
        // ],
        items:Store1.fetch(),
      }
    },
    watch:{
      items:{
        handler:function (items) {
          /*console.log(value,oldvalue)*/
          Store1.save(items);
        },
        deep:true
      }
    },
    methods: {
      toggleFinish: function (item) {
        /* console.log(item)*/
        item.isfinished = !item.isFinished
      },
      addNew:function () {
       /* console.log(this.newItem);*/
      /*  this.newItem=""*/
      this.items.push({
        label:this.newItem,
        isFinished:false
      })
        this.newItem=''
      }
    }
  }
</script>

<style>
  .finished { /*finished的class，就会加上下划线*/
    text-decoration: underline;
  }

  html {
    height: 100%;
  }

  body {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100%;
  }
</style>
```
- 2-4 如何划分组件 (05:07)
```angular2html
                如何划分组件
    功能模块- select,pagenation
    页面区域- header,footer,sidebar
    
    vuejs组件之间的调用--另外一个重要选项components
    ```
     import Header from './header'
      import Footer from './footer'
      new Vue({
        data:{
          isShow:true
        },
        components:{
          [Header,Footer]
        }
      })
      ```
      
      vuejs组件之间的通信-props
      ```
      // this is hedaer.vue
        new Vue({
          data: {
            username: 'xxx'
          },
          props: ['msg'],
          methods: {
            doThis: functiion()
        {
          console.log(this.msg)
        }
        }
        })
      ```
      ```
      //this is app.vue
      <header msg="something interesting"></header>
      <footer></footer>
      ```
```
- 2-5 vuejs 组件1（父向子组件传参） (11:36)
```angular2html
    // App.vue
     ```angular2html
          <template>
            <div id="app">
              <!--<h1>{{title}}</h1>  -->
              <!--<h1 v-text="title"></h1>-->
              <h1 v-html="title"></h1>
              <input v-model="newItem" v-on:keyup.enter="addNew()">
              <ul>
                  <li v-for="item in items" v-bind:class="{finished:item.isFinished}" v-on:click="toggleFinish(item)">
                    <!--v-bind绑定  finished的class 是否是存在的-->
                    <!--数组的话可以同时渲染两个class   v-bind:class="[liclass,liclass2]"-->
                    {{item.label}}
                  </li>
              </ul>
             <component-a msgfromfather="happy"></component-a>
            </div>
          </template>
          
          <script>
            import Store1 from './store1';
            import ComponentA from './components/componentA'
            console.log(Store1);
            export default {
              data: function () {
                return {
                  title: '<span>?</span>This is a todo list',
                  newItem:'',
                  // items: [
                   /* {
                      label: 'coding',
                      isFinished: false
                    },
                    {
                      label: 'walking',
                      isFinished: true
                    },*/
                  // ],
                  items:Store1.fetch(),
                }
              },
              watch:{
                items:{
                  handler:function (items) {
                    /*console.log(value,oldvalue)*/
                    Store1.save(items);
                  },
                  deep:true
                }
              },
              components:{
                ComponentA
              },
              methods: {
                toggleFinish: function (item) {
                  /* console.log(item)*/
                  item.isfinished = !item.isFinished
                },
                addNew:function () {
                 /* console.log(this.newItem);*/
                /*  this.newItem=""*/
                this.items.push({
                  label:this.newItem,
                  isFinished:false
                })
                  this.newItem=''
                }
              }
            }
          </script>
          
          <style>
            .finished { /*finished的class，就会加上下划线*/
              text-decoration: underline;
            }
          
            html {
              height: 100%;
            }
          
            body {
              display: flex;
              align-items: center;
              justify-content: center;
              height: 100%;
            }
          </style>

     ````
     
     ```
     // componentA
     <template>
       <div class="hello">
         <h1>{{ msg }}</h1>
         <h1>{{msgfromfather}}</h1>
         <button v-on:click="onClickMe">Click</button>
       </div>
     </template>
     
     <script>
     export default {
       data () {
         return {
           msg: 'Welcome to Your Vue.js App'
         }
       },
       props:['msgfromfather'],
       methods:{
         onClickMe:function () {
           console.log(this.msgfromfather)
         }
       }
     }
     </script>
     
     <!-- Add "scoped" attribute to limit CSS to this component only -->
     <style scoped>
     h1, h2 {
       font-weight: normal;
     }
     ul {
       list-style-type: none;
       padding: 0;
     }
     li {
       display: inline-block;
       margin: 0 10px;
     }
     a {
       color: #42b983;
     }
     </style>
     ```
```
- 2-6 vuejs 组件2（子向父组件传参） (12:47)   需要好好看一下
```angular2html
自定义事件
vue实例实现了一个自定义事件接口，用于在组件树中通信。这个事件系统独立于原生DOM事件，用法也不同。
每个vue实例都是一个事件触发器
 使用$on()监听事件;
 使用$emit()在它上面触发事件
 使用$dispatch()派发事件，事件沿着父链冒泡
 使用$boradcast()广播事件，事件向下传导给所有的后代
 
 不同于DOM事件，Vue事件在冒泡过程中第一次触发回调之后自动停止冒泡，除非回调明确返回true。


vue-router 路由
  ```youtrack
  //App.vue
  <template>
    <div id="app">
      <!--<h1>{{title}}</h1>  -->
      <!--<h1 v-text="title"></h1>-->
      <h1 v-html="title"></h1>
      <input v-model="newItem" v-on:keyup.enter="addNew()">
      <ul>
          <li v-for="item in items" v-bind:class="{finished:item.isFinished}" v-on:click="toggleFinish(item)">
            <!--v-bind绑定  finished的class 是否是存在的-->
            <!--数组的话可以同时渲染两个class   v-bind:class="[liclass,liclass2]"-->
            {{item.label}}
          </li>
      </ul>
      <p>child tells me:{{childWords}}</p>
     <component-a msgfromfather="happy" v-on:child-tell-me-something="listenToMyBoy"></component-a>
    </div>
  </template>
  
  <script>
    import Store1 from './store1';
    import ComponentA from './components/componentA'
    // console.log(Store1);
    export default {
      data: function () {
        return {
          title: '<span>?</span>This is a todo list',
          newItem:'',
          childWords:'',
          // items: [
           /* {
              label: 'coding',
              isFinished: false
            },
            {
              label: 'walking',
              isFinished: true
            },*/
          // ],
          items:Store1.fetch(),
        }
      },
      watch:{
        items:{
          handler:function (items) {
            /*console.log(value,oldvalue)*/
            Store1.save(items);
          },
          deep:true
        }
      },
      components:{
        ComponentA
      },
      methods: {
        toggleFinish: function (item) {
          /* console.log(item)*/
          item.isfinished = !item.isFinished
        },
        addNew:function () {
         /* console.log(this.newItem);*/
        /*  this.newItem=""*/
        this.items.push({
          label:this.newItem,
          isFinished:false
        })
          this.newItem=''
        },
        listenToMyBoy:function (msg) {
          this.childWords=msg
        }
      }
    }
  </script>
  
  <style>
    .finished { /*finished的class，就会加上下划线*/
      text-decoration: underline;
    }
  
    html {
      height: 100%;
    }
  
    body {
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100%;
    }
  </style>
  
  
  ```
 //components
 <template>
   <div class="hello">
     <h1>{{ msg }}</h1>
     <h1>{{msgfromfather}}</h1>
     <button v-on:click="onClickMe">open mouse</button>
   </div>
 </template>
 
 <script>
 export default {
   data () {
     return {
       msg: 'Welcome to Your Vue.js App'
     }
   },
   props:['msgfromfather'],
   methods:{
     onClickMe:function () {
      /* console.log(this.msgfromfather)*/
       this.$emit('child-tell-me-something',this.msg)
     }
   }
 }
 </script>
 
 <!-- Add "scoped" attribute to limit CSS to this component only -->
 <style scoped>
 h1, h2 {
   font-weight: normal;
 }
 ul {
   list-style-type: none;
   padding: 0;
 }
 li {
   display: inline-block;
   margin: 0 10px;
 }
 a {
   color: #42b983;
 }
 </style>
  ```
```
