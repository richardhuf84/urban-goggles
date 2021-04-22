<template>
  <div>
    <h1>Posts</h1>
    <div v-for="(post, index) in posts" :key="index">
      <h3>
        <prismic-rich-text :field="post.data.post_title" />
      </h3>

      <figure class="hero">
        <prismic-image :field="post.data.post_hero" />
      </figure>
      <figcaption>
        <prismic-rich-text :field="post.data.image_attribution" />
      </figcaption>

      <prismic-rich-text :field="post.data.post_body" />
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
  created() {
    this.getContent();
  },
  methods: {
    async getContent() {
      const posts = await this.$prismic.api.query('');
      this.posts = posts.results.filter((post) => post.type === 'post');
    },
  },
};
</script>

<style scoped>
img {
  max-width: 100%;
  height: auto;
}

.hero {
  max-width: 50vw;
  margin: 0 auto;
}
</style>
