<template>
 <div>
   <div class="top">
      <div class="top-main">
        <div class="left">
          <img src="../../assets/images/postion.png" alt="position" />
          <div>{{city}}</div>
          <div class="exchange" @click="changecity">切换城市</div>
          <div class="cities">
            <div>[</div>
            <div class="font1">新津县</div>
            <div class="font2">崇州</div>
            <div class="font3">彭州</div>
            <div>]</div>
          </div>
          <div class="register_login">
            <div v-if="username" class="login">{{username}}</div>
            <div class="login" v-else @click="login">立即登录</div>
            <div v-if="username" class="register" @click="outlogin">退出</div>
            <div class="register" v-else @click="register">注册</div>
          </div>
        </div>
        <div class="right">
          <div class="box1">
            <div class="font">我的美团</div>
            <div class="block">
              <div class="block_font">我的订单</div>
              <div class="block_font">我的收藏</div>
              <div class="block_font">抵用券</div>
              <div class="block_font">账户设置</div>
            </div>
          </div>
          <div class="box2">手机APP</div>
          <div class="box3">
            <div class="font">商家中心</div>
            <div class="block">
              <div class="block_font">美团餐饮商户中心</div>
              <div class="block_font">登录商家中心</div>
              <div class="block_font">美团智能收银</div>
              <div class="block_font">我想合作</div>
              <div class="block_font">手机免费开店</div>
              <div class="block_font">餐饮代理商招募</div>
              <div class="block_font">商家申请开票</div>
              <div class="block_font">免费合作美团排队</div>
            </div>
          </div>
          <div class="box4">
            <div class="font">美团规则</div>
            <div class="block">
              <div class="block_font">规则中心</div>
              <div class="block_font">规则目录</div>
              <div class="block_font">规则评议院</div>
            </div>
          </div>
          <div class="box5">
            <div class="font">网站规则</div>
            <div class="block">
              <div class="bigbox">
                <div class="one">
                  <div class="title">酒店旅游</div>
                  <div class="one_title">
                    <div v-for="(item,index) in hotelList" :key="index" class="box">
                      <div class="item">{{item}}</div>
                    </div>
                  </div>
                </div>
                <div class="two">
                  <div class="title">吃美食</div>
                  <div class="one_title">
                    <div v-for="(item,index) in foodList" :key="index" class="box">
                      <div class="item">{{item}}</div>
                    </div>
                  </div>
                </div>
                <div class="three">
                  <div class="title">看电影</div>
                  <div class="one_title">
                    <div v-for="(item,index) in movieList" :key="index" class="box">
                      <div class="item">{{item}}</div>
                    </div>
                  </div>
                </div>
                <div class="four">
                  <div class="title">手机应用</div>
                  <div class="one_title">
                    <div v-for="(item,index) in pic" :key="index" class="box">
                      <img :src="item" />
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
   data () {
     return {
        username:'',
        city:'',
        hotelList: [
        "国际机票",
        "火车票",
        "榛果民宿",
        "经济型酒店",
        "主题酒店",
        "商务酒店",
        "公寓",
        "豪华酒店",
        "客栈",
        "青年旅社",
        "度假酒店",
        "别墅",
        "农家院"
      ],
      foodList: ["烤鱼", "特色小吃", "烧烤", "自助餐", "火锅", "代金券"],
      movieList: [
        "热映电影",
        "热门影院",
        "热映电影口碑榜",
        "最受期待电影",
        "国内票房榜",
        "北美票房榜",
        "电影排行榜"
      ],
      pic: [
        "//s0.meituan.net/bs/fe-web-meituan/2d53095/img/appicons/meituan.png",
        "//s1.meituan.net/bs/fe-web-meituan/404d350/img/appicons/waimai.png",
        "//s0.meituan.net/bs/fe-web-meituan/404d350/img/appicons/zhenguo.png",
        "//s1.meituan.net/bs/fe-web-meituan/404d350/img/appicons/dianping.png",
        "//s1.meituan.net/bs/fe-web-meituan/404d350/img/appicons/maoyan.png"
      ]
     }
   },
   components: {

   },
   methods: {
     login(){
       this.$router.push('/login/login')
    },
    register(){
       this.$router.push('/register/register')
    },
    changecity(){
       this.$router.push('/changecity/changecity')
    },
    getuser(){
      this.username=localStorage.getItem('username')
    },
    setcity(){
      if(localStorage.getItem('city')){
        this.city=localStorage.getItem('city')
      }else{
        localStorage.setItem('city',this.location)
      }
    },
    getcity(){
      this.city=localStorage.getItem('city')
    },
    outlogin(){
      localStorage.removeItem('username')
      this.getuser()
    }
   },
   mounted() {
     this.getuser()
     this.setcity()
     this.getcity()
   },
   watch: {

   },
   computed: {
     location(){
       return this.$store.state.city.replace("市","")
     }
   }
 }
</script>

