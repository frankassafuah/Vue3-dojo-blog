<template>
  <div class="post-list" v-for="post in posts" :key="post.id">
    <SinglePost :post="post" />
  </div>
</template>

<script>
import { onMounted, onUnmounted, onUpdated } from "@vue/runtime-core";
import SinglePost from "./SinglePost.vue";
export default {
  name: "PostList",
  components: { SinglePost },
  props: {
    posts: {
      type: Array,
      default: () => [],
    },
  },

  setup() {
    //lifecycle hooks
    onMounted(() => {
      console.log("mounted");
    });
    onUnmounted(() => {
      console.log("Unmounted");
    });
    onUpdated(() => {
      console.log("Updated");
    });
  },
};
</script>

<style></style>
