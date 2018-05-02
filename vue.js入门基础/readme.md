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
https://npm.taobao.org/ 将npm镜像切为cnpm
cnpm -v 查看当前cnpm的版本
cnpm install -g vue-cli全局安装脚手架
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

```
- 2-2 使用vuejs做一个todolist2 (14:23)
- 2-3 使用localstorage来存储todolist (14:05)
- 2-4 如何划分组件 (05:07)
- 2-5 vuejs 组件1（父向子组件传参） (11:36)
- 2-6 vuejs 组件2（子向父组件传参） (12:47)