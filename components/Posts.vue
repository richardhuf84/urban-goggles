<template>
  <div class="posts">
    <h1>Posts</h1>
    <div class="grid-layout">
      <Post v-for="(post, index) in posts" :key="index" :post="post" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: null,
    };
  },
  async fetch() {
    const posts = await this.$prismic.api.query('');
    this.posts = posts.results.filter((post) => post.type === 'post');
  },
  created() {
    this.$fetch();
  },
};
</script>

<style scoped>
.grid-layout {
  display: grid;
  grid-template-rows: auto;
  grid-template-columns: 1fr 1fr 1fr;
}
</style>
