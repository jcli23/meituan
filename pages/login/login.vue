<template>
 <div>
    <div class="all">
      <div class="icon">
        <img src="../../assets/images/meituan.png" alt="">
      </div>
      <div class="main">
        <div class="img">
          <img src="//s0.meituan.net/bs/file/?f=fe-sso-fs:build/page/static/banner/www.jpg" alt="">
        </div>
        <div class="login_box">
          <div class="mode">
            <div class="left">账号登录</div>
            <div class="right">
              <div class="font">手机动态码登录</div>
              <img src="../../assets/images/phone.png" alt="">
            </div>
          </div>
          <div class="box1">
            <div class="left">
              <div class="font">+86</div>
              <img src="../../assets/images/right.png" alt="">
            </div>
            <input type="text" placeholder="手机号" class="input">
          </div>
        </div>
      </div>
    </div>
 </div>
</template>

<script>
 export default {
   data () {
     return {

     }
   },
   components: {

   },
   methods: {

   },
   mounted() {

   },
   watch: {

   },
   computed: {

   }
 }
</script>

<style scoped lang='scss'>
  .all{
    width: 100vw;
    height: 100vh;
    .icon{
      width: 980px;
      height: 54px;
      margin: 40px auto;
      img{
        width: 82px;
        height: 54px;
      }
    }
    .main{
      width: 980px;
      height: 370px;
      margin: 0 auto;
      display: flex;
      .img{
        width: 480px;
        height: 370px;
        img{
          width: 480px;
          height: 370px;
        }
      }
      .login_box{
        width: 270px;
        height: 370px;
        margin-left: 115px;
        .mode{
          width: 100%;
          height: 17px;
          display: flex;
          justify-content: space-between;
          margin-top: 100px;
          align-items: center;
          .left{
            font-size: 14px;
            color: #666;
          }
          .right{
            display: flex;
            width: auto;
            align-items: center;
            .font{
              font-size: 12px;
              color: #666;  
            }
            img{
              width: 14px;
              height: 14px;
              padding-left: 4px;
            }
          }
        }
        .box1{
          width: 100%;
          height: 36px;
          border: 1px solid #999;
          margin: 8px 0;
          display: flex;
          .left{
            width: 40px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            .font{
              font-size: 14px;
              height: 36px;
              line-height: 36px;
              width: auto;
            }
            img{
              width: 14px;
              height: 14px;
            }
          }
          .input{
            width: 230px;
            height: 32px;
            border: none;
            outline: none;
          }
        }
      }
    }
  }
</style>