<template>
  <li>
    <div style="display: inline-block"
    :class="{'fev': post.fev}">
      {{ post.title }}
    </div> |
    <button @click="Click(post)">Delete Post</button> |
    <button @click="$emit('fev',post)">fev Post</button>
  </li>
</template>

<script>
export default {
  name: "SinglePost",
  props: ['post'],
  methods: {
    Click(post) {
      this.$emit('delete', post)

    }
  }
}
</script>

<style scoped>
.fev {
  color: green;
}
</style>