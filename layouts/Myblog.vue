<template>
  <div>
    <el-card class="nav">
              <h1>若城的博客</h1>

     <div class="left">
       <el-row :gutter="20">
        <el-col :span="8" v-for="item in nav" :key="item.label">

          <span class="mynav" @click="handleJump(item.route)">{{item.label}}</span>
        </el-col>
       
      </el-row>
     </div>

     <div class="right">
       <el-row :gutter="20">
        <el-col :span="12"><span  @click="handleGoLogin(1)" class="mynav">登录</span></el-col>
        <el-col :span="12" ><span @click="handleGoLogin(2)" class="mynav">注册</span></el-col>
      </el-row>
     </div>
    </el-card>
    <nuxt />
     
  </div>
</template>
<script>
export default {
  data() {
    return {
      nav:[
         {
          label:'首页',
          route:'index'
         },
         {
          label:'博客画廊',
          route:'photo'
         },
         {
          label:'我的画廊',
          route:'about'
         },
      ]
    }
  },
  methods: {
    handleJump(url){
        this.$router.push({name:url})
    },
    handleGoLogin(idx){
         this.$router.push({name:'login'})

    }
  },
}
</script>
<style lang="scss" scoped>
  .nav{
    
  }
  h1{
     height: 30px;
          cursor: pointer;

     line-height: 30px;
  }
  ::v-deep .el-card__body{
 display: flex;
     justify-content: space-between;
  }
  .left{
     width: 30%;
     cursor: pointer;
  }
  .right{
    width: 10%;
         cursor: pointer;

  }
</style>