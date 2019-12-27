<template>
  <div>
    <div class="all">
      <div class="top">
        <div class="box">
          <div class="one">
            <div class="title">{{data1[0].title}}</div>
            <div v-for="(item,index) in data1[0].list" :key="index">
              <div class="font">{{item}}</div>
            </div>
          </div>
          <div class="two">
            <div class="title">{{data1[1].title}}</div>
            <div v-for="(item,index) in data1[1].list" :key="index">
              <div class="font">{{item}}</div>
            </div>
          </div>
        </div>
        <div class="box">
          <div class="one">
            <div class="title">{{data1[2].title}}</div>
            <div v-for="(item,index) in data1[2].list" :key="index">
              <div class="font">{{item}}</div>
            </div>
          </div>
        </div>
        <div class="box">
          <div class="one">
            <div class="title">{{data1[3].title}}</div>
            <div v-for="(item,index) in data1[3].list" :key="index">
              <div class="font">{{item}}</div>
            </div>
          </div>
          <div class="two">
            <div class="title">{{data1[4].title}}</div>
            <div v-for="(item,index) in data1[4].list" :key="index">
              <div class="font">{{item}}</div>
            </div>
          </div>
        </div>
        <div class="box">
          <div class="one">
            <div class="title">{{data1[5].title}}</div>
            <div v-for="(item,index) in data1[5].list" :key="index">
              <div class="font">{{item}}</div>
            </div>
          </div>
          <div class="two">
            <div class="title">{{data1[6].title}}</div>
            <div v-for="(item,index) in data1[6].list" :key="index">
              <div class="font">{{item}}</div>
            </div>
          </div>
          <div class="three">
            <div class="title">{{data1[7].title}}</div>
            <div v-for="(item,index) in data1[7].list" :key="index">
              <div class="font">{{item}}</div>
            </div>
          </div>
          <div class="four">
            <div class="title">{{data1[8].title}}</div>
            <div v-for="(item,index) in data1[8].list" :key="index">
              <div class="font">{{item}}</div>
            </div>
          </div>
        </div>
        <div class="box">
          <div class="one">
            <div class="title">{{data1[9].title}}</div>
            <div v-for="(item,index) in data1[9].list" :key="index">
              <div class="font">{{item}}</div>
            </div>
          </div>
          <div class="two">
            <div class="title">{{data1[10].title}}</div>
            <div v-for="(item,index) in data1[10].list" :key="index">
              <div class="font">{{item}}</div>
            </div>
          </div>
          <div class="three">
            <div class="title">{{data1[11].title}}</div>
            <div v-for="(item,index) in data1[11].list" :key="index">
              <div class="font">{{item}}</div>
            </div>
          </div>
          <div class="four">
            <div class="title">{{data1[12].title}}</div>
          </div>
          <div class="five">
            <div class="title">{{data1[13].title}}</div>
          </div>
        </div>
      </div>
      <div class="bottom">
        <div class="line">
          <div class="font1">©美团网团购 meituan.com</div>
          <div class="font">京ICP证070791号</div>
          <div class="font">京ICP备10211739号</div>
        </div>
        <div class="line">广播电视节目制作经营许可证（京）字第03889号</div>
        <div class="line">
          <div class="font">食品经营许可证</div>
          <div class="font">互联网药品信息服务资格证</div>
        </div>
        <div class="line">医疗器械网络交易服务第三方平台备案：（京）网械平台备字[2018]第00004号</div>
        <div class="righter">
          <div class="toper">京公网安备11010502025545号</div>
          <div class="bottomer">
            <img
              class="first"
              src="https://p1.meituan.net/travelcube/3e7f8a17e55bace814166b667618b459366061.png@76h_76w_2e"
              alt
            />
            <div class="font">北京三快科技有限公司</div>
            <img class="right" src="../../assets/images/over.png" alt />
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
      data1: [
        {
          title: "用户帮助",
          list: [
            "申请退款",
            "查看美团券密码",
            "常见问题",
            "用户协议",
            "隐私政策",
            "反诈骗公告",
            "消费者权益保障"
          ]
        },
        {
          title: "美团服务",
          list: [
            "美团外卖",
            "美团酒店",
            "猫眼电影",
            "美团配送",
            "美团云",
            "大众点评",
            "美团民宿",
            "无人配送"
          ]
        },
        {
          title: "商家合作",
          list: [
            "美团餐饮商户中心",
            "美食商家入驻(非外卖)",
            "美团外卖开店申请",
            "美团收银官网",
            "外卖配送加盟申请",
            "美团点评餐饮学院",
            "酒店商家入驻",
            "境内度假商家入驻",
            "综合商家入驻",
            "美团民宿房东商家入驻",
            "商家开票申请",
            "美团点评智能收银机",
            "美团点评餐饮开放平台",
            "美团点评收单",
            "免费使用美团排队",
            "快驴进货商家合作",
            "美团闪购商家入驻"
          ]
        },
        {
          title: "代理商加盟",
          list: [
            "美团外卖代理商招募",
            "到店餐饮代理商招募",
            "非餐饮代理商招募",
            "美团联盟",
            "美团收银招募线上分销商",
            "美团点评5S服务商招募",
            "美团收单渠道代理商招募"
          ]
        },
        {
          title: "美团规则",
          list: ["规则中心", "规则目录", "规则评议院"]
        },
        {
          title: "关注美团",
          list: ["美团新浪微博"]
        },
        {
          title: "公司信息",
          list: [
            "关于我们",
            "投资者关系",
            "加入我们",
            "商户诚信公约及管理办法",
            "保险经纪资质"
          ]
        },
        {
          title: "廉正举报",
          list: ["廉政邮箱"]
        },
        {
          title: "知识产权",
          list: ["知识产权维权平台"]
        },
        {
          title: "消费者服务热线",
          list: [
            "外卖消费者：10109777",
            "猫眼消费者：10105335",
            "其他消费者：10107888"
          ]
        },
        {
          title: "商家服务热线",
          list: [
            "外卖&餐饮商家：10105557",
            "休闲娱乐、丽人、ktv、教育、结婚、亲子、家装等商家：10100107"
          ]
        },
        {
          title: "投诉举报热线",
          list: [
            "违法和不良信息举报电话：4006018900",
            "举报邮箱：tousujubao@meituan.com"
          ]
        },
        {
          title: "商家自助入驻美团入口"
        },
        {
          title: "供应商注册入口"
        }
      ]
    };
  },
  components: {},
  methods: {},
  mounted() {},
  watch: {},
  computed: {}
};
</script>

