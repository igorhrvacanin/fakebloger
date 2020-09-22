<template>
  <div>
    <form @submit="addBlog">
      <input
        type="text"
        name="title"
        v-model="title"
        placeholder="Add Title"
        required
      />
      <input
        type="text"
        name="body"
        v-model="body"
        placeholder="Add Text to Blog"
        required
      />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script>
export default {
  name: "AddBlog",
  data() {
    return {
      title: "",
      body: "",
    };
  },
  methods: {
    addBlog(e) {
      e.preventDefault();
      const newBlog = {
        title: this.title,
        body: this.body,
      };
      this.$emit("add-blog", newBlog);
      this.title = "";
      this.body = "";
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  padding: 10px;
}
input[type="text"] {
  width: 100%;
  margin-top: 5px;
  padding: 10px;
}
input[type="submit"] {
  width: 20%;
  margin-top: 5px;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: white;
  padding: 7px 20px;
  cursor: pointer;
}
</style>
