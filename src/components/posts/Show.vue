<template>
  <div class="post">
    <br></br>
    <el-card class="box-card">
      <iccs340-post :post='post'></iccs340-post>
    </el-card>
    <br></br>
    <br></br>
    <div v-for="comment in comments">
      <el-card class="box-card">
        <iccs340-comment :comment='comment'></iccs340-comment>
      </el-card>
    </div>
    <iccs340-new-comment :post='post'></iccs340-new-comment>
  </div>
</template>

<script>
import PostsApi from '../../api/posts.js'
import CommentsApi from '../../api/comments.js'

export default {
  name: 'post',
  components: {
    Iccs340Post: require('./Post'),
    Iccs340Comment: require('../comments/Comment'),
    Iccs340NewComment: require('../comments/New')
  },
  data () {
    return {
      post: {},
      comments: [],
      error: null
    }
  },
  created () {
    // fetch the data when the view is created and the data is
    // already being observed
    this.fetchData()
  },
  watch: {
    // call again the method if the route changes
    '$route': 'fetchData'
  },
  methods: {
    fetchData () {
      PostsApi.getPost(this.$route.params.id, _post => {
        this.post = _post
        CommentsApi.getComments(_post.id, _comments => {
          this.comments = _comments
        })
      })
    }
  }
}
</script>

<style>
</style>
