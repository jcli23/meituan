<template>
  <div>
    <div class="all">
      <div class="left">
        <div class="banner">
          <Carousel autoplay loop class="for">
            <div v-for="(item,index) in banner" :key="index">
              <CarouselItem>
                <img :src="item.img" alt class="img" />
              </CarouselItem>
            </div>
          </Carousel>
        </div>
        <div class="bottom">
          <div class="left">
            <img src="//p0.meituan.net/codeman/843d7347cb20d945e4bc39b6403f0515182965.png" alt />
          </div>
          <div class="right">
            <img src="//p1.meituan.net/codeman/16442c19da1f1c4544f794e29d99c92051716.jpg" alt />
          </div>
        </div>
      </div>
      <div class="center">
        <div class="top">
          <img src="//p0.meituan.net/codeman/e473bb428f070321269b23370ff02ba956209.jpg" alt />
        </div>
        <div class="bottom1">
          <img src="//p1.meituan.net/codeman/5b21cddb4bb1cbc3a9c3bce0f726c75940469.jpg" alt />
        </div>
      </div>
      <div class="right">
        <div class="top">
          <div class="img">
            <img src="//s0.meituan.net/bs/fe-web-meituan/2d05c2b/img/avatar.jpg" alt="">
          </div>
          <div class="hi">HI!您好</div>
          <div class="register" @click="register">注册</div>
          <div class="login" @click="login">立即登录</div>
        </div>
        <div class="bottom">
          <div class="img">
            <img src="//s1.meituan.net/bs/fe-web-meituan/60ac9a0/img/download-qr.png" alt="">
          </div>
          <div class="app">美团APP手机版</div>
          <div class="font">
            <div class="red">1元起</div>
            <div class="none">吃喝玩乐</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
 props:{
     banner:{
       type:Array,
       default:()=>[]
     }
   },
  data() {
    return {
      
    };
  },
  components: {},
  methods: {
    login(){
      this.$router.push('/login/login')
    }
  },
  mounted() {
    
  },
  watch: {},
  computed: {}
};
</script>

<style scoped lang='scss'>
.all {
  width: 950px;
  height: 425px;
  display: flex;
  .left {
    width: 550px;
    height: 425px;
    .banner {
      padding-top: 10px;
      width: 100%;
      height: 240px;
      .for {
        width: 100%;
        height: 240px;
      }
      .img {
        width: 100%;
        height: 240px;
        display: block;
      }
    }
    .bottom {
      width: 100%;
      height: 165px;
      display: flex;
      margin-top: 10px;
      .left {
        width: 270px;
        height: 165px;
        position: relative;
        top: 10px;
        img {
          width: 100%;
          height: 100%;
        }
      }
      .right {
        width: 270px;
        height: 165px;
        position: relative;
        top: 10px;
        left: 10px;
        img {
          width: 100%;
          height: 100%;
        }
      }
    }
  }
  .center {
    width: 150px;
    height: 425px;
    margin: 0 10px;
    .top {
      width: 150px;
      height: 240px;
      margin-top: 10px;
      img {
        width: 150px;
        height: 240px;
      }
    }
    .bottom1 {
      width: 150px;
      height: 165px;
      margin-top: 10px;
      img {
        width: 150px;
        height: 165px;
      }
    }
  }
  .right{
    width: 228px;
    height: 425px;
    .top {
      width: 228px;
      height: 240px;
      margin-top: 10px;
      background: white;
      .img {
        width: 228px;
        height: 60px;
        padding-top: 30px;
        display: flex;
        align-items: center;
        justify-content: center;
        img{
          width: 55px;
          height: 55px;
          border-radius: 50%;
        }
      }
      .hi{
          width: 100%;
          font-size: 16px;
          text-align: center;
          margin-top: 20px;
      }
      .register{
        width: 120px;
        height: 40px;
        text-align: center;
        line-height: 40px;
        font-size: 14px;
        margin: 10px 54px 15px;
        border: 1px solid #E5E5E5;
        border-radius: 20PX;
        &:hover{
          background: rgb(253, 251, 244);
        }
      }
      .login{
        width: 120px;
        height: 40px;
        text-align: center;
        font-size: 14px;
        line-height: 40px;
        margin: 10px 54px 15px;
        border: 1px solid #E5E5E5;
        border-radius: 20PX;
        &:hover{
          background: rgb(253, 251, 244);
        }
      }
    }
    .bottom{
      width: 228px;
      height: 165px;
      background: white;
      margin-top: 10px;
      .img{
        width: 100px;
        height: 100px;
        margin: 0 auto;
        padding-top: 10px;
        img{
          width: 95px;
          height: 95px;
        }
      }
      .app{
        width: 228px;
        height: 21px;
        line-height: 21px;
        text-align: center;
        font-size: 16px;
        color: #222;
        margin-top: 10px;
      }
      .font{
        width: 228px;
        height: 16px;
        display: flex;
        align-items: center;
        margin-top: 4px;
        justify-content: center;
        .red{
          font-size: 12px;
          color: rgb(245, 198, 127);
        }
        .none{
          font-size: 12px;
          padding-left: 5px;
        }
      }
    }
  }
}
@media screen and (max-width: 1200px) {
  .all {
    width: 710px;
    height: 425px;
    background: white;
    .left{
      width: 470px;
      .bottom .left{
        width: 230px;
      }
      .bottom .right{
        width: 220px;
      }
    }
    .center{
      display: none;
    }
    .right{
      margin-left: 10px;
    }
  }
}
</style>