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
              {{ aboutMe }}
            </div>
          </div>
        </el-card>
		<el-card class="box-card">
          <clock />
        </el-card>
      </el-aside>
      <el-main class="myAbout">
        <el-card>
          <!-- <el-row>
            <el-image fit="fill" :src="pho"></el-image>
          </el-row>
          <el-row>
             <p>{{aboutMe}}</p>
          </el-row>
       -->
        <div class="wrap">

<div class="cube">

	<div class="out_front">
		<img :src="img1" class="pic">
	</div>
	
	<div class="out_back">
		<img :src="img2" class="pic">
	</div>
	
	<div class="out_left">
		<img :src="img3" class="pic">
	</div>
	<div class="out_right">
		<img :src="img4" class="pic">
	</div>
	<div class="out_top">
		<img :src="img5" class="pic">
	</div>
	<div class="out_bottom">
		<img :src="img6" class="pic">
	</div>
	
	<span class="in_front">
		<img :src="img7" class="in_pic">
	</span>
	<span class="in_back">
		 <img :src="img8" class="in_pic">
	</span>
	<span class="in_left">
		<img :src="img9" class="in_pic">
	</span>
	<span class="in_right">
		<img :src="img10" class="in_pic">
	</span>
	<span class="in_top">
		<img :src="img11" class="in_pic">
	</span>
	<span :src="img12" class="in_pic">
	</span>
</div>
</div>
 </el-card> 
      </el-main>
    </el-container>
  </div>
</template>

<script>
import pho from "../../assets/img/1.jpg";
import img1 from "../../static/heng/1.jpg"
import img2 from "../../static/heng/2.jpg"
import img3 from "../../static/heng/3.jpg"
import img4 from "../../static/heng/4.jpg"
import img5 from "../../static/heng/5.jpg"
import img6 from "../../static/heng/6.jpg"
import img7 from "../../static/heng/7.jpg"
import img8 from "../../static/heng/8.jpg"
import img9 from "../../static/heng/9.jpg"
import img10 from "../../static/heng/10.jpg"
import img11 from "../../static/heng/11.jpg"
import img12 from "../../static/heng/12.jpg"
import clock from "../../components/Clock.vue"

export default {
  layout: "Myblog",
  data() {
    return {
      pho,
      img1,
      img2,
      img3,
      img4,
      img5,
      img6,
      img7,
      img8,img9,
      img10,
      img11,
      img12,
      aboutMe: `大家好，我是一名专注于 Python 和前端技术的技术讲解者。
       我擅长将复杂的技术概念转化为简单易懂的语言，帮助初学者快速入门，
       并满足高级开发者对更深入理解的需求。 作为一位资深的 Python 开发者，我具备广泛的编程经验和深厚的技术功底。我熟练掌握 Python 语言的各种特性和库，能够灵活运用它们解决实际问题。
       不论是爬虫、数据分析、后端开发还是机器学习，我都能够提供高效、可靠的解决方案。
        如果你对 Python 或前端技术有任何疑问或需要帮助，欢迎与我联系。无论是入门指导、项目建议还是技术咨询，
        我都会竭诚为您提供帮助。让我们一起探索技术的魅力，共同成长和进步！`,
    };
  },
  component(){
    clock
  },
  methods: {
    handleLink(item) {
      //  window.location.href =
      window.open(item, "_blank");
    },
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
.myAbout ::v-deep .el-card__body{
  display: flex;
  flex-direction: column;
  height: 1200px;
}
.myAbout ::v-deep .el-card{
     height: 1200px;

}
.myAbout ::v-deep .el-image{
display: flex;
justify-content: center;
}

.myAbout ::v-deep .el-image__inner{
  width: 300px;
  height: 300px;
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
.mycol {
  cursor: pointer;
}

::v-deep .el-card {
  margin-bottom: 20px;
}

::v-deep .el-aside{
   margin-top: 20px;
}


/*最外层容器样式*/
.wrap{
	width: 10px;
	height: 10px;
	/*改变左右上下,图片方块移动*/
	margin: 400px 400px;
	position: relative;
	
}
/*包裹所有容器样式*/
.cube{
	width:600px;
	height:400px;
	margin: 0 auto;
	transform-style: preserve-3d;
	transform: rotateX(-30deg) rotateY(-80deg);
	-webkit-animation: rotate 20s infinite;
	/*匀速*/
	animation-timing-function: linear;
}
@-webkit-keyframes rotate{
	from{transform: rotateX(0deg) rotateY(0deg);}
	to{transform: rotateX(360deg) rotateY(360deg);}
}
.cube div{
	position: absolute;
	width: 300px;
	height: 300px;
	opacity: 0.8;
	transition: all .4s;
}
/*定义所有图片样式*/
.pic{
	width: 300px;
	height: 300px;
}
.cube .out_front{
	transform: rotateY(0deg) translateZ(150px);
}
.cube .out_back{
	transform: translateZ(-150px) rotateY(180deg);
}
.cube .out_left{
	transform: rotateY(90deg) translateZ(150px);
}
.cube .out_right{
	transform: rotateY(-90deg) translateZ(150px);
}
.cube .out_top{
	transform: rotateX(90deg) translateZ(150px);
}
.cube .out_bottom{
	transform: rotateX(-90deg) translateZ(150px);
}
/*定义小正方体样式*/
.cube span{
	display: bloack;
	width: 200px;
	height: 200px;
	position: absolute;
	top: 50px;
	left: 50px;
}
.cube .in_pic{
	width: 200px;
	height: 200px;
}
.cube .in_front{
	transform: rotateY(0deg) translateZ(100px);
}
.cube .in_back{
	transform: translateZ(-100px) rotateY(180deg);
}
.cube .in_left{
	transform: rotateY(90deg) translateZ(100px);
}
.cube .in_right{
	transform: rotateY(-90deg) translateZ(100px);
}
.cube .in_top{
	transform: rotateX(90deg) translateZ(100px);
}
.cube .in_bottom{
	transform: rotateX(-90deg) translateZ(100px);
}
/*鼠标移入后样式*/
.cube:hover .out_front{
	transform: rotateY(0deg) translateZ(400px);
}
.cube:hover .out_back{
	transform: translateZ(-400px) rotateY(180deg);
}
.cube:hover .out_left{
	transform: rotateY(90deg) translateZ(400px);
}
.cube:hover .out_right{
	transform: rotateY(-90deg) translateZ(400px);
}
.cube:hover .out_top{
	transform: rotateX(90deg) translateZ(400px);
}
.cube:hover .out_bottom{
	transform: rotateX(-90deg) translateZ(400px);
}
</style>