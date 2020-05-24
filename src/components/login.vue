<template>
  <div class="login_container">
    <div class="login_box">
      <div class="left_box">
        <img class="heart_logo" src="../assets/images/heart.png" alt="heart logo" />
        <div class="msg">
          <p>梦想</p>
          <p>从这里出发</p>
        </div>
      </div>
      <div class="right_box">
        <el-form
          :model="loginForm"
          ref="loginForm"
          :rules="loginFormRules"
          label-width="100px"
          class="loginForm"
        >
          <el-form-item label="用户名:" prop="username">
            <el-input v-model="loginForm.username" prefix-icon="el-icon-user"></el-input>
          </el-form-item>
          <el-form-item label="密码:" prop="password">
            <el-input type="password" v-model="loginForm.password" prefix-icon="el-icon-lock"></el-input>
          </el-form-item>
          <el-form-item>
            <el-button type="primary" @click="submitForm">提交</el-button>
            <el-button type="info" @click="resetForm">重置</el-button>
          </el-form-item>
        </el-form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    data() {
      return {
        loginForm: {
          username: 'admin',
          password: '123456'
        },
        loginFormRules:{
            username:[
                { required: true, message: '请输入用户名称', trigger: 'blur' },
                { min: 3, max: 8, message: '长度在 3 到 8 个字符', trigger: 'blur' }
            ],
            password:[
                { required: true, message: '请输入用户密码', trigger: 'blur' },
                { min: 5, max: 16, message: '长度在 5 到 16 个字符', trigger: 'blur' }
            ]
        }
      };
    },
    methods: {
      submitForm() {
        this.$refs.loginForm.validate(async (valid) => {
          if (!valid) return;
          const {data:res} = await this.$http.post('login',this.loginForm);
          if(res.meta.status!==200) return this.$message.error('登陆失败！');
          this.$message.success('登陆成功！');
          window.sessionStorage.setItem('token',res.data.token);
          this.$router.push('/home');
        });
      },
      resetForm() {
        this.$refs.loginForm.resetFields();
      }
    }
};
</script>

<style lang="less" scoped>
.login_container {
  width: 100%;
  height: 100%;
  background-image: url("../assets/images/login-bg.png");
  background-size: cover;
  position: relative;
  .login_box {
    width: 830px;
    height: 350px;
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    margin: auto;
    display: flex;
    .left_box {
      width: 350px;
      height: 100%;
      background-color: #409eff;
      z-index: 200;
      border-radius: 10px;
      display: flex;
      .heart_logo {
        width: 200px;
        height: 200px;
        margin-top: 50px;
      }
      .msg {
        display: flex;
        flex-direction: column;
        color: #fff;
        margin-top: 160px;
        p {
          line-height: 30px;
        }
      }
    }
    .right_box {
      width: 370px;
      height: calc(100%-180)px;
      background-color: #fff;
      border-radius: 10px;
      margin-left: -20px;
      padding:100px 80px 80px 50px;
    }
  }
}
</style>