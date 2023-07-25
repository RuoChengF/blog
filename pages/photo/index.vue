<template>
  <div>
    <!-- 循环渲染图片 -->
    <!-- <img v-for="item in imgUrlList" :src="item" :key="item" > -->
    <img src="../../static/imgdata/574ba57647de4dd693c823ce828236cd.png" alt="" srcset="">
    <div v-for="item in imgUrlList" :src="item" :key="item">
       {{item}}
       <img :src="item" alt="" srcset="">
    </div>
  </div>
</template>

<script>
import imgdata from "../../static/imgdata/image_data.json"
export default {
  data() {
    return {
      imgdata  ,// json 数据
      imgUrlList:[]
    };
  },
  mounted() {
      imgdata.forEach(item => {
        console.log(item);
        this.imgUrlList.push(`../../static/imgdata/${item.filename}`)
      });
  },
  methods: {
    
  },
};
</script>
