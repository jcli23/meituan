<template>
  <div>
    <div class="all">
      <div class="op-area">
        <div class="left_font">按省份选择：</div>
        <div class="two_box">
          <div class="one">
            <div v-if="chooseprovince!==null" class="title">{{chooseprovince}}</div>
            <div v-else class="title">省份</div>
            <img src="../../assets/images/deep.png" alt class="box" @click="open1" />
            <div :class="lock1===false? 'city_box':'city_box2'">
              <div class="font">省份</div>
              <div class="main_name">
                <div v-for="(item,index) in province" :key="index" class="for">
                  <div class="name" @click="choosepro(item.name,item.id)">{{item.name}}</div>
                </div>
              </div>
            </div>
            <img v-if="lock1===true" src="../../assets/images/top_jiao.png" alt class="jiao" />
            <div class="line"></div>
          </div>
          <div class="two">
            <div v-if="choosecity!==null" class="title">{{choosecity}}</div>
            <div v-else class="title">城市</div>
            <img src="../../assets/images/deep.png" class="box" @click="open2" alt />
            <div :class="lock2===false? 'city_box':'city_box2'">
              <div class="font">城市</div>
              <div class="main_name">
                <div v-for="(item,index) in cities" :key="index" class="for">
                  <div class="name" @click="choosepro2(item.name)">{{item.name}}</div>
                </div>
              </div>
            </div>
            <img v-if="lock2===true" src="../../assets/images/top_jiao.png" alt class="jiao" />
            <div v-if="lock2===true" class="line"></div>
          </div>
        </div>
        <div class="search">
          <div class="font">直接搜索：</div>
          <div class="input">
            <input v-model="value" placeholder="请输入城市中文或拼音" @input="searchvalue(value)" @blur="searchvalue(value)" />
            <!-- <div class="resultbox" v-if="searchlist.length>0">
              <div v-for="(item,index) in searchlist" :key="index">
                <div>{{item}}</div>
              </div>
            </div> -->
          </div>
        </div>
      </div>
      <div class="hotcity">
        <div class="font">热门城市：</div>
        <div v-for="(item,index) in hotcity" :key="index" class="for">
          <div v-if="item.name==='市辖区'" class="title">{{item.province}}</div>
          <div v-else class="title">{{item.name}}</div>
        </div>
      </div>
      <div class="pysearch">
        <div class="font">按拼音首字母查找：</div>
        <div v-for="(item,index) in letter" :key="index" class="for">
          <a :href="'#'+item" class="letter">{{item}}</a>
        </div>
      </div>
      <div class="citylist" v-for="(item,index) in letter" :key="index">
        <div :id="item" class="letter">{{item}}</div>
        <div class="right">
          <div v-for="(item1,index1) in citylist[item]" :key="index1" class="for">
            <div class="name" @click="city(item1.name)">{{item1.name}}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import citylist from "../../assets/city";
