<template>
  <div class="login">
    <p class="title">
      <span>Bank </span>
      Support Portal
    </p>
    <form action="" class="login-form" v-on:submit.prevent>
      <div class="container">
        <div class="input-wrap">
          <i class="fas fa-user"></i>
          <input type="email" class="input" placeholder="E-mail" v-model="email">
          <i v-show="validEmail" class="fas fa-check"></i>
          <i v-show="invalidEmail" class="fas fa-times"></i>
        </div>
        <label class="error" v-show="invalidEmail">Invalid E-mail</label>

        <div class="input-wrap">
          <i class="fas fa-lock"></i>
          <input type="password" class="input" placeholder="Password" v-model="pass">
          <i v-show="validPass" class="fas fa-check"></i>
          <i v-show="invalidPass" class="fas fa-times"></i>
        </div>
        <label class="error" v-show="invalidPass">Invalid Password</label>

        <div class="btn-wrap">
          <button class="btn" v-on:click="checkForm">Login</button>
          <p class="text">Forgot your password? 
            <a href="#" class="reset-pass">Reset it here.</a>
          </p>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'LoginForm',
  data() {
    return {
      email: '',
      pass: '',
      invalidEmail: false,
      invalidPass: false,
      validEmail: false,
      validPass: false
    }
  },
  methods: {
    checkForm() {
      this.checkLogin(this.email);
      this.checkPass(this.pass);   
      this.invalidEmail ? this.validEmail = false : this.validEmail = true;
      this.invalidPass ? this.validPass = false : this.validPass = true;
    },
    checkLogin(email) {
      let re = /.+@.+\..+/;
      return re.test(email) ? this.invalidEmail = false : this.invalidEmail = true
    },
    checkPass(pass){
      return pass == '' ? this.invalidPass = true : this.invalidPass = false
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .container {
    width: 295px;
    display: flex;
    flex-direction: column;
    margin: 0 auto;
  }

  .error,
  .fas {
    color:red;
    font-size: 14px;
  }

  .error {
    padding-top: 5px;
    padding-left: 0px;
  }

  .fa-check {
    color: green; 
  }

  .fa-check,
  .fa-times {
    margin-bottom: 15px;
    margin-left: 5px;
  }

  .fa-user,
  .fa-lock {
    position: absolute;
    bottom: 0;
    padding: 15px;
    font-size: 14px;
    color: #666;
  }

  .input-wrap {
    position: relative;
    display: flex;
    flex-direction: row;
    align-items: flex-end;
  }

  .btn-wrap
  {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }

  span {
    color: #2fa2c3;
    font-size: 41px;
    font-weight: bold;
  }

  .login {
    display: flex;
    align-items: center;
    flex-direction: column;
    color: #666;
  }

  .login-form {
    width: 440px;
    border: 1px solid #999;
    border-radius: 5px;
  }

  .input {
    width: 295px;
    height: 40px;
    margin-top: 34px;
    font-size: 14px;
    color: #666;
    padding-left: 35px;
    border: 1px solid #999;
    border-radius: 5px;
  }

  .btn {
    margin-top: 40px;
    margin-bottom: 20px;
    background-color: #2fa2c3;
    color: #fff;
    border: none;
    font-size: 18px;
    padding: 10px 30px;
    border-radius: 4px;
    letter-spacing: -0.18px;
  }

  .text {
    margin-bottom: 34px;
    font-size: 12px;
  }

  .reset-pass{
    text-decoration: none;
    color: #36a2c1;
  }
</style>
