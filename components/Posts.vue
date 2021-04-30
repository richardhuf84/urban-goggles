<template>
  <div class="posts">
    <h1>Posts</h1>
    <div v-for="(post, index) in posts" :key="index" class="post">
      <figure class="hero">
        <prismic-image :field="post.data.post_hero" />
        <figcaption>
          <prismic-rich-text :field="post.data.image_attribution" />
        </figcaption>
      </figure>

      <div class="post__content">
        <prismic-rich-text :field="post.data.post_title" />

        <prismic-rich-text :field="post.data.post_body" />
      </div>
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
  asyncData() {
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

.posts {
  text-align: left;
}

.hero {
  max-width: 50vw;
  margin: 0;
  flex-basis: 33%;
}

.post {
  display: flex;
  box-shadow: 0 0 12px rgba(0, 0, 0, 0.4);
  margin: 20px;
  /* padding: 20px; */
}

.post__content {
  flex-basis: 66%;
  padding: 20px;
}
</style>
