<template>
  <div class="login-wrap">
    <el-form ref="form" :label-position="labelPosition" :model="userForm" label-width="80px">
      <el-form-item label="账号">
        <el-input v-model="userForm.username"></el-input>
      </el-form-item>
      <el-form-item label="密码">
        <el-input type="password" v-model="userForm.password"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="login">登录</el-button>
        <el-button>取消</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      labelPosition: 'top',
      userForm: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    async login () {
      const res = await axios.post('http://localhost:8888/api/private/v1/login', this.userForm)
      const data = res.data
      if (data.meta.status === 200) {
        this.$router.push({
          name: 'home'
        })
      }
      console.log(res)
    }
  }
}
</script>

<style>

</style>
