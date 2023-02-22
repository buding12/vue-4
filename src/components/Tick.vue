<template>
  <div>
    <input ref="myInp" type="text" placeholder="请输入内容" v-if="isShow">
    <button v-else @click="btn">点我进行搜索</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isShow:false
    }
  },
  methods: {
  async  btn(){
      this.isShow = true
     
      await this.$nextTick();
      this.$refs.myInp.focus()
    }
  },
}
</script>

<style>

</style>