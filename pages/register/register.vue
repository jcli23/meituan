<template>
  <div>
    <div class="all">
      <div class="top">
        <div class="center">
          <img src="../../assets/images/logo.png" alt />
          <div class="right">
            <div class="font">已有美团账号？</div>
            <div class="button">立即登录</div>
          </div>
        </div>
      </div>
      <div class="form">
        <div class="center">
          <Form ref="formValidate" :model="formValidate" :rules="ruleValidate" :label-width="120">
            <FormItem label="昵称" prop="username">
              <Input type="text" v-model="formValidate.username" />
            </FormItem>
            <FormItem label="邮箱" prop="email">
              <Input type="text" v-model="formValidate.email" />
            </FormItem>
            <FormItem label="密码" prop="password">
              <Input type="password" v-model="formValidate.password" />
            </FormItem>
            <FormItem label="确认密码" prop="confirm">
              <Input type="password" v-model="formValidate.confirm" />
            </FormItem>
            <FormItem label="验证码" prop="code">
              <Input type="text" v-model="formValidate.code" />
            </FormItem>
            <div class="getcode">发送验证码</div>
            <FormItem>
              <Button type="primary" @click="handleSubmit('formValidate')">同意以下协议并注册</Button>
            </FormItem>
          </Form>
        </div>
      </div>
      <div></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      formValidate: {
        username: "",
        email: "",
        password: "",
        confirm: "",
        code: ""
      },
      ruleValidate: {
        username: [
          {
            required: true,
            message: "请输入用户名,长度为4~12位",
            min: 4,
            max: 12,
            trigger: "blur"
          }
        ],
        email: [
          {
            required: true,
            message: "请输入邮箱",
            trigger: "blur"
          },
        ],
        password: [
          {
            required: true,
            message: "请输入密码,长度为6~12位",
            min: 6,
            max: 12,
            trigger: "blur"
          },
          
        ],
        confirm: [
          {
            required: true,
            message: "请确认密码",
            min: 6,
            max: 12,
            trigger: "blur"
          },
          
        ],
        code: [
          {
            required: true,
            message: "请输入验证码",
            trigger: "blur"
          }
        ]
      }
    };
  },
  components: {},
  methods: {
    handleSubmit(name) {
      this.$refs[name].validate(valid => {
        if (valid) {
        let data={}
        data.username=this.formValidate.username,
        data.password=this.formValidate.password
        this.$axios
        .post(`users/register`,data)
        .then(res => {
          console.log(res)
          this.$Message.success("注册成功");
          // this.$store.state.username=this.formValidate.username;
          this.$router.push('/login/login')
        })
        .catch(err => {
          console.log(err);
        });
        } else {
          this.$Message.error("注册失败，请填写注册信息");
        }
      });
    }
  },
  mounted() {},
  watch: {},
  computed: {}
};
</script>

<style scoped lang='scss'>
.all {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  .top {
    width: 100%;
    height: 50px;
    border-bottom: 1px solid #ffc300;
    .center {
      width: 700px;
      height: 100%;
      margin: 0 auto;
      display: flex;
      align-items: center;
      justify-content: space-between;
      img {
        height: 40px;
      }
      .right {
        display: flex;
        height: 50px;
        align-items: center;
        .button {
          width: 60px;
          height: 30px;
          text-align: center;
          line-height: 30px;
          color: white;
          font-size: 10px;
          background: #ffc300;
          border-radius: 3px;
        }
      }
    }
  }
  .form {
    width: 770px;
    margin: 0 auto;
    .center {
      width: 350px;
      padding-top: 30px;
      .getcode {
        width: 100px;
        height: 30px;
        line-height: 30px;
        text-align: center;
        border: 1px solid #f2f2f2;
        border-radius: 15px;
        margin-left: 120px;
        &:hover {
          border: 1px solid skyblue;
          color: skyblue;
        }
      }
      .confirm {
        margin-top: 20px;
        width: 140px;
        height: 30px;
        line-height: 30px;
        text-align: center;
        border-radius: 5px;
        margin-left: 120px;
        color: #333;
        background: #ffc300;
      }
    }
  }
}
</style>