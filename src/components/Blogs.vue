<template>
  <div>
    <div v-bind:key="blog.id" v-for="blog in blogs">
      <BlogItem v-bind:blog="blog" v-on:del-blog="$emit(`del-blog`, blog.id)" />
    </div>
  </div>
</template>

<script>
import BlogItem from "./BlogItem.vue";

export default {
  name: "Blogs",
  components: {
    BlogItem,
  },
  props: ["blogs"],
};
</script>

<style scoped></style>
