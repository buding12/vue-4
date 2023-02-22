<template>
  <div>
    <h1>生命周期</h1>
    <!-- 3.使用组件 -->
    <Life v-if="show"></Life>
    <button @click="show = false">销毁组件</button>
    <hr />
    <h1>2.axios使用</h1>
    <UseAxios></UseAxios>
    <!-- 3.获取原生DOM -->
    <More></More>

    <Tick></Tick>

     <h1>5.组件对象的name属性</h1>
     <ComNameHAHA> </ComNameHAHA>
  </div>
</template>

<script>
// 1.引入life组件
import Life from "./components/Life.vue";
// 2.1导入axios组件
import UseAxios from "./components/UseAxios.vue";
// 3.引入组件
import More from "./components/More.vue";
// 引入
import Tick from './components/Tick.vue'

import Com from './components/Com.vue'
export default {
  data() {
    return {
      show: true,
    };
  },
  //2.注册组件
  components: {
    Life,
    UseAxios,
    More,
    Tick,
    [Com.name]:Com
  },
};
</script>

<style>
</style>