<template>
  <div class="post">
    <h3>{{ post.title }}</h3>
    <p>{{ snippet }}</p>
  </div>
</template>

<script>
import { computed } from "@vue/runtime-core";
export default {
  props: {
    post: {
      type: Object,
      defualt: () => ({}),
    },
  },
  setup(props) {
    const snippet = computed(() => {
      return props.post.body.substring(0, 50) + "...";
    });

    return { snippet };
  },
};
</script>

<style></style>
