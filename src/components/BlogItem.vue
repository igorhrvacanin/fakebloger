<template>
  <div class="blog-item">
    <p>
      {{ blog.title }}
      <button @click="$emit('del-blog', blog.id)" class="del">x</button>
    </p>
    <p>{{ blog.body }}</p>
  </div>
</template>

<script>
export default {
  name: "BlogItem",
  props: ["blog"],
  methods: {},
};
</script>

<style scoped>
.blog-item {
  background: white;
  padding: 10px;
  border-bottom: 1px solid #ccc;
}
.blog-item :first-child {
  font-size: 1.5rem;
}
.del {
  background: #555;
  color: white;
  padding: 1px 5px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>
