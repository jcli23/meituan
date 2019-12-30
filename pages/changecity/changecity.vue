<template>
  <div>
    <toper></toper>
    <div class="top_header">
      <div class="main">
        <div class="main_center">
          <div class="left">
            <img src="../../assets/images/logo.png" alt="logo" />
          </div>
          <div class="center">
            <div class="top">
              <div class="input">
                <input type="text" placeholder="搜索商家或地点" />
              </div>
              <div class="right">
                <img src="../../assets/images/search.png" />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="cities">
      <div class="center">
         <cities></cities>
      </div>
    </div>
    <div class="all_bottom">
      <div class="center">
        <low></low>
      </div>
    </div>
  </div>
</template>

<script>
import toper from "../../components/top/index";
import low from "../../components/footer/index";
import cities from "../../components/cities/cities";
export default {
  data() {
    return {
      
    };
  },
  components: {
    toper,
    low,
    cities
  },
  methods: {
    
  },
  mounted() {
    
  },
  watch: {},
  computed: {}
};
</script>

<style scoped lang='scss'>
.top_header {
  width: 100%;
  height: 122px;
  background: white;
  .main {
    width: 100%;
    height: 122px;
    .main_center {
      max-width: 1190px;
      min-width: 960px;
      height: 122px;
      margin: 0 auto;
      display: flex;
      .left {
        width: 30%;
        height: 46px;
        margin-top: 28px;
        img {
          width: 122px;
        }
      }
      .center {
        width: 45%;
        margin-top: 28px;
        .top {
          width: 100%;
          display: flex;
          height: 40px;
          .input {
            width: 85%;
            height: 40px;
            padding-left: 10px;
            border: 1px solid #f2f2f2;
            border-right: none;
            border-radius: 6px 0 0 6px;
            input {
              width: 100%;
              height: 38px;
              border: none;
              outline: none;
            }
          }
          .right {
            width: 15%;
            height: 40px;
            display: flex;
            background: rgb(248, 204, 149);
            align-items: center;
            justify-content: center;
            border-radius: 0 6px 6px 0;
            img {
              width: 20px;
              height: 20px;
            }
          }
        }
      }
    }
  }
}
.cities{
  width: 100%;
  background: #f8f8f8;
  padding: 20px 0 40px 0;
  .center{
    width: 1190px;
    margin: 0 auto;
    background: white;
  }
}
.all_bottom{
  width: 100%;
  height: 659px;
  background: #f8f8f8;
  .center{
    width: 1190px;
    height: 659px;
    margin: 0 auto;
  }
}
</style>