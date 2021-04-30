<template>
  <div class="posts">
    <h1>Posts</h1>
    <div v-for="(post, index) in posts" :key="index" class="post">
      <figure class="hero">
        <prismic-image :field="post.data.post_hero" />
        <figcaption class="hero__caption">
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
.posts {
  max-width: 65vw;
  text-align: left;
}

.hero {
  margin: 0;
  flex-basis: 33%;
}

.hero__caption {
  padding: 0 20px;
}

.post {
  display: flex;
  box-shadow: 0 0 12px rgba(0, 0, 0, 0.4);
  flex-direction: column;
  margin: 20px;
}

.post__content {
  flex-basis: 66%;
  padding: 20px;
}
</style>
