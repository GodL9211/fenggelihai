<!-- 单文件组件及slot插槽 -->

<template>
  <li class="item">
    <!-- {{item}} -->
    <input type="checkbox" v-model="checked">
    <slot name="item" v-bind="{checked}"></slot>
  </li>
</template>

<script>
  export default {
    props: ["item"],
    data(){
      return {
        checked: false
      }
    }
  }
</script>

<style scoped>
/* <style> */
       .item {
            color: red;
        }

</style>