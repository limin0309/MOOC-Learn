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