export default {
  data() {
    return {
      province: [],
      chooseprovince: null,
      choosecity: null,
      value: "",
      lock1: false,
      lock2: false,
      id: 0,
      searchresult:[],
      cities: [],
      hotcity: [],
      citylist: {},
      letter: [
        "A",
        "B",
        "C",
        "D",
        "E",
        "F",
        "G",
        "H",
        "J",
        "K",
        "L",
        "M",
        "N",
        "P",
        "Q",
        "R",
        "S",
        "T",
        "W",
        "X",
        "Y",
        "Z"
      ]
    };
  },
  components: {},
  methods: {
    getprovince() {
      this.$axios
        .get(`province`)
        .then(res => {
          this.province = res.data.data.province;
          console.log(this.province);
        })
        .catch(err => {
          console.log(err);
        });
    },
    gethotcity() {
      this.$axios
        .get(`hotCity`)
        .then(res => {
          this.hotcity = res.data.data.hots;
          console.log(this.hotcity);
        })
        .catch(err => {
          console.log(err);
        });
    },
    getcities() {
      this.$axios
        .get(`citys/${this.id}`)
        .then(res => {
          this.cities = res.data.data.city;
          console.log(this.cities);
        })
        .catch(err => {
          console.log(err);
        });
    },
    open1() {
      this.lock1 = !this.lock1;
      this.lock2 = false;
    },
    open2() {
      if (this.chooseprovince !== null) {
        this.lock1 = false;
        this.lock2 = !this.lock2;
      }
    },
    choosepro(e, id) {
      (this.chooseprovince = e), (this.id = id), this.getcities();
      this.lock1 = false;
    },

    choosepro2(e) {
      (this.choosecity = e), localStorage.setItem("city", this.choosecity);
      localStorage.setItem("chooseprovince", this.chooseprovince);
      this.$router.push("/");
      this.lock2 = false;
    },
    city(e){
      localStorage.setItem("city",e);
      this.$router.push("/");
    },
    searchvalue(value){
       if(value.length>0){
         this.letter.map(item=>{
           this.citylist[item].map(item1=>{
             if(item1.spell.indexOf(value)>-1 ||item1.name.indexOf(value)>-1){
                this.searchresult.push(item1.name)
             }
           })
         })
       }
    }
  },
  mounted() {
    this.getprovince();
    this.gethotcity();
    this.citylist = citylist.data.cities;
  },
  watch: {},
  computed: {}
};
</script>

