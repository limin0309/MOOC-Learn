<template>
  <div id="app">
    <!--<h1>{{title}}</h1>  -->
    <!--<h1 v-text="title"></h1>-->
    <h1 v-html="title"></h1>
    <div v-for="item in items" v-bind:class="{finished:item.isFinished}">
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
  .finished{

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
