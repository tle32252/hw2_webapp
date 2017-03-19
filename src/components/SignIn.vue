<template>
  <div class="sign-in">
    <h1>Sign In</h1>
    <label>Username</label>
    <el-input
  placeholder="E-mail"
  icon="search"
  v-model="email">
</el-input>




    <br></br>
    <label>Password</label>
    <el-input
  placeholder="password"
  icon="search"
  v-model="password"
  type="password">
</el-input>

    <br></br>
    <el-button type="success" @click.native="login">Login</el-button>
  </div>
</template>

<script>
import UsersApi from '../api/users.js'
import router from '../router'

export default {
  name: 'sign-in',
  data () {
    return {
      email: 'u5680913@iccs340.com',
      password: 'u5680913'
    }
  },
  methods: {
    login () {
      console.log('methods.login')
      UsersApi.login(this.email, this.password, function (_response) {
        // NOTE: Posts.index is not yet implemented
        router.push({ name: 'Posts.index' })
      })
    }
  }
}
</script>

<style scoped>
</style>
