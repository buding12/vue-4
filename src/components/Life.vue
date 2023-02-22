<template>
  <div>
    <p>学习生命周期，看控制台打印</p>
    <p>{{ msg }}</p>
    <p id="myp">{{ msg }}</p>
    <ul id="myUL">
      <li v-for="(val, index) in arr" :key="index">{{ val }}</li>
    </ul>
    <button @click="arr.push(1000)">点击末尾价值</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      msg: "布丁真好看",
      arr: [2, 5, 4, 6]
    };
  },
  //  一、初始化
  // new Vue()以后，vue内部给实例对象添加了一些属性和方法，data和methods初始化“之前”
  beforeCreate() {
    console.log("beforeCreate ---执行了");
    console.log(this.msg);
  },
  // data和methods初始化以后
  // 场景: 网络请求, 注册全局事件
  created() {
    console.log("created -- 执行");
    console.log(this.msg); // hello, Vue
    // this.timer = setInterval(() => {
    //     console.log("哈哈哈");
    // }, 1000)
  },
  //  二、挂载
  // 真实DOM挂载之前
  beforeMount() {
    console.log("beforeMount --执行");
    console.log(document.getElementById("myp"));
    this.msg = "重新值";
  },
  // 真实DOM挂载之后
  mounted() {
    console.log("mounted --执行");
    console.log(document.getElementById("myp"));
  },

  // 三、更新
  // data数据改变才执行
  beforeUpdate() {
    console.log("beforeUpdate -- 执行");
    console.log(document.querySelectorAll("#myUL>li")[4]); // undefined
  },
  // 更新之后
  // 获取更新之后的真实DOM
  updated() {
    console.log("updated ---执行");
    console.log(document.querySelectorAll("#myUL>li")[4]);
  },
  // 四、销毁组件
  beforeDestroy() {
    console.log("beforeDestroy -- 执行");
  },
  destroyed() {
    console.log("destrory -- 执行");
  },
};
</script>

<style>
</style>