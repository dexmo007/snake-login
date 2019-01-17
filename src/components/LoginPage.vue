<template>
  <div class="page">
    <div class="container">
      <div class="left">
        <div class="login">Login</div>
        <div
          class="eula"
        >By logging in you agree to the ridiculously long terms that you didn't bother to read</div>
      </div>
      <div class="right">
        <svg viewBox="0 0 320 300">
          <defs>
            <linearGradient
              inkscape:collect="always"
              id="linearGradient"
              x1="13"
              y1="193.49992"
              x2="307"
              y2="193.49992"
              gradientUnits="userSpaceOnUse"
            >
              <stop style="stop-color:#ff00ff;" offset="0" id="stop876"></stop>
              <stop style="stop-color:#ff0000;" offset="1" id="stop878"></stop>
            </linearGradient>
          </defs>
          <path
            d="m 40,120.00016 239.99984,-3.2e-4 c 0,0 24.99263,0.79932 25.00016,35.00016
            0.008,34.20084 -25.00016,35 -25.00016,35 h -239.99984 c 0,-0.0205 -25,4.01348
            -25,38.5 0,34.48652 25,38.5 25,38.5 h 215 c 0,0 20,-0.99604 20,-25 0,-24.00396
            -20,-25 -20,-25 h -190 c 0,0 -20,1.71033 -20,25 0,24.00396 20,25 20,25 h 168.57143"
          ></path>
        </svg>
        <form class="form" @submit.prevent="submitLogin" novalidate>
          <label for="email">Email</label>
          <input type="text" id="email" v-model="email" required ref="email" @focus="emailFocussed">
          <label for="password">Password</label>
          <input
            type="password"
            id="password"
            v-model="password"
            required
            @focus="passwordFocussed"
          >
          <input type="submit" id="submit" value="Submit" ref="submit" @focus="submitFocussed">
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import anime from 'animejs';

function animateFocus(current, offset, array) {
  if (current) current.pause();
  return anime({
    targets: 'path',
    strokeDashoffset: {
      value: offset,
      duration: 700,
      easing: 'easeOutQuart',
    },
    strokeDasharray: {
      value: array,
      duration: 700,
      easing: 'easeOutQuart',
    },
  });
}

export default {
  name: 'LoginPage',
  props: {},
  data() {
    return {
      current: null,
      email: '',
      password: '',
    };
  },
  methods: {
    emailFocussed() {
      this.current = animateFocus(this.current, 0, '240 1386');
    },
    passwordFocussed() {
      this.current = animateFocus(this.current, -336, '240 1386');
    },
    submitFocussed() {
      this.current = animateFocus(this.current, -730, '530 1386');
    },
    submitLogin() {
      this.$refs.submit.focus();
      setTimeout(() => {
        this.email = '';
        this.password = '';
        this.$refs.email.focus();
      }, 700);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.page {
  background: #e2e2e5;
  display: flex;
  flex-direction: column;
  height: 100%;
  position: absolute;
  place-content: center;
  width: 100%;
}
@media (max-width: 767px) {
  .page {
    height: auto;
    margin-bottom: 20px;
    padding-bottom: 20px;
  }
}
.container {
  display: flex;
  height: 320px;
  margin: 0 auto;
  width: 640px;
}
@media (max-width: 767px) {
  .container {
    flex-direction: column;
    height: 630px;
    width: 320px;
  }
}
.left {
  background: white;
  height: calc(100% - 40px);
  top: 20px;
  position: relative;
  width: 50%;
}
@media (max-width: 767px) {
  .left {
    height: 100%;
    left: 20px;
    width: calc(100% - 40px);
    max-height: 270px;
  }
}
.login {
  font-size: 50px;
  font-weight: 900;
  margin: 50px 40px 40px;
}
.eula {
  color: #999;
  font-size: 14px;
  line-height: 1.5;
  margin: 40px;
}
.right {
  background: #474a59;
  box-shadow: 0px 0px 40px 16px rgba(0, 0, 0, 0.22);
  color: #f1f1f2;
  position: relative;
  width: 50%;
}
@media (max-width: 767px) {
  .right {
    flex-shrink: 0;
    height: 100%;
    width: 100%;
    max-height: 350px;
  }
}
svg {
  position: absolute;
  width: 320px;
}
path {
  fill: none;
  stroke: url(#linearGradient);
  stroke-width: 4;
  stroke-dasharray: 240 1386;
}
.form {
  margin: 40px;
  position: absolute;
}
label {
  color: #c2c2c5;
  display: block;
  font-size: 14px;
  height: 16px;
  margin-top: 20px;
  margin-bottom: 5px;
}
input {
  background: transparent;
  border: 0;
  color: #f2f2f2;
  font-size: 20px;
  height: 30px;
  line-height: 30px;
  outline: none !important;
  width: 100%;
}
input::-moz-focus-inner {
  border: 0;
}
#submit {
  color: #707075;
  margin-top: 40px;
  transition: color 300ms;
}
#submit:focus {
  color: #f2f2f2;
}
#submit:active {
  color: #d0d0d2;
}
</style>
