<template>
  <div class="page-layout">
    <prismic-rich-text :field="page.data.page_title" />

    <prismic-rich-text :field="page.data.body" />
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
  data() {
    return {
      page: null,
    };
  },
};
</script>

<style scoped>
.page-layout {
  padding: 20px;
}
</style>
