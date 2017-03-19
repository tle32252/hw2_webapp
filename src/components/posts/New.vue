<template>
  <div class="new-post">
    <h1>Create New Post</h1>
    <label>Topic</label>
    <el-input placeholder="" v-model="post.name"></el-input>
    <br></br>
    <label>Content</label>
    <el-input type="textarea":rows="2" placeholder="" v-model="post.content"></el-input>
    <br></br>
    <el-button type="success" @click.native="createPost">Post</el-button>
  </div>
</template>

<script>
import PostsApi from '../../api/posts.js'
import router from '../../router'

export default {
  name: 'new-post',
  data () {
    return {
      post: {
        name: '',
        content: ''
      }
    }
  },
  methods: {
    createPost () {
      PostsApi.createPost(this.post,
        function (_post) {
          router.push({ name: 'Posts.index' })
        }
      )
    }
  }
}
</script>

<style>
</style>