<style scoped lang='scss'>
   .top {
  width: 100%;
  height: 40px;
  background: #f8f8f8;
  .top-main {
    max-width: 1190px;
    min-width: 960px;
    height: 40px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    .left {
      height: 40px;
      display: flex;
      align-items: center;
      img {
        width: 12px;
        height: 12px;
      }
      .exchange {
        padding: 0 2px;
        margin: 0 4px;
        font-size: 12px;
        height: 18px;
        border: 1px solid #999;
        &:hover {
          color: #fe8c00;
        }
      }
      .cities {
        display: flex;
        font-size: 12px;
        .font1 {
          margin: 0 4px;
          &:hover {
            color: #fe8c00;
          }
        }
        .font2 {
          margin: 0 4px;
          &:hover {
            color: #fe8c00;
          }
        }
        .font3 {
          margin: 0 4px;
          &:hover {
            color: #fe8c00;
          }
        }
      }
      .register_login {
        margin: 0 0 0 15px;
        display: flex;
        .login {
          font-size: 12px;
          margin: 0 0 0 10px;
          color: #fe8c00;
        }
        .register {
          font-size: 12px;
          margin: 0 0 0 10px;
        }
      }
    }
    .right {
      height: 40px;
      display: flex;
      align-items: center;
      .box1 {
        .block {
          display: none;
          position: absolute;
          top: 40px;
          border: 1px solid #f2f2f2;
          border-top: none;
          .block_font {
            font-size: 12px;
            padding: 8px 12px;
            background: white;
            border-top: none;
            border-bottom: none;
            &:hover {
              color: #fe8c00;
            }
          }
        }
        .font {
          font-size: 12px;
          padding: 14px 12px;
          &:hover {
            color: #fe8c00;
            background: white;
          }
        }
        &:hover {
          .font {
            background: white;
          }
          .block {
            display: block;
          }
        }
      }
      .box2 {
        font-size: 12px;
        padding: 14px 12px;
        &:hover {
          color: #fe8c00;
        }
      }
      .box3 {
        position: relative;
        .block {
          display: none;
          position: absolute;
          top: 41px;
          right: 0;
          border: 1px solid #f2f2f2;
          border-top: none;
          .block_font {
            font-size: 12px;
            min-width: 120px;
            height: 36px;
            text-align: center;
            line-height: 36px;
            background: white;
            border-top: none;
            border-bottom: none;
            &:hover {
              color: #fe8c00;
            }
          }
        }
        .font {
          font-size: 12px;
          padding: 14px 12px;
          &:hover {
            color: #fe8c00;
            background: white;
          }
        }
        &:hover {
          .font {
            background: white;
          }
          .block {
            display: block;
          }
        }
      }
      .box4 {
        position: relative;
        .block {
          display: none;
          position: absolute;
          top: 43px;
          right: -1px;
          border: 1px solid #f2f2f2;
          border-top: none;
          background: white;
          .block_font {
            font-size: 12px;
            min-width: 80px;
            height: 36px;
            text-align: center;
            line-height: 36px;
            background: white;
            &:hover {
              color: #fe8c00;
            }
          }
        }
        .font {
          font-size: 12px;
          padding: 14px 12px;
          &:hover {
            color: #fe8c00;
            background: white;
          }
        }
        &:hover {
          .font {
            background: white;
          }
          .block {
            display: block;
          }
        }
      }
      .box5 {
        position: relative;
        z-index: 100;
        .block {
          display: none;
          width: 1190px;
          background: white;
          height: 300px;
          position: absolute;
          top: 43px;
          right: 1px;
          border: 1px solid #f2f2f2;
          border-top: none;
          .bigbox {
            display: flex;
            width: 100%;
            height: 400px;
            .one {
              width: 30%;
              .title {
                width: 100%;
                height: 80px;
                text-align: center;
                line-height: 80px;
                font-weight: 700;
                font-size: 14px;
              }
              .one_title {
                width: 70%;
                margin: 0 auto;
                display: flex;
                flex-wrap: wrap;
                .box {
                  width: 33%;
                  height: 30px;
                  line-height: 30px;
                  text-align: center;
                  .item {
                    font-size: 12px;
                    &:hover {
                      color: #fe8c00;
                    }
                  }
                }
              }
            }
            .two {
              width: 15%;
              .title {
                width: 100%;
                height: 80px;
                text-align: center;
                line-height: 80px;
                font-weight: 700;
                font-size: 14px;
              }
              .one_title {
                width: 100%;
                margin: 0 auto;
                display: flex;
                flex-wrap: wrap;
                .box {
                  width: 50%;
                  height: 30px;
                  line-height: 30px;
                  text-align: center;
                  .item {
                    font-size: 12px;
                    &:hover {
                      color: #fe8c00;
                    }
                  }
                }
              }
            }
          }
          .three {
            width: 15%;
            .title {
              width: 100%;
              height: 80px;
              text-align: center;
              line-height: 80px;
              font-weight: 700;
              font-size: 14px;
            }
            .one_title {
              width: 100%;
              margin: 0 auto;
              display: flex;
              flex-wrap: wrap;
              .box {
                width: 100%;
                height: 30px;
                line-height: 30px;
                text-align: center;
                .item {
                  font-size: 12px;
                  &:hover {
                    color: #fe8c00;
                  }
                }
              }
            }
          }
          .four {
            width: 40%;
            .title {
              width: 100%;
              height: 80px;
              text-align: center;
              line-height: 80px;
              font-weight: 700;
              font-size: 14px;
            }
            .one_title {
              width: 80%;
              margin: 40px 0 0 10%;
              display: flex;
              justify-content: space-around;
              flex-wrap: wrap;
              .box {
                width: 60px;
                height: 60px;
                img {
                  width: 100%;
                  height: 100%;
                }
              }
            }
          }
        }
        .font {
          font-size: 12px;
          padding: 14px 12px;
          &:hover {
            color: #fe8c00;
            background: white;
          }
        }
        &:hover {
          .font {
            background: white;
          }
          .block {
            display: block;
          }
        }
      }
    }
  }
}
</style>