<style scoped lang='scss'>
.all {
  width: 100%;
  height: 100%;
  .top {
    width: 100%;
    height: 538px;
    border-top: 1px solid #999;
    padding: 40px 45px;
    display: flex;
    .box {
      flex: 1;
      height: 538px;
      .one {
        padding: 0 0 20px;
        .title {
          height: 28px;
          font-size: 14px;
          line-height: 28px;
          color: #333;
        }
        .font {
          font-size: 12px;
          line-height: 24px;
          color: #666;
          overflow: hidden;
          &:hover {
            color: #feb655;
          }
        }
      }
      .two {
        padding: 0 0 20px;
        .title {
          height: 28px;
          font-size: 14px;
          line-height: 28px;
          color: #333;
        }
        .font {
          font-size: 12px;
          line-height: 24px;
          color: #666;
          overflow: hidden;
          &:hover {
            color: #feb655;
          }
        }
      }
      .three {
        padding: 0 0 20px;
        .title {
          height: 28px;
          font-size: 14px;
          line-height: 28px;
          color: #333;
        }
        .font {
          font-size: 12px;
          line-height: 24px;
          color: #666;
          &:hover {
            color: #feb655;
          }
        }
      }
      .four {
        padding: 0 0 20px;
        .title {
          height: 28px;
          font-size: 14px;
          line-height: 28px;
          color: #333;
        }
        .font {
          font-size: 12px;
          line-height: 24px;
          color: #666;
          &:hover {
            color: #feb655;
          }
        }
      }
      .five {
        padding: 0 0 20px;
        .title {
          height: 28px;
          font-size: 14px;
          line-height: 28px;
          color: #333;
        }
      }
    }
  }
  .bottom {
    position: relative;
    width: 100%;
    height: 121px;
    padding: 15px 0 30px 20px;
    border-top: 1px solid #999;
    .line {
      width: 440px;
      height: 19px;
      display: flex;
      align-items: center;
      font-size: 12px;
      color: #999;
      &:hover {
        color: #feb655;
      }
      .font {
        font-size: 12px;
        color: #999;
        height: 19px;
        line-height: 19px;
        margin: 0 19px 0 0;
        &:hover {
          color: #feb655;
        }
      }
      .font1 {
        font-size: 12px;
        color: #999;
        height: 19px;
        line-height: 19px;
        margin: 0 19px 0 0;
      }
    }
    .righter {
      position: absolute;
      width: 497px;
      height: 68px;
      top: 15px;
      right: 0;
      .toper {
        font-size: 12px;
        color: #999;
        height: 19px;
        line-height: 19px;
        text-align: right;
        &:hover {
          color: #feb655;
        }
      }
      .bottomer {
        display: flex;
        .first {
          width: 38px;
          height: 38px;
        }
        .font {
          height: 38px;
          line-height: 38px;
          margin: 0 5px;
          &:hover {
            color: #feb655;
          }
        }
      }
    }
  }
}
</style>