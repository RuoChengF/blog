<template>
  <div>
    <el-card class="nav">
              <h1>若城的博客</h1>

     <div class="left">
       <el-row :gutter="20">
        <el-col :span="8"><span class="mynav" @click="handleJump(1)">首页</span></el-col>
        <el-col :span="8"><span class="mynav" @click="handleJump(2)">博客相册</span></el-col>
        <el-col :span="8"><span class="mynav" @click="handleJump(3)">关于我</span></el-col>
      </el-row>
     </div>

     <div class="right">
       <el-row :gutter="20">
        <el-col :span="12"><span class="mynav">登录</span></el-col>
        <el-col :span="12"><span class="mynav">注册</span></el-col>
      </el-row>
     </div>
    </el-card>
    <nuxt />
     
  </div>
</template>
<script>
export default {
  methods: {
    handleJump(index){
        this.$router.push({name:'photo-photo'})
    }
  },
}
</script>
<style lang="scss" scoped>
  .nav{
    
  }
  h1{
     height: 30px;
     line-height: 30px;
  }
  ::v-deep .el-card__body{
 display: flex;
     justify-content: space-between;
  }
  .left{
     width: 30%;
  }
  .right{
    width: 10%;
  }
</style>