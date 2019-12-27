<template>
  <div>
    <div class="all">
      <div class="top">
        <div class="style">有格调</div>
        <div v-for="(item,index) in tablist" :key="index" class="for" @mouseenter="mouseenter(item.tab,index)">
          <div class="font">{{item.name}}</div>
          <div v-if="enter===index">
            <img src="../../assets/images/triangle.png" alt />
          </div>
        </div>
      </div>
      <div class="main">
        <div v-for="(item,index) in result" :key="index" class="for">
          <div v-if="index<6" class="box">
            <div v-if="item.photos.length>0">
              <img :src="item.photos[0].url" alt="">
            </div>
            <div v-else>
              <img src="//s1.meituan.net/bs/fe-web-meituan/60ac9a0/img/download-qr.png" alt="">
            </div>
            <div class="name">{{item.name}}</div>
            <div class="type">
              <div v-for="(item1,index1) in item.types" :key="index1" class="for">
                <div class="font">{{item1}}</div>
              </div>
            </div>
            <div class="price">
              <div class="icon">￥</div>
              <div v-if="item.biz_ext.cost.length>0" class="value">{{item.biz_ext.cost}}</div>
              <div v-else class="value">0</div>
              <div class="font">/起</div>
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
      city: "",
      keyword: "景点",
      enter:0,
      result:[],
      tablist: [
        {
          name: "全部",
          tab: "景点"
        },
        {
          name: "约会聚餐",
          tab: "美食"
        },
        {
          name: "丽人SPA",
          tab: "丽人"
        },
        {
          name: "电影演出",
          tab: "电影"
        },
        {
          name: "品质出游",
          tab: "旅游"
        }
      ]
    };
  },
  components: {},
  methods: {
    getstyle() {
      let city = this.location.replace("市", "");
      this.$axios
        .get(`results?city=${city}&keyword=${this.keyword}`)
        .then(res => {
          this.result=res.data.data.pois.slice(0,6);
          res.data.data.pois.map(item=>{
            item.types=item.type.split(';')
          })
        })
        .catch(err => {
          console.log(err);
        });
    },
    mouseenter(tab,index){
      this.keyword=tab
      this.enter=index
      this.getstyle()
    }
  },
  mounted() {
    this.getstyle();
  },
  watch: {},
  computed: {
    location() {
      return this.$store.state.city;
    }
  }
};
</script>

<style scoped lang='scss'>
.all {
  width: 100%;
  height: 694px;
  .top {
    width: 100%;
    height: 44px;
    background: #c0a866;
    border-radius: 5px 5px 0 0;
    display: flex;
    align-items: center;
    .style {
      font-size: 18px;
      color: #f8f8f8;
      padding: 0 5px;
      margin: 0 10px 0 13px;
      font-weight: 700;
    }
    .for {
      position: relative;
      height: 44px;
      .font {
        font-size: 14px;
        color: #f8f8f8;
        padding: 0 5px;
        line-height: 44px;
      }
      img {
        width: 10px;
        height: 10px;
        position: absolute;
        bottom: -2px;
        left: 50%;
        transform: translate(-50%);
      }
    }
  }
  .main{
    margin: 11px 10px 10px;
    width: 1170px;
    height: 628px;
    display: flex;
    flex-wrap: wrap;
    .for{
      width: 33%;
      height: 314px;
      padding: 10px;
      &:hover{
        background: #f8f8f8;
        border-radius: 10px;
      }
      .box{
        height: 294px;
        img{
          width: 100%;
          height: 208px;
          border-radius: 5px;
        }
        .name{
          width: 100%;
          height: 22px;
          font-size: 16px;
          line-height: 22px;
          text-overflow: ellipsis;
          margin: 8px 0;
        }
        .type{
          display: flex;
          flex-wrap: wrap;
          width: 100%;
          height: 20px;
          overflow: hidden;
          white-space: nowrap;
          text-overflow: ellipsis;
          .for{
            padding: 0 10px 5px 0;
            height: 20px;
            width: auto;
            .font{
              border: 1px solid #999;
              padding: 0 3px 0 3px;
              font-size: 12px;
            }
          }
        }
        .price{
          display: flex;
          align-items: center;
          .icon{
            font-size: 16px;
            color: #FEb655;
          }
          .value{
            font-size: 22px;
            color: #FEb655;
          }
          .font{
            font-size: 16px;
            color: #FEb655;
          }
        }
      }
    }
  }
}
</style>