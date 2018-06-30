<template>
    <div>
      <mu-appbar style="width: 100%;" color="primary">
        机器人登录
      </mu-appbar>
      <mu-form class="login" ref="login" :model="validateForm">
        <mu-form-item label="手机号码" prop="username" :rules="usernameRules">
          <mu-text-field v-model="validateForm.username" prop="username"></mu-text-field>
        </mu-form-item>
        <mu-form-item label="密码" prop="password" :rules="passwordRules">
            <mu-text-field type="password" v-model="validateForm.password" prop="password"></mu-text-field>
        </mu-form-item>
        <mu-form-item class="agree" prop="isAgree" :rules="argeeRules">
          <a @click="forget" class="forget">忘记密码？</a>
        </mu-form-item>
        <mu-form-item class="button">
          <mu-button color="primary" @click="submit">登录</mu-button>
          <mu-button @click="openReg">注册</mu-button>
        </mu-form-item>
      </mu-form>
    </div>
</template>

<script>
export default {
  name: 'Login',
  data () {
    return {
      usernameRules: [
        { validate: (val) => !!val, message: '必须填写手机号码'},
        { validate: (val) => val.length == 11, message: '手机号长度必须为11位'}
      ],
      passwordRules: [
        { validate: (val) => !!val, message: '必须填写密码'},
        { validate: (val) => val.length >= 3 && val.length <= 10, message: '密码长度大于3小于10'}
      ],
      validateForm: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    submit () {
      this.$refs.login.validate().then((result) => {
        console.log('form valid: ', result)
      });
    },
    openReg () {
       this.$router.push('/reg')
    },
    forget (){
      this.$router.push('/forget')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.login{
  padding: 20px;
}
.login .button{
  margin-bottom: 0px;
  padding-bottom: 0px;
}
.login .agree{
  padding-bottom: 5px;
  margin-bottom: 10px;
  height: 40px;
}
.login .agree .mu-form-item-label{
  display: none;
}
.login .forget{
  text-decoration: underline;
  position:absolute;
  left: 8px;
}
.login .mu-checkbox{
  margin-right:5px;
}
</style>
