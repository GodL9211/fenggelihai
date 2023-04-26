<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    {{msg}}
    <div>
        <input type="text" v-model="info">
        <button @click="handleClick">添加</button>
    </div>
    <ul>
        <!-- <li v-for="item in list">{{item}}</li> -->  
        <!-- 使用自定义组件替换， 驼峰转为-分割  插槽，作用域插槽-->
        <todo-item v-for="item in list" :key="item" :item="item">
        <template v-slot:item="itemProps">
          <!-- <span style="font-size: 90px;">{{ item }}</span> -->
          <span :style="{fontSize: '90px', color: itemProps.checked ? 'red':'blue'}">{{ item }}</span>
        </template>
        </todo-item>
    </ul>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import TodoItem from './components/TodoItem.vue'

export default {
  name: 'App',
  data(){
      return {
          msg: 'hello world',
          info: '',
          list: [],
      }
  },
  methods: {
      handleClick(){
          this.list.push(this.info)
          this.info = ''
      }
  },
  components: {
    TodoItem,
  }
}
</script>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
