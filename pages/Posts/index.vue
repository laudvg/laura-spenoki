<template>
  <div>
    posts
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      posts: [],
    }
  },
  head() {
    return {
      title: "About the blog",
      meta: [
        {
          hid:"description", //unique identifier
          name:"description", //name
          content:"The midnight gospell stories" //
        }
      ]
    };
  },
  async created() {
    const configuration = {
      headers: {
      'Content-type': 'application/json; charset=UTF-8',
      },
    }
    const posts = `https://jsonplaceholder.typicode.com/posts/`
    try {
      const response = await axios.get(posts, configuration);
      this.posts = response.data
      // console.log(response.data);
    } catch (error) {
      console.log(err);
    }
  },
}
</script>

<style>

</style>