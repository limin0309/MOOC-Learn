##1、前端服务化的优点：
- 前后端完全解耦(开发、代码、部署、纯页面改版)
- 前端的html、css、js和image统一维护
- 页面与ajax的html模板复用
- 框架机使用nodejs，前端整体使用js
- 解放后端，更关注与数据层和业务逻辑层

## 4章 Vue.js-数据驱动的组件化前端开发
#### 4-1 Vue.js-数据驱动的组件化前端开发(1)
######尤雨溪--目前就职于www.meteor.com
######github.com/meteor/meteor
###展示内容：
- v-model的展示   更多详见官网
- 数据驱动 
- 组件化 
```
        //my-component将其当做html的一个标签来使用
        //在Vue.js中注册组件
        // 扩展Vue来自定义一个可复用的组件类
        vue MyComponent =Vue.extend({
            template:'<p>{{msg}}</p>',
            paramAttributes:['msg']
        })
         // 全局注册该组件
         Vue.component('my-component',MyComponent)
```
```$xslt
 //在 Vue模块中使用组件
         <my-component msg="Hello"></my-component>
                my-component 组件的模块将会被填充到该元素中，而msg
                则会被作为数据传入该组件实例。渲染过程如下：
            <my-conponent>
                <p>Hello!</p>
            </my-conponent>
``` 
       
####4-2 Vue.js-数据驱动的组件化前端开发(2)
#####通过paramAttributes实现父子组件之间的数据传递
```
<my-component msg="{{msgFormParent}}"></my-component>
```
#####一些实现细节
######ES5的局限：
```$xslt
不能侦测对象属性的添加/删除
//如果data上不存在prop属性，
//则必须要用$set或$add才会触发更新
data.$set('prop',value)
data.$add('prop',value)

//删除属性要用$delete
data.$delete('prop')

//数组不能用arr[0]=value,要用$set
arr.$set(0,value)
```
######基于CommanJS的单文件组件：Vueify
通过Browserify或者Webpack这样的模块构建工具，将一个组件的模板，CSS和JS都写在同一个文件里
