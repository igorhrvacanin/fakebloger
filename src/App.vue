<template>
  <div id="app">
    <Header />
    <AddBlog v-on:add-blog="addBlog" />
    <form class="search">
      <input
        type="text"
        v-model="search"
        name="search"
        placeholder="Search Blogs"
      />
    </form>

    <Blogs v-bind:blogs="filteredBlogs" v-on:del-blog="deleteBlog" />
  </div>
</template>

<script>
import Blogs from "./components/Blogs";
import Header from "./components/layout/Header";
import AddBlog from "./components/AddBlog";
import axios from "axios";

export default {
  name: "App",
  components: {
    Blogs,
    Header,
    AddBlog,
  },
  data() {
    return {
      blogs: [],
      search: "",
    };
  },
  methods: {
    deleteBlog(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/posts/${id}`)
        .then((res) => {
          this.blogs = this.blogs.filter((blog) => blog.id !== id);
          return res;
        })

        .catch((err) => console.log(err));
    },

    addBlog(newBlog) {
      const { title, body } = newBlog;

      axios
        .post("https://jsonplaceholder.typicode.com/posts", { title, body })
        .then((res) => (this.blogs = [...this.blogs, res.data]))
        .catch((err) => console.log(err));
    },
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/posts?_limit=5")
      .then((res) => (this.blogs = res.data))
      .catch((err) => console.log(err));
  },
  computed: {
    filteredBlogs: function fil() {
      return this.blogs.filter((blog) => {
        return blog.title.match(this.search);
      });
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
form .search {
  display: flex;
  flex-direction: column;
  padding: 10px;
}
input[name="search"] {
  width: 20%;
  margin-top: 5px;
  padding: 10px;
  margin-left: 10px;
}
</style>
