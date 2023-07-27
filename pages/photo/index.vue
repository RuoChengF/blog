<template>
  <div class="myPho">
    <!-- 循环渲染图片 -->
   
   <el-row :gutter="20">

    <el-col :span="8"  v-for="item in blogJson"
      :key="item.imgLink"
      > 
      <el-card
     
      class="mycard"
    >
      <el-image
      style="width: 100%; height: 300px"
      :src="item.imgLink"
      fit="fill"></el-image>

      <div class="titleDiv" style="padding: 14px">
        <span @click="handleLink(item.blogLink)">{{ item.title }}</span>
      </div>
    </el-card>
  
    </el-col>
   </el-row>
  </div>
</template>

<script>
// import imgdata from "../../static/imgdata/image_data.json";
import blogJson from "../../assets/result.json";
export default {
  layout: "Myblog",

  data() {
    return {
      // imgdata, // json 数据
      // imgUrlList: [],
      blogJson,
    };
  },
  
  mounted() {
    // imgdata.forEach((item) => {
    //   console.log(item);
    //   this.imgUrlList.push(require(`../../static/imgdata/${item.filename}`));
    // });
  },
  methods: {
    handleLink(item){
             window.open(item, "_blank")

    }
  },
};
</script>
<style lang="scss" scoped>
  .mycard ::v-deep .el-card__body{
    display: flex !important;
    flex-direction: column !important;
  }
  .myPho ::v-deep .el-col-8{
margin-bottom: 20px;
margin-top: 20px;
  }
  .titleDiv{
     height: 40px;
     cursor: pointer;
  }
</style>
