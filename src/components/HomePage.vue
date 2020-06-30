<template>
  <div class="full-size">
    <el-container>
      <el-header>
        <div class="login-slogan">
          <a @click="showLogin">{{ msg }}</a> 
          {{ user.name }}
        </div>
      </el-header>
      <el-container>
        <el-aside width="200px">
        </el-aside>
        <el-main>
          <h1 class="header-style">商品统计管理系统</h1>
          <div class="login-form">
            <div v-if="flag">
              <input class="input-bg" type="text" v-model="account" placeholder="   账号" />
              <input class="input-bg" type="password" v-model="password" placeholder="   密码" />
              <input class="input-submit" type="submit" name="submit" value="提交" @click="login(account,password)" />
            </div>
          </div>
        </el-main>
        <el-aside width="200px">Aside</el-aside>
      </el-container>
      <el-footer>Footer</el-footer>
    </el-container>
  </div>
</template>

<script>
export default {
  name: 'HomePage',
  data () {
    return {
      msg: '登录',
      flag: false,
      account: '',
      password: '',
      user: {
        id: '',
        name: '',
        password: '',
        phone: '',
        isEnabled: 1,
        creator: '',
        createTime: '',
        lastModifier: '',
        lastModifierTime: '',
        sequence: 1
      },
      username: '111'
    }
  },
  methods: {
     showLogin () {
       this.flag = true
     },
     login (account,password) {
       var that = this;
       let data = {"id": account,"password": password};
       this.$axios.post("/apis/user/login", data)
       .then( res => {
        that.user = res.data
        that.flag = false
       });
     }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .full-size {
    height: 100%;
    background-image: url("../../build/pic/bg_homepage01.jpg");
    background-repeat: no-repeat;
    background-size: 100% 100%;
  }

  .el-header {
    /* background-color: #B3C0D1; */
    background-color: rgba(179,192,209, 0.6);
    color: #333;
    text-align: center;
    width: 100%;
    line-height: 6%;
  }

  .el-footer {
    /* background-color: #B3C0D1; */
    background-color: rgba(179,192,209, 0.6);
    color: #333;
    text-align: center;
    width: 100%;
    line-height: 6%;
  }
  
  .el-aside {
    /* background-color: #D3DCE6; */
    background-color: rgba(211,220,230, 0.6);
    color: #333;
    text-align: center;
    width: 20%;
    line-height: 88%;
  }
  
  .el-main {
    /* background-color: #E9EEF3; */
    background-color: rgba(233,238,243, 0.6);
    color: #333;
    text-align: center;
    width: 60%;
    line-height: 88%;
  }
  
  .el-container {
    height: 100%;
  }

  .header-style {
    line-height: 76%;
    color: rgb(7, 43, 77);
    font-size: 120px;
  }

  .login-slogan {
    margin-right: 66px;
    float: right;
    position: relative;
  }

  a {
    text-decoration: none;
    line-height: 360%;
  }

  a:hover {
    color: white;
    font-size: 120%;
  }

  .button-style {
    background: rgba(179,192,209, 0.6);
  }

  .input-bg {
    border: none;
    outline: none;
    border-radius: 16px;
    height: 26px;
    display: block;
    margin-top: 10px;
    margin-left: 260px;
    background-color: rgb(239, 244, 245);
    text-align: left;
  }

  .input-submit {
    border: none;
    outline: none;
    border-radius: 16px;
    width: 46px;
    height: 26px;
    display: block;
    margin-top: 36px;
    margin-left: 340px;
    background-color: rgb(239, 244, 245);
    text-align: center;
    line-height: 16px;
  }

  .login-form {
    margin-top: 120px;
  }
</style>
