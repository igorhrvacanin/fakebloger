<template>
  <div class="blog-item">
    <div class="blog-title-left">
      <div v-if="!editing" class="blog-title-label">{{ blog.title }}</div>
      <input
        v-else
        class="blog-title-edit"
        type="text"
        v-model="blog.title"
        @keyup.enter="doneEdit()"
      />

      <button class="edit-me" @click="editBlog()">
        {{ button.text }}
      </button>

      <button @click="$emit('del-blog', blog.id)" class="del">x</button>
    </div>

    <div class="blog-body-left">
      <div v-if="!editing" class="blog-body-label">{{ blog.body }}</div>
      <textarea
        v-else
        class="blog-body-edit"
        type="text"
        v-model="blog.body"
        @keyup.enter="doneEdit()"
      />
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
      button: {
        text: "Edit Me",
      },
    };
  },

  methods: {
    editBlog() {
      this.editing = !this.editing;
      if (this.editing == true) {
        this.button.text = "Submit";
      } else {
        this.button.text = "Edit Me";
      }
    },

    doneEdit() {
      debugger; // eslint-disable-line no-debugger
      this.editing = false;
      this.button.text = "Edit Me";
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
.blog-title-label {
  font-size: 1.5rem;
  padding: 10px;
  border: 1px solid white;
  margin-left: 12px;
}
.blog-body-label {
  padding: 10px;
  border: 1px solid white;
  margin-left: 12px;
  font-size: 1.1rem;
}
.blog-title-edit,
.blog-body-edit {
  font-size: 15px;
  color: #2c3e50;
  margin-left: 12px;
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
}
.blog-body-edit {
  height: 100px;
}
.edit-me {
  background-color: #2c3e50;
  color: white;
  border: none;
  padding: 5px;
}
</style>
