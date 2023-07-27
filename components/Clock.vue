<template>
  <div id="app">
    <canvas ref="canvas"></canvas>
  </div>
</template>

<script>
export default {
  mounted() {
    const WINDOW_WIDTH = 450;
    const WINDOW_HEIGHT = 200;
    const RADIUS = 2.5; //球半径
    const NUMBER_GAP = 10; //数字之间的间隙
    const u = 0.65; //碰撞能量损耗系数
    const colors = ["#33B5E5", "#0099CC", "#AA66CC", "#9933CC", "#99CC00", "#669900", "#FFBB33", "#FF8800", "#FF4444", "#CC0000"]; //彩色小球的颜色
    const  digit =
                [
                    [
                        [0,0,1,1,1,0,0],
                        [0,1,1,0,1,1,0],
                        [1,1,0,0,0,1,1],
                        [1,1,0,0,0,1,1],
                        [1,1,0,0,0,1,1],
                        [1,1,0,0,0,1,1],
                        [1,1,0,0,0,1,1],
                        [1,1,0,0,0,1,1],
                        [0,1,1,0,1,1,0],
                        [0,0,1,1,1,0,0]
                    ],//0
                    [
                        [0,0,0,1,1,0,0],
                        [0,1,1,1,1,0,0],
                        [0,0,0,1,1,0,0],
                        [0,0,0,1,1,0,0],
                        [0,0,0,1,1,0,0],
                        [0,0,0,1,1,0,0],
                        [0,0,0,1,1,0,0],
                        [0,0,0,1,1,0,0],
                        [0,0,0,1,1,0,0],
                        [1,1,1,1,1,1,1]
                    ],//1
                    [
                        [0,1,1,1,1,1,0],
                        [1,1,0,0,0,1,1],
                        [0,0,0,0,0,1,1],
                        [0,0,0,0,1,1,0],
                        [0,0,0,1,1,0,0],
                        [0,0,1,1,0,0,0],
                        [0,1,1,0,0,0,0],
                        [1,1,0,0,0,0,0],
                        [1,1,0,0,0,1,1],
                        [1,1,1,1,1,1,1]
                    ],//2
                    [
                        [1,1,1,1,1,1,1],
                        [0,0,0,0,0,1,1],
                        [0,0,0,0,1,1,0],
                        [0,0,0,1,1,0,0],
                        [0,0,1,1,1,0,0],
                        [0,0,0,0,1,1,0],
                        [0,0,0,0,0,1,1],
                        [0,0,0,0,0,1,1],
                        [1,1,0,0,0,1,1],
                        [0,1,1,1,1,1,0]
                    ],//3
                    [
                        [0,0,0,0,1,1,0],
                        [0,0,0,1,1,1,0],
                        [0,0,1,1,1,1,0],
                        [0,1,1,0,1,1,0],
                        [1,1,0,0,1,1,0],
                        [1,1,1,1,1,1,1],
                        [0,0,0,0,1,1,0],
                        [0,0,0,0,1,1,0],
                        [0,0,0,0,1,1,0],
                        [0,0,0,1,1,1,1]
                    ],//4
                    [
                        [1,1,1,1,1,1,1],
                        [1,1,0,0,0,0,0],
                        [1,1,0,0,0,0,0],
                        [1,1,1,1,1,1,0],
                        [0,0,0,0,0,1,1],
                        [0,0,0,0,0,1,1],
                        [0,0,0,0,0,1,1],
                        [0,0,0,0,0,1,1],
                        [1,1,0,0,0,1,1],
                        [0,1,1,1,1,1,0]
                    ],//5
                    [
                        [0,0,0,0,1,1,0],
                        [0,0,1,1,0,0,0],
                        [0,1,1,0,0,0,0],
                        [1,1,0,0,0,0,0],
                        [1,1,0,1,1,1,0],
                        [1,1,0,0,0,1,1],
                        [1,1,0,0,0,1,1],
                        [1,1,0,0,0,1,1],
                        [1,1,0,0,0,1,1],
                        [0,1,1,1,1,1,0]
                    ],//6
                    [
                        [1,1,1,1,1,1,1],
                        [1,1,0,0,0,1,1],
                        [0,0,0,0,1,1,0],
                        [0,0,0,0,1,1,0],
                        [0,0,0,1,1,0,0],
                        [0,0,0,1,1,0,0],
                        [0,0,1,1,0,0,0],
                        [0,0,1,1,0,0,0],
                        [0,0,1,1,0,0,0],
                        [0,0,1,1,0,0,0]
                    ],//7
                    [
                        [0,1,1,1,1,1,0],
                        [1,1,0,0,0,1,1],
                        [1,1,0,0,0,1,1],
                        [1,1,0,0,0,1,1],
                        [0,1,1,1,1,1,0],
                        [1,1,0,0,0,1,1],
                        [1,1,0,0,0,1,1],
                        [1,1,0,0,0,1,1],
                        [1,1,0,0,0,1,1],
                        [0,1,1,1,1,1,0]
                    ],//8
                    [
                        [0,1,1,1,1,1,0],
                        [1,1,0,0,0,1,1],
                        [1,1,0,0,0,1,1],
                        [1,1,0,0,0,1,1],
                        [0,1,1,1,0,1,1],
                        [0,0,0,0,0,1,1],
                        [0,0,0,0,0,1,1],
                        [0,0,0,0,1,1,0],
                        [0,0,0,1,1,0,0],
                        [0,1,1,0,0,0,0]
                    ],//9
                    [
                        [0,0,0,0],
                        [0,0,0,0],
                        [0,1,1,0],
                        [0,1,1,0],
                        [0,0,0,0],
                        [0,0,0,0],
                        [0,1,1,0],
                        [0,1,1,0],
                        [0,0,0,0],
                        [0,0,0,0]
                    ]//:
                ];

    const canvas = this.$refs.canvas;
    const context = canvas.getContext("2d");

    canvas.width = WINDOW_WIDTH;
    canvas.height = WINDOW_HEIGHT;

    let currentDate = new Date();

    setInterval(() => {
      //清空整个Canvas，重新绘制内容
      context.clearRect(0, 0, context.canvas.width, context.canvas.height);
      drawDatetime(context);
    }, 50);

    function drawDatetime(cxt) {
      const nums = [];
      context.fillStyle = "#005eac";
      const date = new Date();
      let offsetX = 70, offsetY = 30;
      const hours = date.getHours();
      const num1 = Math.floor(hours / 10);
      const num2 = hours % 10;
      nums.push({ num: num1 });
      nums.push({ num: num2 });
      nums.push({ num: 10 }); //冒号
      const minutes = date.getMinutes();
      const num3 = Math.floor(minutes / 10);
      const num4 = minutes % 10;
      nums.push({ num: num3 });
      nums.push({ num: num4 });
      nums.push({ num: 10 }); //冒号
      const seconds = date.getSeconds();
      const num5 = Math.floor(seconds / 10);
      const num6 = seconds % 10;
      nums.push({ num: num5 });
      nums.push({ num: num6 });

          for (let x = 0; x < nums.length; x++) {
        const currentNum = nums[x].num;

        offsetX = drawSingleNumber(offsetX, offsetY, currentNum, cxt);

        //绘制彩色小球
        if (currentNums[x] !== undefined && currentNums[x] !== currentNum) {
          addBalls(nums[x].offsetX, offsetY);
        }
      }

      currentNums = nums;

      //绘制彩色小球
      for (let i = 0; i < balls.length; i++) {
        cxt.fillStyle = balls[i].color;
        cxt.beginPath();
        cxt.arc(balls[i].x, balls[i].y, RADIUS, 0, 2 * Math.PI);
        cxt.closePath();
        cxt.fill();
      }

      //更新彩色小球位置
      updateBallsPosition();
    }

    let currentNums = []; //当前的数字

    let balls = []; //彩色小球数组

   function drawSingleNumber(x, y, num, cxt) {
  cxt.fillStyle = colors[Math.floor(Math.random() * colors.length)];
  cxt.font = "9px Arial"; // 设置字体大小和字体样式

  for (let i = 0; i < digit[num].length; i++) {
    for (let j = 0; j < digit[num][i].length; j++) {
      if (digit[num][i][j] === 1) {
        cxt.beginPath();
        cxt.arc(
          x + j * 2 * (RADIUS + 1) + (RADIUS + 1),
          y + i * 2 * (RADIUS + 1) + (RADIUS + 1),
          RADIUS,
          0,
          2 * Math.PI
        );
        cxt.closePath();
        cxt.fill();
      }
    }
  }

  return x + digit[num][0].length * 2 * (RADIUS + 1);
}

    function addBalls(x, y) {
      for (let i = 0; i < digit[0].length; i++) {
        for (let j = 0; j < digit[0][i].length; j++) {
          if (digit[0][i][j] === 1) {
            let ball = {
              x: x + j * 2 * (RADIUS + 1) + (RADIUS + 1),
              y: y + i * 2 * (RADIUS + 1) + (RADIUS + 1),
              g: 1.5 + Math.random(),
              vx: Math.pow(-1, Math.ceil(Math.random() * 1000)) * 4,
              vy: -5,
              color: colors[Math.floor(Math.random() * colors.length)]
            };

            balls.push(ball);
          }
        }
      }
    }

    function updateBallsPosition() {
      for (let i = 0; i < balls.length; i++) {
        balls[i].x += balls[i].vx;
        balls[i].y += balls[i].vy;
        balls[i].vy += balls[i].g;

        if (balls[i].y >= WINDOW_HEIGHT - RADIUS) {
          balls[i].y = WINDOW_HEIGHT - RADIUS;
          balls[i].vy = -balls[i].vy * u;
        }
      }

      //移除已经离开画布的小球
      balls = balls.filter(ball => ball.x + RADIUS > 0 && ball.x - RADIUS < WINDOW_WIDTH);
    }
  }
};
</script>

<style scoped>
#app {
  text-align: center;
}
</style>

