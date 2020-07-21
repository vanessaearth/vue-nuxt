<template>
  <div>
    <el-form :model="form"
             :rules="rules">
      <el-form-item props="name">
        <i class="el-icon-email" />
        <el-input v-model="form.name" />
      </el-form-item>
      <el-form-item props="pwd">
        <i class="el-icon-lock" />
        <el-input v-model="form.pwd" />
      </el-form-item>
      <el-form-item props="captcha">
        <i class="el-icon-lock" />
        <el-input v-model="form.captcha" />
        <img :src="captchaUrl"
             alt=""
             @click="refreshCaptcha">
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      form: {
        name: '',
        pwd: '',
        captcha: ''
      },
      rules: {},
      captchaUrl: ''
    }
  },
  mounted () {
    this.refreshCaptcha()
  },
  methods: {
    refreshCaptcha () {
      this.captchaUrl = '/api/captcha?_t=' + new Date().getTime()
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
