<template>
  <div class="display card" :class="alignImageClass">
    <div class="display__image">
      <prismic-image :field="display.display_image" />
    </div>

    <div class="display__content">
      <prismic-rich-text
        class="display__title"
        :field="display.display_title"
      />

      <prismic-rich-text :field="display.display_body" />

      <prismic-link :field="display.call_to_action" />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    display: {
      type: Object,
      required: true,
    },
  },
  computed: {
    alignImageClass() {
      return `display--image-${this.display.align_image}`;
    },
  },
};
</script>

<style scoped>
.card {
  box-shadow: 0 0 12px rgba(0, 0, 0, 0.4);
  padding: 20px;
  margin: 20px;
}

.display {
  display: flex;
  justify-content: space-between;
}

.display__image {
  flex-basis: 48%;
}

.display__image img {
  width: 100%;
}

.display__content {
  flex-basis: 48%;
}

.display--image-right {
  flex-direction: row-reverse;
}
</style>
