<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    {{message}}
    <div :id="message">
      <input v-model="message">
      <ul>
        <todo-item @delete="handleDelete" v-for="item in list" :key="item.title" :title="item.title" :del="item.del">
          <template v-slot:pre="{value}">
            <span slot="pre">前置图标,{{value}}</span>
          </template>
          <template v-slot:sub>
            <span slot="sub">后置图标</span>
          </template>

        </todo-item>
      </ul>
      <todo-list></todo-list>
    </div>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import TodoList from "@/components/TodoList";
import TodoItem from "@/components/TodoItem";

export default {
  name: 'App',
  components: {
    TodoList,
    TodoItem
  },
  data(){
    return {
      message:'hello,world',
      list:[{
        title:'class1',
        del:true
      },{
        title:'class2',
        del:true
      }],
    }
  },
  methods:{
    handleDelete(val){
      console.log('handDelete',val)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
