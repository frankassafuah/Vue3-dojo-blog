<template>
  <div class="post-list" v-for="post in posts" :key="post.id">
    <SinglePost :post="post" />
  </div>
</template>

<script>
import SinglePost from "./SinglePost.vue";
export default {
  props: {
    posts: {
      type: Array,
      default: () => [],
    },
  },
  components: { SinglePost },
};
</script>

<style></style>
