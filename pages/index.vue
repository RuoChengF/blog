<template>
  <div class="container">
    <el-container>
      <el-aside width="500px">
        <el-card class="box-card">
          <div slot="header">
            <span>关于我</span>
          </div>
          <div class="wrapper">
            <div class="image">
              <el-avatar shape="square" :size="200" :src="pho"></el-avatar>
            </div>
            <div class="text">
               {{aboutMe}}
            </div>
          </div>
        </el-card>
      </el-aside>
      <el-main>
        <el-card v-for="(item, index) in blogJson" :key="index">
          <el-row :gutter="20">
            <el-col :span="20" class="mycol">
              <h3 @click="handleLink(item.blogLink)">{{ item.title }}</h3>
              <p>{{ item.desc }}</p>
            </el-col>

            <el-col :span="4">
              <el-image
                style="width: 100px; height: 100px"
                :src="item.imgLink"
                fit="fill"
              ></el-image>
            </el-col>
          </el-row>
        </el-card>
      </el-main>
    </el-container>
  </div>
</template>

<script>
import pho from "../assets/img/1.jpg";
import blogJson from "../assets/result.json";
export default {
  layout: "Myblog",
  data() {
    return {
      pho,
      blogJson,
      aboutMe: `大家好，我是一名专注于 Python 和前端技术的技术讲解者。
       我擅长将复杂的技术概念转化为简单易懂的语言，帮助初学者快速入门，
       并满足高级开发者对更深入理解的需求。 作为一位资深的 Python 开发者，我具备广泛的编程经验和深厚的技术功底。我熟练掌握 Python 语言的各种特性和库，能够灵活运用它们解决实际问题。
       不论是爬虫、数据分析、后端开发还是机器学习，我都能够提供高效、可靠的解决方案。
        如果你对 Python 或前端技术有任何疑问或需要帮助，欢迎与我联系。无论是入门指导、项目建议还是技术咨询，
        我都会竭诚为您提供帮助。让我们一起探索技术的魅力，共同成长和进步！`,
    };
  },
  methods: {
    handleLink(item){
      //  window.location.href = 
      window.open(item, "_blank")
    }
  },
};
</script>
<style lang="scss" scoped>
// .box-card{
//    padding: 30px 0px 30px 0;
// }
.wrapper {
  overflow: hidden; /* 确保容器可以包含浮动元素 */
  width: 500px; /* 文字区域宽度 */
}

.text {
}

.image {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  overflow: hidden;
  border: 2px solid #f0f0f0;
  float: left;
  shape-outside: circle();
}
.mycol{
   cursor: pointer;
}

::v-deep .el-card {
   margin-bottom: 20px;
}
</style>