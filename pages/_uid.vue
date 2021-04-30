<template>
  <div class="page-layout">
    <prismic-rich-text :field="page.data.page_title" />

    <prismic-rich-text :field="page.data.body" />

    <Display
      v-for="(display, index) in page.data.display"
      :key="index"
      :display="display"
    />
  </div>
</template>

<script>
export default {
  async asyncData({ $prismic, params, error }) {
    const page = await $prismic.api.getByUID('page', params.uid);

    if (page) {
      return { page };
    } else {
      error({ statusCode: 404, message: 'Page not found' });
    }
  },
};
</script>

<style scoped>
.page-layout {
  padding: 20px;
}
</style>
