<template>
  <div class="section dwo">
    <div class="container">
      <div class="row full-height justify-content-center">
        <div class="col-12 text-center align-self-center py-5">
          <div class="section pb-5 pt-5 pt-sm-2 text-center">
            <input class="checkbox" type="checkbox" id="reg-log" name="reg-log">
            <div class="card-3d-wrap mx-auto">
              <div class="card-3d-wrapper bgk">
                <div class="card-front">
                  <div class="center-wrap">
                    <div class="section text-center">
                      <h4 class="mb-4 pb-3">登录</h4>
                      <div class="form-group">
                        <input type="email" v-model="logEmail" class="form-style" placeholder="请输入电子邮箱" id="logemail" autocomplete="off">
                        <i class="fa fa-user-circle-o" aria-hidden="true"></i>
                      </div>
                      <div class="form-group mt-2">
                        <input type="password" v-model="logPass" class="form-style" placeholder="请输入密码" id="logpass" autocomplete="off">
                        <i class="fa fa-unlock-alt" aria-hidden="true"></i>
                      </div>
                      <a href="javascript:" class="btn mt-4" @click="login">登录</a>
                      <div class="d-flex justify-content-between mt-4 text-left">
                        <div class="flex-fill">
                          <p>没有帐号？<label for="reg-log" @click="toggleForm">立即注册</label></p>
                        </div>
                        <div class="flex-fill text-right">
                          <p><a href="javascript:" class="forgot link">忘记密码？</a></p>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div class="card-back">
                  <div class="center-wrap">
                    <div class="section text-center">
                      <h4 class="mb-4 pb-3">注册</h4>
                      <div class="form-group">
                        <input type="text" v-model="regName" class="form-style" placeholder="请输入用户名" id="regname" autocomplete="off">
                        <i class="fa fa-user-circle-o" aria-hidden="true"></i>
                      </div>
                      <div class="form-group mt-2">
                        <input type="email" v-model="regEmail" class="form-style" placeholder="请输入电子邮箱" id="regemail" autocomplete="off">
                        <i class="fa fa-envelope" aria-hidden="true"></i>
                      </div>
                      <div class="form-group mt-2">
                        <input type="password" v-model="regPass" class="form-style" placeholder="请输入密码" id="regpass" autocomplete="off">
                        <i class="fa fa-unlock-alt" aria-hidden="true"></i>
                      </div>
                      <a href="javascript:" class="btn mt-4" @click="register">注册</a>
                      <p class="mb-0 mt-4 text-center">已有帐号？<label for="reg-log" @click="toggleForm"> 立即登录 </label></p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      logEmail: '',
      logPass: '',
      regName: '',
      regEmail: '',
      regPass: '',
      isLoginForm: true
    }
  },
  methods: {
    login() {
      // 进行登录逻辑处理
      this.$router.push({name:'index'})
    },
    register() {
      // 进行注册逻辑处理
    },
    toggleForm() {
      this.isLoginForm = !this.isLoginForm;
    }
  },
  //  head() {
  //     return {
  //      'bootstrap/dist/css/bootstrap.css',
  //   'font-awesome/css/font-awesome.min.css'
  //     }
  //   }
}
</script>
<style scoped>
  @import 'bootstrap/dist/css/bootstrap.css';
  @import 'font-awesome/css/font-awesome.min.css';
</style>
  

<style lang="scss" scoped>
 
a {
    cursor: pointer;
    transition: all 200ms linear;
}
a:hover {
    text-decoration: none;
}
.link {
    color: #c4c3ca;
}
.link:hover {
    color: #ffeba7;
}
p {
    font-weight: 500;
    font-size: 14px;
    line-height: 1.7;
}
h4 {
    font-weight: 600;
}
h6 span {
    padding: 0 20px;
    text-transform: uppercase;
    font-weight: 700;
}
.section.dwo {
    position: relative;
    width: 100%;
    display: block;
    font-family: "Poppins", sans-serif;
    font-weight: 300;
    font-size: 15px;
    line-height: 1.7;
    color: #c4c3ca;
    background-color: #1f2029;
    overflow-x: hidden;
}
.full-height {
    min-height: 100vh;
}
[type="checkbox"]:checked,
[type="checkbox"]:not(:checked) {
    position: absolute;
    left: -9999px;
}
.checkbox:checked + label,
.checkbox:not(:checked) + label {
    position: relative;
    display: block;
    text-align: center;
    width: 60px;
    height: 16px;
    border-radius: 8px;
    padding: 0;
    margin: 10px auto;
    cursor: pointer;
    background-color: #ffeba7;
}
.checkbox:checked + label:before,
.checkbox:not(:checked) + label:before {
    position: absolute;
    display: block;
    width: 36px;
    height: 36px;
    border-radius: 50%;
    color: #ffeba7;
    background-color: #102770;
    font-family: "unicons";
    content: "\eb4f";
    z-index: 20;
    top: -10px;
    left: -10px;
    line-height: 36px;
    text-align: center;
    font-size: 24px;
    transition: all 0.5s ease;
}
.checkbox:checked + label:before {
    transform: translateX(44px) rotate(-270deg);
}

