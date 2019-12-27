<template>
 <div>
   <div class="all">
     <div v-for="(item,index) in menu" :key="index" class="for" @mouseenter="mouseenter(index)" @mouseleave="mouseleave(index)">
        <i class="iconfont" :class="icons[index].icon" :style="{color:icons[index].color}"></i>
        <div class="name">{{item.name}}</div>
        <img src="../../assets/images/right.png" alt="" class="right">
     </div>
     <div class="outbox" v-if="enter===true" @mouseenter="mouseenter1" @mouseleave="mouseleave">
        <div v-for="(item,index) in menu[checkindex].child" :key="index" class="child">
          <div class="top">
            <div class="title">{{item.title}}</div>
            <div class="right">
              <div class="font">更多</div>
              <img src="../../assets/images/right.png" alt="">
            </div>
          </div>
          <div class="title">
            <div v-for="(item1,index1) in item.child" :key="index1" class="name">
              <div class="font">{{item1}}</div>
            </div>
          </div>
        </div>
      </div>
   </div>
 </div>
</template>

<script>
 export default {
   props:{
     menu:{
       type:Array,
       default:()=>[]
     }
   },
   data () {
     return {
       checkindex:null,
       enter:false,
       icons:[
         {icon:"iconfood",color:"#ff8200"},
         {icon:"iconwaimai",color:"#ffb500"},
         {icon:"iconHotel",color:"#9B5E3E"},
         {icon:"iconzhenguo",color:"#ffb500"},
         {icon:"iconArtboard",color:"#ff3d00"},
         {icon:"iconjiaotong-lunchuan",color:"#03A9F4"},
         {icon:"iconktv",color:"#00BF96"},
         {icon:"iconlife",color:"#00BF96"},
         {icon:"iconliren",color:"#FF4081"},
         {icon:"iconmarried",color:"#FF4081"},
         {icon:"iconchild",color:"#FF4081"},
         {icon:"iconsport",color:"#03A9F4"},
         {icon:"icondecorate",color:"#00BF96"},
         {icon:"iconeducation",color:"#00BF96"},
         {icon:"iconmedical",color:"#03A9F4"},
         {icon:"iconbar",color:"#00BF96"}
       ]
     }
   },
   components: {

   },
   methods: {
    //  getmenu(){
    //    this.$axios.get('menu').then(res=>{
    //        this.menu=res.data.data.menu
    //        console.log(this.menu)
    //    }).catch(err=>{
    //      console.log(err)
    //    })
    //  },
     mouseenter(index){
       this.checkindex=index
       this.enter=true
     },
     mouseenter1(){
       this.enter=true
     },
     mouseleave(index){
       this.enter=false
     },
     mouseleave(){
       this.enter=false
     }
   },
   mounted() {
    // this.getmenu()
   },
   watch: {

   },
   computed: {
      
   }
 }
</script>

<style scoped lang='scss'>
  .all{
    width: 100%;
    padding: 10px 0 0 0;
    position: relative;
    .for{
      width: 228px;
      height: 26px;
      position: relative;
      display: flex;
      padding: 2px 12px;
      align-items: center;
      .name{
        padding-left: 10px;
        font-size: 13px;
      }
      .right{
        position: absolute;
        width: 12px;
        height: 12px;
        right: 12px;
      }
      &:hover{
        .name{
          font-weight: 700;
        }
        background: #fcf3d7;
      }
    }
  }
  .outbox{
    position: absolute;
    width: 400px;
    height: 415px;
    top: 10px;
    left: 228px;
    z-index: 100;
    background: white;
    .child{
      width: 86%;
      margin: 0 6%;
      .top{
        width: 100%;
        height: 50px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        border-bottom: 1px solid #E5E5E5;
        .title{
          font-size: 20px;
        }
        .right{
          display: flex;
          width: 50px;
          align-items: center;
          justify-content: flex-end;
          .font{
            font-size: 12px;
            color: #999;
          }
          img{
            width: 12px;
            height: 12px;
          }
        }
      }
      .title{
        width: 100%;
        display: flex;
        flex-wrap: wrap;
        .name{
          padding: 5px 10px;
          .font{
            font-size: 10px;
            &:hover{
              color: #FE8C00;
            }
          }
        }
      }
    }
  }
</style>