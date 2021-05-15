<template>
  <div class="post">
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
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
.hero {
  margin: 0;
  /* flex-basis: 33%; */
  max-height: 14vw;
  overflow: hidden;
}

.hero img {
  max-width: 100%;
  object-fit: cover;
}

.hero__caption {
  padding: 0 20px;
}

.post {
  display: flex;
  box-shadow: 0 0 12px rgba(0, 0, 0, 0.4);
  flex-direction: column;
  margin: 20px;
  padding-bottom: 1rem;
}

h1 {
  font-size: 1.5rem;
}

.post__content {
  flex-basis: 66%;
  padding: 20px;
  max-height: 30vw;
  overflow: hidden;
  position: relative;
}

.post__content::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 3rem;
  background: linear-gradient(
    to bottom,
    rgba(255, 255, 255, 0),
    rgba(255, 255, 255, 1)
  );
}
</style>