.card-3d-wrap {
    position: relative;
    width: 440px;
    max-width: 100%;
    height: 400px;
    -webkit-transform-style: preserve-3d;
    transform-style: preserve-3d;
    perspective: 800px;
    margin-top: 60px;
}
.card-3d-wrapper {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    -webkit-transform-style: preserve-3d;
    transform-style: preserve-3d;
    transition: all 600ms ease-out;
}
.card-front,
.card-back {
	width: 100%;
	height: 100%;
	background-color: #2a2b38;
	background-image: url("../../assets/pat.svg");
	background-position: bottom center;
	background-repeat: no-repeat;
	background-size: 300%;
	position: absolute;
	border-radius: 6px;
	left: 0;
	top: 0;
	-webkit-transform-style: preserve-3d;
	transform-style: preserve-3d;
	-webkit-backface-visibility: hidden;
	-moz-backface-visibility: hidden;
	-o-backface-visibility: hidden;
	backface-visibility: hidden;
	border: 1px solid #ffffff21;
}
.card-back {
    transform: rotateY(180deg);
}
.checkbox:checked ~ .card-3d-wrap .card-3d-wrapper {
    transform: rotateY(180deg);
}
.center-wrap {
    position: absolute;
    width: 100%;
    padding: 0 35px;
    top: 50%;
    left: 0;
    transform: translate3d(0, -50%, 35px) perspective(100px);
    z-index: 20;
    display: block;
}

.form-group {
    position: relative;
    display: block;
    margin: 0;
    padding: 0;
}
.form-style {
    padding: 13px 20px;
    padding-left: 55px;
    height: 48px;
    width: 100%;
    font-weight: 500;
    border-radius: 4px;
    font-size: 14px;
    line-height: 22px;
    letter-spacing: 0.5px;
    outline: none;
    color: #c4c3ca;
    background-color: #1f2029;
    border: none;
    -webkit-transition: all 200ms linear;
    transition: all 200ms linear;
    box-shadow: 0 4px 8px 0 rgba(21, 21, 21, 0.2);
}
.form-style:focus,
.form-style:active {
    border: none;
    outline: none;
    box-shadow: 0 4px 8px 0 rgba(21, 21, 21, 0.2);
}

.fa{
    position: absolute;
    top: 0;
    left: 18px;
    height: 48px;
    font-size: 24px;
    line-height: 48px;
    text-align: left;
    color: #ffeba7;
    -webkit-transition: all 200ms linear;
    transition: all 200ms linear;
}
.form-group input:-ms-input-placeholder {
    color: #c4c3ca;
    opacity: 0.7;
    -webkit-transition: all 200ms linear;
    transition: all 200ms linear;
}
.form-group input::-moz-placeholder {
    color: #c4c3ca;
    opacity: 0.7;
    -webkit-transition: all 200ms linear;
    transition: all 200ms linear;
}
.form-group input:-moz-placeholder {
    color: #c4c3ca;
    opacity: 0.7;
    -webkit-transition: all 200ms linear;
    transition: all 200ms linear;
}
.form-group input::-webkit-input-placeholder {
    color: #c4c3ca;
    opacity: 0.7;
    -webkit-transition: all 200ms linear;
    transition: all 200ms linear;
}
.form-group input:focus:-ms-input-placeholder {
    opacity: 0;
    -webkit-transition: all 200ms linear;
    transition: all 200ms linear;
}
.form-group input:focus::-moz-placeholder {
    opacity: 0;
    -webkit-transition: all 200ms linear;
    transition: all 200ms linear;
}
.form-group input:focus:-moz-placeholder {
    opacity: 0;
    -webkit-transition: all 200ms linear;
    transition: all 200ms linear;
}
.form-group input:focus::-webkit-input-placeholder {
    opacity: 0;
    -webkit-transition: all 200ms linear;
    transition: all 200ms linear;
}

.btn {
    border-radius: 4px;
    height: 44px;
    font-size: 13px;
    font-weight: 600;
    text-transform: uppercase;
    -webkit-transition: all 200ms linear;
    transition: all 200ms linear;
    padding: 0 30px;
    letter-spacing: 1px;
    display: -webkit-inline-flex;
    display: -ms-inline-flexbox;
    display: inline-flex;
    -webkit-align-items: center;
    -moz-align-items: center;
    -ms-align-items: center;
    align-items: center;
    -webkit-justify-content: center;
    -moz-justify-content: center;
    -ms-justify-content: center;
    justify-content: center;
    -ms-flex-pack: center;
    text-align: center;
    border: none;
    background-color: #ffeba7;
    color: #102770;
    box-shadow: 0 8px 24px 0 rgba(255, 235, 167, 0.2);
}

.btn:hover {
    background-color: #f3d97f;
    color: #061f6e;
    box-shadow: 0 8px 24px 0 rgba(16, 39, 112, 0.2);
}

.logo {
    position: absolute;
    top: 30px;
    right: 30px;
    display: block;
    z-index: 100;
    transition: all 250ms linear;
}
.logo img {
    height: 26px;
    width: auto;
    display: block;
}
label {
    margin-bottom: 0;
    cursor: pointer;
}
label:hover {
    color: #ffeba7;
}

.bgk {
 
  background-color: #151823;
  animation: textColor 10s ease infinite;
}
.bgk:after {
  position: absolute;
  content: "";
  top: 1vw;
  left: 0;
  right: 0;
  z-index: -1;
  height: 100%;
  width: 100%;
  margin: 0 auto;
  transform: scale(0.78);
  -webkit-filter: blur(2vw);
  background: linear-gradient(270deg, #0fffc1, #7e0fff);
  background-size: 150% 150%;
  animation: animateGlow 10s ease infinite;
}
@keyframes animateGlow {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
@keyframes textColor {
  0% {
    color: #7e0fff;
  }
  50% {
    color: #0fffc1;
  }
  100% {
    color: #7e0fff;
  }
}

</style>