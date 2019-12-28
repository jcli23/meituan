<template>
  <div>
    <div class="all">
      <div class="icon">
        <img src="../../assets/images/meituan.png" alt />
      </div>
      <div class="main">
        <div class="img">
          <img src="//s0.meituan.net/bs/file/?f=fe-sso-fs:build/page/static/banner/www.jpg" alt />
        </div>
        <div class="login_box">
          <div class="warning" :class="toast===true? 'warning1':'warning'">
            <img src="../../assets/images/warning.png" alt />
            <div class="font">请输入正确的用户名和密码</div>
          </div>
          <div class="mode">
            <div class="left">账号登录</div>
            <div class="right">
              <div class="font">手机动态码登录</div>
              <img src="../../assets/images/phone.png" alt />
            </div>
          </div>
          <div class="box1" :class="checked1===true? 'border1':''">
            <div class="left">
              <div class="font">+86</div>
              <img src="../../assets/images/right.png" alt />
            </div>
            <input
              type="text"
              v-model="username"
              placeholder="用户名"
              class="input"
              @focus="write1"
              @blur="user(username)"
            />
          </div>
          <div class="box2" :class="checked2===true? 'border2':''">
            <div class="left">
              <img src="../../assets/images/lock.png" alt />
            </div>
            <input
              type="password"
              v-model="password"
              placeholder="密码"
              class="input"
              @focus="write2"
              @blur="lock(password)"
            />
          </div>
          <div class="forget">忘记密码?</div>
          <div class="button" @click="login">登录</div>
          <div class="nouser">
            <div class="font">还没有账号?</div>
            <div class="free">免费注册</div>
          </div>
          <div class="third">
            <div class="line"></div>
            <div class="font">用合作网站账号登录</div>
            <div class="line"></div>
          </div>
          <div class="icons">
            <img class="qq" src="../../assets/images/qq.png" alt />
            <img class="weibo" src="../../assets/images/weibo.png" alt />
          </div>
        </div>
      </div>
      <div class="bottom">
        <img src="../../assets/images/bottom.png" alt />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      checked1: null,
      checked2: null,
      username: "",
      toast: false,
      password: ""
    };
  },
  components: {},
  methods: {
    write1() {
      this.checked1 = true;
      this.checked2 = false;
      this.toast = false;
    },
    write2() {
      this.checked2 = true;
      this.checked1 = false;
    },
    user(e) {},
    lock(e) {},
    login() {
      let data = {};
      (data.username = this.username), (data.password = this.password);
      this.$axios
        .post(`users/login`, data)
        .then(res => {
          console.log(res);
          if (res.data.code === 200) {
            localStorage.setItem("username", this.username);
            this.$router.push("/");
            this.$Message.success("登录成功");
          } else {
            this.toast = true;
          }
        })
        .catch(err => {
          console.log(err);
        });
    }
  },
  mounted() {},
  watch: {},
  computed: {}
};
</script>

<style scoped lang='scss'>
.all {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  .icon {
    width: 980px;
    height: 54px;
    margin: 40px auto;
    img {
      width: 82px;
      height: 54px;
    }
  }
  .main {
    width: 980px;
    height: 370px;
    margin: 0 auto;
    display: flex;
    .img {
      width: 480px;
      height: 370px;
      img {
        width: 480px;
        height: 370px;
      }
    }
    .login_box {
      width: 270px;
      height: 370px;
      position: relative;
      margin-left: 115px;
      .warning {
        width: 100%;
        height: 36px;
        position: absolute;
        margin: 0 0 8px 0;
        background: #f3eee6;
        border: 1px solid #fe8c00;
        display: flex;
        display: none;
        img {
          width: 18px;
          height: 18px;
          margin: 9px;
        }
        .font {
          width: 224px;
          height: 36px;
          line-height: 36px;
        }
      }
      .warning1 {
        display: block;
        width: 100%;
        height: 36px;
        position: absolute;
        margin: 0 0 8px 0;
        background: #f3eee6;
        border: 1px solid #fe8c00;
        display: flex;
        img {
          width: 18px;
          height: 18px;
          margin: 9px;
        }
        .font {
          width: 224px;
          height: 36px;
          line-height: 36px;
        }
      }
      .mode {
        width: 100%;
        height: 17px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-top: 45px;
        .left {
          font-size: 14px;
          color: #666;
        }
        .right {
          display: flex;
          width: auto;
          align-items: center;
          .font {
            font-size: 12px;
            color: #666;
          }
          img {
            width: 14px;
            height: 14px;
            padding-left: 4px;
          }
        }
      }
      .box1 {
        width: 100%;
        height: 36px;
        border: 1px solid #999;
        margin: 8px 0;
        display: flex;
        align-items: center;
        .left {
          width: 40px;
          display: flex;
          justify-content: space-between;
          align-items: center;
          .font {
            font-size: 14px;
            height: 36px;
            line-height: 36px;
            width: auto;
          }
          img {
            width: 14px;
            height: 14px;
          }
        }
        .input {
          width: 230px;
          height: 32px;
          border: none;
          outline: none;
        }
      }
      .border1 {
        border: 1px solid #fe8c00;
      }
      .box2 {
        width: 100%;
        height: 36px;
        border: 1px solid #999;
        margin: 8px 0;
        display: flex;
        align-items: center;
        .left {
          width: 36px;
          height: 36px;
          display: flex;
          justify-content: center;
          align-items: center;
          img {
            width: 18px;
            height: 18px;
          }
        }
        .input {
          width: 234px;
          height: 32px;
          border: none;
          outline: none;
        }
      }
      .border2 {
        border: 1px solid #fe8c00;
      }
      .forget {
        width: 100%;
        height: 18px;
        line-height: 18px;
        text-align: right;
        margin: 0 0 8px 0;
        color: #fe8c00;
      }
      .button {
        width: 100%;
        height: 34px;
        margin: 8px 0;
        text-align: center;
        line-height: 34px;
        font-weight: 700;
        font-size: 14px;
        background: #ffbd00;
        border-radius: 5px;
      }
      .nouser {
        display: flex;
        width: 100%;
        height: 21px;
        .font {
          height: 21px;
          line-height: 21px;
          font-size: 14px;
        }
        .free {
          height: 21px;
          line-height: 21px;
          font-size: 14px;
          color: #fe8c00;
          padding-left: 5px;
        }
      }
      .third {
        display: flex;
        width: 100%;
        height: 21px;
        margin: 8px 0;
        align-items: center;
        .line {
          width: 60px;
          height: 1px;
          background: #ccc;
        }
        .font {
          width: 150px;
          height: 21px;
          line-height: 21px;
          text-align: center;
          font-size: 14px;
        }
      }
      .icons {
        width: 100%;
        display: flex;
        height: 18px;
        margin-top: 20px;
        justify-content: center;
        .qq {
          width: 18px;
          height: 18px;
          margin-right: 20px;
        }
        .weibo {
          width: 18px;
          height: 18px;
        }
      }
    }
  }
  .bottom {
    width: 980px;
    margin: 0 auto;
  }
}
</style>