<style scoped lang='scss'>
.all {
  width: 100%;
  padding: 20px;
  .op-area {
    width: 100%;
    height: 40px;
    margin: 0 0 30px 0;
    display: flex;
    align-items: center;
    .left_font {
      font-size: 16px;
      color: #333;
    }
    .two_box {
      display: flex;
      width: 360px;
      height: 40px;
      .one {
        width: 150px;
        height: 40px;
        margin: 0 10px 0 20px;
        padding: 10px 0 10px 10px;
        position: relative;
        border: 1px solid #cdcdcd;
        border-radius: 4px;
        .title {
          font-size: 14px;
          color: #666;
          width: 120px;
        }
        .box {
          width: 8px;
          height: 8px;
          position: absolute;
          top: 16px;
          right: 10px;
        }
        .city_box {
          display: none;
          width: 264px;
          position: absolute;
          padding: 20px 0 20px 15px;
          border: 1px solid #cdcdcd;
          border-radius: 4px;
          left: 0;
          top: 48px;
          background: white;
          .font {
            width: 100%;
            height: 21px;
            margin: 0 0 11px 0;
            font-size: 16px;
            color: #ccc;
          }
          .main_name {
            width: 100%;
            display: flex;
            flex-wrap: wrap;
            .for {
              margin: 6px 0;
              .name {
                padding: 0 8px;
                height: 20px;
                line-height: 20px;
                color: #666;
              }
            }
          }
        }
        .city_box2 {
          display: block;
          width: 264px;
          position: absolute;
          padding: 20px 0 20px 15px;
          border: 1px solid #cdcdcd;
          border-radius: 4px;
          left: 0;
          top: 48px;
          background: white;
          .font {
            width: 100%;
            height: 21px;
            margin: 0 0 11px 0;
            font-size: 16px;
            color: #ccc;
          }
          .main_name {
            width: 100%;
            display: flex;
            flex-wrap: wrap;
            .for {
              margin: 6px 0;
              .name {
                padding: 0 8px;
                height: 20px;
                line-height: 20px;
                color: #666;
              }
            }
          }
        }
        .jiao {
          position: absolute;
          z-index: 100;
          width: 20px;
          height: 20px;
          top: 35px;
          left: 30px;
        }
        .line {
          width: 16px;
          height: 1px;
          background: white;
          position: absolute;
          left: 32px;
          top: 48px;
        }
      }
      .two {
        width: 150px;
        height: 40px;
        margin: 0 20px 0 10px;
        padding: 10px 0 10px 10px;
        position: relative;
        border: 1px solid #cdcdcd;
        border-radius: 4px;
        .title {
          font-size: 14px;
          color: #666;
          width: 100px;
        }
        .box {
          width: 8px;
          height: 8px;
          position: absolute;
          top: 16px;
          right: 10px;
        }
        .city_box {
          display: none;
          width: 264px;
          position: absolute;
          padding: 20px 0 20px 15px;
          border: 1px solid #cdcdcd;
          border-radius: 4px;
          left: 0;
          top: 48px;
          background: white;
          .font {
            width: 100%;
            height: 21px;
            margin: 0 0 11px 0;
            font-size: 16px;
            color: #ccc;
          }
          .main_name {
            width: 100%;
            display: flex;
            flex-wrap: wrap;
            .for {
              margin: 6px 0;
              .name {
                padding: 0 8px;
                height: 20px;
                line-height: 20px;
                color: #666;
              }
            }
          }
        }
        .city_box2 {
          display: block;
          width: 264px;
          position: absolute;
          padding: 20px 0 20px 15px;
          border: 1px solid #cdcdcd;
          border-radius: 4px;
          left: 0;
          top: 48px;
          background: white;
          .font {
            width: 100%;
            height: 21px;
            margin: 0 0 11px 0;
            font-size: 16px;
            color: #ccc;
          }
          .main_name {
            width: 100%;
            display: flex;
            flex-wrap: wrap;
            .for {
              margin: 6px 0;
              .name {
                padding: 0 8px;
                height: 20px;
                line-height: 20px;
                color: #666;
              }
            }
          }
        }
        .jiao {
          position: absolute;
          z-index: 100;
          width: 20px;
          height: 20px;
          top: 35px;
          left: 30px;
        }
        .line {
          width: 16px;
          height: 1px;
          background: white;
          position: absolute;
          left: 32px;
          top: 48px;
        }
      }
    }
    .search {
      display: flex;
      width: 310px;
      height: 40px;
      margin: 0 0 0 40px;
      align-items: center;
      .font {
        font-size: 16px;
        color: #333;
      }
      .input {
        width: 230px;
        height: 40px;
        border: 1px solid #cdcdcd;
        padding: 3px 0 3px 5px;
        border-radius: 4px;
        input {
          width: 100%;
          height: 100%;
          border: none;
          outline: none;
        }
      }
    }
  }
  .hotcity {
    width: 100%;
    height: 80px;
    padding: 30px 0;
    border-top: 1px solid #cdcdcd;
    border-bottom: 1px solid #cdcdcd;
    display: flex;
    align-items: center;
    .font {
      font-size: 16px;
      color: #333;
    }
    .for {
      margin: 0 20px;
      .title {
        color: #666;
        font-size: 14px;
      }
    }
  }
  .pysearch {
    width: 100%;
    height: 80px;
    padding: 30px 0;
    border-top: 1px solid #cdcdcd;
    display: flex;
    align-items: center;
    .font {
      font-size: 16px;
      color: #333;
    }
    .for {
      margin: 0 10px;
      width: 25px;
      height: 25px;
      text-align: center;
      line-height: 25px;
      .letter {
        font-size: 15px;
        color: #222;
        &:hover {
          color: #feb655;
        }
      }
    }
  }
  .citylist {
    width: 100%;
    padding: 13px 30px 13px 10px;
    display: flex;
    &:hover{
      background: #f8f8f8;
    }
    .letter{
      width: 40px;
      height: 40px;
      background: #ffd000;
      border-radius: 50%;
      text-align: center;
      line-height: 40px;
      font-size: 16px;
      color: #222;
    }
    .right{
      width: 1065px;
      display: flex;
      flex-wrap: wrap;
      .for{
        margin: 10px 20px;
        .name{
          font-size: 14px;
          &:hover {
          color: #feb655;
        }
        }
      }
    }
  }
}
</style>