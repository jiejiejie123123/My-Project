<template>
  <div class="login-container">
    我是注册页面
    <el-form ref="form" :model="form" :rule="registerRule" class="login-form">
      <div class="title-container">
        <img src="/logo.png" alt="" srcset="" />
      </div>
      <!-- 邮箱 -->
      <el-form-item prop="email">
        <el-input
          ref="email"
          v-model="form.email"
          placeholder="邮箱"
          name="email"
        ></el-input>
      </el-form-item>
      <!-- 验证码 -->
      <el-form-item prop="emailcode">
          <div class="send=email-btn">
              <el-button type="primary" @click="sendCode">发送</el-button>
          </div>
        <el-input
          ref="emailcode"
          v-model="form.emailcode"
          placeholder="邮箱验证码"
          name="emailcode"
        ></el-input>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  layout: 'login',
  data() {
    return {
      form: {
        email: '1351655648@qq.com',
        emailcode:'',
      },
      registerRule:{

      }
    }
  },
  methods:{
     async sendCode(){
          let res = await this.$http.get('/user/sendcode?email='+this.form.email)
          if(res.data.code === 0){
              this.$notift({
                  title:res.data.msg,
                  type:'success'
              })
          }
      },
  }
}
</script>

<style>
</style>