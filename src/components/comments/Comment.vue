<template>
  <div class="comment">
      <div class="md-list-text-container">
        <span>{{ comment.user.email }}</span>
        <br></br>
        <span>{{ comment.content }}</span>
      </div>
    </md-list-item>
  </div>
</template>

<script>

export default {
  name: 'comment',
  props: {
    comment: {
      type: Object,
      required: false,
      default: {}
    }
  }
}
</script>

<style scoped>
  .md-list-item {
    padding-left: 40px;
  }
</style>
