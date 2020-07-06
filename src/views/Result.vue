<template>
  <div class="home-container">
    <el-card header="游戏结果" class="home-card">
      <el-table :data="resultData" style="width: 100%">
        <el-table-column prop="name" label="姓名"> </el-table-column>
        <el-table-column prop="status" label="身份"> </el-table-column>
      </el-table>
      <div class="info">
        <el-button @click="gotoRule">回到首页</el-button>
        <el-button @click="gotoRank">排行版</el-button>
      </div>
    </el-card>
  </div>
</template>

<script>
import { axios } from "axios";
import apiUrl from "../config/apiUrl";
export default {
  name: "Result",
  data() {
    return {
      resultData: [
        {
          status: "预言家",
          name: "王小虎"
        },
        {
          status: "平民",
          name: "王小虎"
        },
        {
          status: "预言家",
          name: "王小虎"
        },
        {
          status: "平民",
          name: "王小虎"
        },
        {
          status: "预言家",
          name: "王小虎"
        },
        {
          status: "平民",
          name: "王小虎"
        }
      ]
    };
  },
  methods: {
    gotoRule() {
      this.$router.push("/home");
    },
    gotoRank() {
      this.$router.push("/rank");
    },
    getResultData() {
      axios
        .get({ method: "GET", URL: apiUrl.getResult })
        .then(res => (this.resultData = res.data))
        .catch(error =>
          this.$message({
            message: error.msg || "获取数据失败",
            type: "warning"
          })
        );
    }
  },
  mounted() {
    this.getResultData();
  }
};
</script>

<style scoped>
.home-card {
  width: 20rem;
  margin: 6rem auto;
}

.info {
  display: flex;
  justify-content: space-around;
}
</style>


