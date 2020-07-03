<template>
  <div class="home-container">
    <el-card header="【首页】" class="home-card">
      <el-form @submit.native.prevent="enterTheGame">
        <el-form-item label="名字">
          <el-input v-model="model.username"></el-input>
        </el-form-item>
        <el-form-item label="房间号">
          <el-input v-model="model.password"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" native-type="submit" class="button"
            >进入游戏</el-button
          >
        </el-form-item>
      </el-form>
      <div class="info">
<!--      todo: refactor button sytle-->
        <el-button @click ="gotoRule">游戏规则说明</el-button>
<!--        <el-link type="info" href="/rule">游戏规则说明</el-link>-->
      </div>
    </el-card>
  </div>
</template>

<script>
export default {
  name:'Home',
  data() {
    return {
      model: {},
    };
  },
  methods: {
    gotoRule(){
      this.$router.push('/rule')
    },
    enterTheGame() {
      console.log(this.model);
    },
  },
};
</script>

<style>
.home-card {
  width: 20rem;
  margin: 6rem auto;
}

.info {
  margin-left: 12rem;
}
</style>
