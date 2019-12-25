<template>
 <div>
   <div class="main">
     <div class="main_center">
        <div class="left">
          <img src="../../assets/images/logo.png" alt="logo">
        </div>
        <div class="center">
          <div class="top">
            <div class="input">
              <input type="text" placeholder="搜索商家或地点">
            </div>
            <div class="right">
              <img src="../../assets/images/search.png">
            </div>
          </div>
          <div class="hot">
            <div v-for="(item,index) in results" :key="index" class="for">
              <div class="name">{{item.name}}</div>
            </div>
          </div>
        </div>
     </div>
     <div class="main_bottom">
       <div class="center">
         <div class="yellow">美团外卖</div>
         <div class="red">猫眼电影</div>
         <div class="red">美团酒店</div>
         <div class="yellow">民宿/公寓</div>
         <div class="yellow">商家入驻</div>
         <div class="red">美团公益</div>
       </div>
     </div>
   </div>
 </div>
</template>

<script>
 export default {
   data () {
     return {
       city:'',
       results:[]
     }
   },
   components: {

   },
   methods: {
     searchhot(){
       let city=this.location.replace("市","")
       this.$axios.get(`hotPlace?city=${city}`).then(res=>{
           this.results=res.data.data.result
           console.log(this.results)
       }).catch(err=>{
         console.log(err)
       })
     }
   },
   mounted() {
     this.searchhot()
   },
   watch: {

   },
   computed: {
     location(){
       return this.$store.state.city
     }
   }
 }
</script>

<style scoped lang='scss'>
  .main{
    width: 100%;
    height: 122px;
    .main_center{
      max-width: 1190px;
      min-width: 960px;
      height: 122px;
      margin: 0 auto;
      display: flex;
      .left{
        width: 30%;
        height: 46px;
        margin-top: 28px;
        img{
        width: 122px;
        }
      }
      .center{
        width: 45%;
        margin-top: 28px;
        .top{
          width: 100%;
          display: flex;
          height: 40px;
          .input{
            width: 85%;
            height: 40px;
            padding-left: 10px;
            border: 1px solid #f2f2f2;
            border-right: none;
            border-radius: 6px 0 0 6px;
            input{
              width: 100%;
              height: 38px; 
              border: none;
              outline: none;
            }
          }
          .right{
            width: 15%;
            height: 40px;
            display: flex;
            background: rgb(248, 204, 149);
            align-items: center;
            justify-content: center;
            border-radius: 0 6px 6px 0;
            img{
              width: 20px;
              height: 20px;
            }
          }
        }
        .hot{
          display: flex;
          padding: 8px 0 0 12px;
          width: 100%;
          height: 25px;
          flex-wrap: wrap;
          overflow: hidden;
          .for{
            padding: 0 10px 3px 0;
            white-space: nowrap;
            .name{
              font-size: 12px;
              &:hover{
                color: #FE8C00;
              }
            }
          }
        }
      }
    }
    .main_bottom{
      width: 100%;
      height: 35px;
      .center{
        height: 35px;
        max-width: 1190px;
        min-width: 960px;
        display: flex;
        margin: 0 auto;
        justify-content: center;
        .red{
          font-size: 16px;
          font-weight: 700;
          color: #222;
          margin: 0 20px;
          &:hover{
            color: rgb(241, 77, 48);
          }
        }
        .yellow{
          font-size: 16px;
          font-weight: 700;
          color: #222;
          margin: 0 20px;
          &:hover{
            color: rgb(202, 155, 24);
          }
        }
      }
    }
  }
</style>