<template>
  <div>
    <el-button :plain="true" @click="open">打开消息提示</el-button>
    <el-button :plain="true" @click="openVn">VNode</el-button>
    <el-button type="primary" icon="el-icon-search" @click="addUser">添加用户</el-button>
    <el-button type="primary" icon="el-icon-search" @click="userList">用户列表</el-button>
    <el-button>hello</el-button>
  </div>
</template>

<script>
export default {
  methods: {
    open() {
      this.$message("这是一条消息提示");
    },
    ui() {
      alert("wojiao康文壮将");
    },

    openVn() {
      const h = this.$createElement;
      this.$message({
        message: h("p", null, [
          h("span", null, "内容可以是 "),
          h("i", { style: "color: teal" }, "VNode")
        ])
      });
    },
    async addUser() {
      await this.$http
        .post("http://kangkangin.asia:8080/signin/addUser", {
          'xuehao':'123456784',
          'name':'kangwenzhuang11',
          'phone':'17805973818',
          'mail':'1519752991@qq.com',
          'password':'123456',
          'shenfen':2,
          'sex':'男',
          'motto':'福大数计学院2号楼304',
        })
        .then(res => {
          console.log("添加信息："+res['body'].resultMessage);//因为存在重复添加所以会返回信息，学号和身份同时重复视为添加失败;
        });
    },
    async userList() {
      await this.$http
        .post("http://172.17.173.150:8080/signin/userList", {
          'shenfen':2,
        })
        .then(res => {
          console.log("用户列表"+res['body'].data);//你需要在前端定义一个数组接收,此时，打印结果是object，想看结果的话JSON.stringify(res['body'].data)，所以要定义一个数组，例如前端user[] 接收，你百度解决;
          console.log("用户列表"+JSON.stringify(res['body'].data));
        });
    }
  }
};
</script>