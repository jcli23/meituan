<template>
  <div class="container">
    <toper></toper>
    <div class="top_header">
      <top_header></top_header>
    </div>
    <div class="page_index">
      <div class="center">
        <classification class="left" :menu="menu"></classification>
        <div class="center_center">
          <logo :banner="banner"></logo>
        </div>
      </div>
    </div>
    <div class="quality">
      <div class="center">
        <quality></quality>
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
import toper from "../components/top/index";
import top_header from "../components/top_header/index";
import classification from "../components/classification/index";
import logo from "../components/logo/index";
import quality from "../components/quality/index";
import low from "../components/footer/index";

export default {
  components: {
    toper,
    top_header,
    classification,
    logo,
    quality,
    low
  },
  data() {
    return {
      city: "",
      menu:[],
      banner:[],
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
    };
  },
  methods: {
    
  },
  mounted() {

  },
  async asyncData(cty) {
    let [menu, position, hotCity,city,banner] = await Promise.all([
      cty.$axios.get("menu"),
      cty.$axios.get("position"),
      cty.$axios.get("hotCity"),
      cty.$axios.get("city"),
      cty.$axios.get("banner")
    ]);
    // console.log(menu.data.data)
    // console.log(position.data.data)
    // console.log(hotCity.data.data)
    console.log(banner.data.data)
    cty.store.state.city = position.data.data.city;
    return {

      city: position.data.data.city.replace("市",""),
      menu:menu.data.data.menu,
      banner:banner.data.data
    };
  },
  computed: {
     
  },

};
</script>

<style scoped lang='scss'>
.top_header {
  width: 100%;
  height: 157px;
  background: white;
}
.page_index {
  width: 100%;
  height: 425px;
  background: #f8f8f8;
  .center {
    max-width: 1190px;
    min-width: 960px;
    height: 425px;
    display: flex;
    margin: 0 auto;
    .left {
      height: 425px;
      width: 228px;
      border: 1px solid #e5e5e5;
      border-top: none;
      background: white;
    }
    .center_center{
      margin-left: 10px;
    }
  }
}
.quality{
  width: 100%;
  height: 774px;
  background: #f8f8f8;
  display: flex;
  align-items: center;
  .center{
    width: 1190px;
    height: 694px;
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
@media screen and (max-width: 1200px){
  .quality .center{
    width: 960px;
  }
  .all_bottom .center{
    width: 960px;
  }
}
</style>
