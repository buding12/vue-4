<template>
  <div>
    <p>获取所有图书信息</p>
    <button @click="getAllFn">查看控制台</button>
    <p>2.查询书籍</p>
    <input type="text" placeholder="请输入要查询的书籍" v-model="bName" />
    <button @click="findFn">查询</button>
    <p>3.书籍的添加</p>
    <input type="text" placeholder="请输入书名" v-model="bookObj.bookname" />
    <input type="text" placeholder="请输入作者名" v-model="bookObj.author" />
    <input type="text" placeholder="请输入出版社" v-model="bookObj.publisher" />
    <button @click="sendFn">发布</button>
  </div>
</template>

<script>
// 1.导入axios
import axios from "axios";
// 配置基础路径
axios.defaults.baseURL = "http://123.57.109.30:3006";
export default {
  data() {
    return {
      // 定义bName变量
      bName: "",
      bookObj: {
        //参数名提前跟后台的参数名对上-发送请求就不用早从对接
        bookname: "",
        author: "",
        publisher: "",
      },
    };
  },
  methods: {
    async getAllFn() {
      // 获取axios
      // axios({
      //   method:'GET',
      //   url:' http://123.57.109.30:3006/api/getbooks',
      // }).then(res =>{
      //   console.log(res.data);
      // })
      // 简单写法
      const data = await axios.get("http://123.57.109.30:3006/api/getbooks");
      console.log(data);
    },
    // 查询书籍名
    findFn() {
      axios({
        url: "/api/getbooks",
        method: "GET",
        params: {
          bookname: this.bName,
        },
      }).then((res) => {
        console.log(res);
      });
    },
    // 发布
    sendFn() {
    axios({
       url: "/api/addbook",
        method: "post",
        data: {
          appkey: "7250d3eb-18e1-41bc-8bb2-11483665535a",
          ...this.bookObj
        },
    }).then(res =>{
      console.log(res);
    })
    },
  },
};
</script>

<style>
</style>