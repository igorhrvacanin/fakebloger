<template>
  <div class="blog-item">
    <div class="blog-title-left">
      <div v-if="!editing" @dblclick="editBlog(blog)" class="blog-title-label">{{ blog.title }}</div>
      <input v-else class="blog-title-edit" type="text" v-model="blog.title" />

      <button @click="editBlog()">Edit me</button>

      <button @click="$emit('del-blog', blog.id)" class="del">x</button>
    </div>

    <div class="blog-body-left">
      <div v-if="!editing" class="blog-body-label">{{ blog.body }}</div>
      <input v-else class="blog-body-edit" type="text" v-model="blog.body" />
    </div>
  </div>
</template>

<script>
export default {
  name: "BlogItem",
  props: ["blog"],
  data() {
    return {
      editing: false,
    };
  },
  methods: {
    editBlog() {
      this.editing = !this.editing;
    },
  },
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
.blog-title-left,
.blog-body-left {
  display: flex;
  align-items: center;
}
.blog-title-label,
.blog-body-label {
  padding: 10px;
  border: 1px solid white;
  margin-left: 12px;
}
.blog-title-edit,
.blog-body-edit {
  font-size: 24px;
  color: #2c3e50;
  margin-left: 12px;
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
}
</style>
