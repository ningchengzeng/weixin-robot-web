<template>
    <div>
        <mu-appbar color="primary" title="用户注册">
          <mu-button slot="left" icon @click="goBack">
            <mu-icon value="keyboard_arrow_left"></mu-icon>
          </mu-button>
          <mu-button slot="right" flat  @click="submit">
              <mu-icon value="done"></mu-icon>
          </mu-button>
        </mu-appbar>
        <mu-form class="reg" ref="reg" :model="validateForm">
            <mu-form-item label="手机号码" prop="username" :rules="usernameRules">
              <mu-text-field v-model="validateForm.username" prop="username"></mu-text-field>
            </mu-form-item>
            <mu-form-item label="密码" prop="password" :rules="passwordRules">
                <mu-text-field type="password" v-model="validateForm.password" prop="password"></mu-text-field>
            </mu-form-item>
            <mu-form-item label="确认密码" prop="repassword" :rules="passwordReRules">
                <mu-text-field type="password" v-model="validateForm.repassword" prop="repassword"></mu-text-field>
            </mu-form-item>
            <mu-form-item class="agree" prop="isAgree" :rules="argeeRules">
              <mu-checkbox label="同意" v-model="validateForm.isAgree"></mu-checkbox>
              <a>用户协议</a>
            </mu-form-item>
          </mu-form>
    </div>
</template>

<script>
export default {
  name: 'Reg',
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
      passwordRegRules: [
        { validate: (val) => !!val, message: '必须填写密码'},
        { validate: (val) => val.length >= 3 && val.length <= 10, message: '密码长度大于3小于10'},
        { validate: (val, model) => model.password != val, message: '二次密码不相同'}
      ],
      argeeRules: [{ validate: (val) => !!val, message: '必须同意用户协议'}],
      validateForm: {
        username: '',
        password: '',
        repassword: '',
        isAgree: false
      }
    }
  },
  methods: {
    submit () {
      this.$refs.reg.validate().then((result) => {
        console.log('form valid: ', result)
      });
    },
    goBack (){
        this.$router.push('/')
    }
  }
}
</script>

<style>
.reg{
  padding: 20px;
}
</style>
