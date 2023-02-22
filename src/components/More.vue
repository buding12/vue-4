<template>
  <div>
    <p>1.获取原生DOM</p>
    <h1 id="h" ref="myH">我是一只小蝴蝶</h1>
    <p>2.获取组件对象 - 可调用组件内一切</p>
    <Demo ref="de"></Demo>
    <p>3.VUE更新DOM是异步的</p>
    <p ref="myP">{{ count }}</p>
    <button @click="btn">点击COUNT+1，马上提取p标签内容</button>
  </div>
</template>

<script>
// 导入dome组件
import Demo from "./child/Dome.vue";
export default {
  mounted() {
    console.log(document.getElementById("h"));
    console.log(this.$refs.myH);
    let demoObj = this.$refs.de;
    demoObj.fn();
  },
  components: {
    Demo,
  },
  data() {
    return {
      count: 0,
    };
  },
  methods: {
    btn() {
      this.count++;
        // console.log(this.$refs.myP.innerHTML); // 0
      this.$nextTick(() => {
        console.log(this.$refs.myP.innerHTML);
      });
    },
  },
};
</script>

<style>
</style>