<template>
  <div class="posts">
    <div v-for="post in posts">
      <router-link :to="{ name: 'Posts.show', params: {id: post.id } }">
        <el-card class="box-card">
          <iccs340-post :post='post'></iccs340-post>
        </el-card>
      </router-link>
    </div>
  </div>
</template>

<script>
import PostsApi from '../../api/posts.js'

export default {
  name: 'posts',
  components: {
    Iccs340Post: require('./Post')
  },
  data () {
    return {
      posts: null,
      error: null
    }
  },
  beforeRouteEnter (to, from, _next) {
    PostsApi.getPosts(_posts => {
      _next(vm => {
        vm.posts = _posts
      })
    })
  },
  watch: {
    $route () {
      PostsApi.getPosts(_posts => {
        this.posts = _posts
      })
    }
  }
}
</script>

<style>
.box-card {
   font-size: 20px;
   font-family: Times New Roman;
 }
</style>
