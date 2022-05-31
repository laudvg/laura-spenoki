<template>
  <div>
    <add-post></add-post>
    <post-card v-for="post in posts" v-bind:key="post.id" 
    :id="post.id"
    :post="post.body"
    :title="post.title"
    :user="post.userId"
    ></post-card>
  </div>
</template>

<script>
import axios from "axios";
import PostCard from "../../components/MainBlog/PostCard.vue";
import AddPost from "../../components/MainBlog/AddPost.vue";

export default {
  components: {
    PostCard,
    AddPost,
  },
  data() {
    return {
      posts: [],
    }
  },
  head() {
    return {
      title: "TMG Posts",
      meta: [
        {
          hid:"description", //unique identifier
          name:"description", //name
          content:"The midnight gospell stories" //
        }
      ]
    };
  },
  created() {
    this.fetchPosts();
  },

  methods: {
    async fetchPosts(){
    const configuration = {
      headers: {
      'Content-type': 'application/json; charset=UTF-8',
      },
    }
    try {
      const route = `https://jsonplaceholder.typicode.com/posts/`
      const response = await axios.get(route, configuration);
      this.posts = response.data
    } catch (error) {
      console.log(err);
    }
    }
  }
}
</script>

<style>

</style>