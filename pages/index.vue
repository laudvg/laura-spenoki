<template>
  <div>
    <add-post></add-post>
    <b-row
    class="mt-4 post-cards"
    >
      <post-card v-for="post in posts" v-bind:key="post.id" 
      :id="post.id"
      :post="post.body"
      :title="post.title"
      :user="post.userId"
      class="post-card mx-4 my-4"
      ></post-card>

    </b-row>
  </div>
</template>

<script>
import axios from "axios";
import PostCard from "../components/MainBlog/PostCard.vue"
import AddPost from "../components/MainBlog/AddPost.vue";

export default {
  name: 'IndexPage',
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
          content:"The midnight gospel stories" //
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
.post-cards{
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  align-items: flex-start;
}

.post-card{
  max-width: 30rem;
  height: 20rem;
}
</style>
