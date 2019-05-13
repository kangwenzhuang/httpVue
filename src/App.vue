<template>
  <div>
    <el-button :plain="true" @click="open">打开消息提示</el-button>
    <el-button :plain="true" @click="openVn">VNode</el-button>
    <el-button type="primary" icon="el-icon-search" @click="sayHello">搜索</el-button>
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
    async sayHello() {
      console.log("udfhiefhfedgfie");
      await this.$http
        .post("http://172.17.173.150:8080/signin/test", {})
        .then(res => {
          console.log("我真的很难受");
        });
      await this.$http
        .get("http://172.17.173.150:8080/signin/test")
        .then(res => {
          console.log(res.bodyText);
        });
    }
  }
};
</script>