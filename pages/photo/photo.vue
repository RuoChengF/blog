<template>
    <div>
         <el-carousel :interval="4000" type="card" height="200px">
    <el-carousel-item v-for="item in blogJson" :key="item">
      <img :src="item.imgLink" alt="" srcset="">
      <!-- <h3 class="medium">{{ item.title }}</h3> -->
    </el-carousel-item>
  </el-carousel>
    </div>
</template>
<script>
import blogJson from "../../assets/result.json";

export default {
      layout: "Myblog",

    data() {
        return {
            blogJson
        }
    },
}
</script>