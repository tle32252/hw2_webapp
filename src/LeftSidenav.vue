<template>
  <el-menu theme="dark":default-active="activeIndex" class="el-menu-demo" mode="horizontal" @select="handleSelect">
    <el-submenu index="1">
      <template slot="title">Menu</template>
      <el-button type="success" index="2-1" @click.native="index">Home</el-button>
      <br></br>
      <el-button type="success" index="2-2" @click.native="newPost">New Post</el-button>
      <br></br>
      <el-button type="success" index="2-3" @click.native="logout">Logout</el-button>
    </el-submenu>
  </el-menu>
</template>

<script>
import router from './router'
import UsersApi from './api/users.js'

export default {
  data () {
    return {
      activeIndex: '1'
    }
  },
  methods: {
    handleSelect (key, keyPath) {
      console.log(key, keyPath)
    },
    index () {
      router.push({ name: 'Posts.index' })
    },
    newPost () {
      router.push({ name: 'Posts.new' })
    },
    logout () {
      UsersApi.logout()
      router.push({name: 'Users.sign_in'})
    }
  }
}
</script>

<style lang="css">
</style>
