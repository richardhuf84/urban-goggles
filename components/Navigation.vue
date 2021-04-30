<template>
  <ul>
    <li><nuxt-link to="/">Home</nuxt-link></li>
    <li><nuxt-link to="posts">Posts</nuxt-link></li>
    <li>
      Pages
      <ul>
        <li><nuxt-link to="/about">About</nuxt-link></li>
        <li>
          <nuxt-link to="/the-jamstack-is-lots-of-fun">JAMStack</nuxt-link>
        </li>
      </ul>
    </li>
  </ul>
</template>

<script>
export default {
  mounted() {
    // console.log(this);
  },
};
</script>

<style scoped></style>
