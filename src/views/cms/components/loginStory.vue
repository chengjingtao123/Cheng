<template>
  <div class="login-box">
    <!-- 通过:rules="loginFormRules"来绑定输入内容的校验规则 -->
    <el-form :rules="loginFormRules" ref="loginForm" :model="loginForm" label-position="right" label-width="auto"
      show-message>
      <div class="login-title">私密不开放</div>
      <!-- <div style="margin-top: 5px"></div> -->
      <el-form-item label="用户名" prop="loginName">
        <el-col :span="22">
          <el-input type="text" v-model="loginForm.loginName"></el-input>
        </el-col>
      </el-form-item>
      <el-form-item label="密码" prop="loginPassword">
        <el-col :span="22">
          <el-input type="password" show-password v-model="loginForm.loginPassword"></el-input>
        </el-col>
      </el-form-item>
      <el-form-item>
        <div style="margin-right: 64px;"></el-button><el-button type="primary"
            @click="loginSubmit('loginForm')">登录</el-button></div>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
  export default {
    name: "login",
    data() {
      return {
        loginForm: {
          loginName: "",
          loginPassword: "",
        },
        // 表单验证，需要在 el-form-item 元素中增加 prop 属性
        loginFormRules: {
          loginName: [{ required: true, message: "账号不可为空", trigger: "blur" }],
          loginPassword: [{ required: true, message: "密码不可为空", trigger: "blur" }],
        },
      };
    },
    methods: {
      loginSubmit(formName) {
        // 判断账号和密码是否匹配
        if (this.loginForm.loginName === "admin" && this.loginForm.loginPassword === "asd3913087") {
          // 使用 vue-router 路由到指定页面，该方式称之为编程式导航
          this.$router.push("/components/cmsMyStory");
        } else {
          this.$message.error("账号或密码错误，请重新输入");
        }
      },
    },
  };
</script>

<style scoped>
  .login-box {
    border: 1px solid #DCDFE6;
    background-color: white;
    opacity: 0.8;
    width: 350px;
    margin: 0px auto;
    padding: 35px 35px 15px 35px;
    border-radius: 5px;
    text-align: center;
    -webkit-border-radius: 5px;
    -moz-border-radius: 5px;
    box-shadow: 0 0 25px palegreen;
  }

  .login-title {
    text-align: center;
    margin: 0 auto 40px auto;
    color: #66CD00;
    font-size: 30px;
    font-weight: bold;
  }
</style>