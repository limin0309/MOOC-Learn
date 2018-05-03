###1章 课程介绍
#####初步认识vue
**1-1 Vue基础知识介绍 (13:59)**
######课程介绍
- Vue基础知识介绍
- 购物车功能案例介绍
- 地址列表功能案例实现
- 课程总结

######vue的优势：
- 1、易用
- 2、灵活-渐进式
声明式渲染 组件系统 客户端路由   大规模状态管理 构建工具
- 3、高效

######vue基础指令介绍
- 指令的使用:v-model v-text v-show v-if v-bind v-for v-on
    -  此处要注意v-show和v-if的区别
         - v-if 条件判断，不满足条件的话则不会出现在dom中
         - v-show 是否显示，不管满不满足条件均会在dom中，若不满足条件，则会设置成隐藏 display:none
- 过滤器filter
- 组件Component

###2章 创建Vue实例
#####创建一个Vue实例
**2-1 创建Vue实例 (15:27)**
######购物车案例课程安排
 ```angular2html
- 创建一个Vue的实例
- 通过v-for指令渲染产品数据
- 使用filter对金额和图片进行格式化
- 使用v-on实现产品金额的动态计算
- 综合演示

  ***vue的生命周期***
  
   new Vue({
          el:'#app',
          data:{title:"Hello Vue"
          },
          filters:{
  
          },
          mounted:function () {
              this.cartView();或者
              this.$nextTick(function（）{
              vm.cartView();
              })
          },
          methods: {
              cartView:function () {
                  this.title="vue hello"
              }
          },
      })
      
      //用mounted方法将默认的Hello vue修改为vue Hello
```

###3章 使用v-for指令渲染商品列表
#####教你如何使用v-for指令渲染商品列表
**3-1 使用v-for指令渲染商品列表 (26:17)**
```$xslt
使用v-for指令渲染产品数据

```
###4章 过滤器的使用
#####教你如何使用vue过滤器
**4-1 vue过滤器的使用 (14:26)**
```$xslt

```
###5章 购物车综合案例讲解
#####实现购物车的基本功能
**5-1 单件商品金额计算和单选全选功能 (28:00)**
```$xslt

```
**5-2 商品总金额计算、删除功能实现 (23:20)**
```$xslt

```
###6章 地址列表综合案例讲解
#####实现地址列表的基本功能
**6-1 地址列表过滤和展开所有功能实现 (21:45)**
```$xslt
地址列表案例课程安排
 通过v-for指令渲染地址数据以及数组过滤
 地址卡片选择
 综合演示
 
 
 数组的常用方法:splice  slice   slice会返回一个全新的数组，跟原来的addressList没有任何的关系。splice会对原来的数组进行操作，整个原生的对象就会发生变化。
```
**6-2 卡片选中、设置默认等功能实现 (15:34)**
```$xslt

```
###7章 课程总结
**7-1 课程总结 (08:27)**
```$xslt
课程总结
. 学会如何创建一个Vue实例
. 指令 v-model v-text v-show v-if v-bind v-for v-on
. 过滤器的使用、computed使用
. 结合指令和API
. axios


看到列表--应该想到v-for
看到金额，货币转换，应该想到过滤器
凡是看到表单，单选框，复选框，下拉框，只要是v-model的，我们应该想到双向数据绑定
凡是看到+  -，删除，有操作的，我们应该想到v-on绑定事件
有样式变化的，用v-bind动态操作
v-for里面是可以套v-for的
axios的使用
```