<template>
  <div>
    <h1>{{ post.title }}</h1>
    <h3> {{ post.body }}</h3>
    <h3> {{ post.id }}</h3>
    
    <div>
      <comment-card v-for="comment in comments" v-bind:key="comment.id"
      :id="comment.id"
      :name="comment.name"
      :email="comment.email"
      :body="comment.body"
      ></comment-card>
    </div>
  </div>
  
</template>

<script>
import axios from "axios";
import CommentCard from "../../../components/MainBlog/CommentCard.vue";

export default {
  components: {
    CommentCard,
  },
  data(){
    return {
      post:{},
      comments:[],
    }
  },
  head() {
    return {
      title: "TMG " + this.post.title,
      meta: [
        {
          hid:"description", //unique identifier
          name:"description", //name
          content:"The midnight gospel stories", //
        }
      ]
    };
  },
  created() {
    this.fetchPost();
    this.fetchComments();
  },

  methods:{
    async fetchPost(){
      const configuration = {
        headers: {
        'Content-type': 'application/json; charset=UTF-8',
        },
      }
      try {
        const route = `https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`
        const response = await axios.get(route, configuration);
        this.post = response.data;
        console.log(response.data);
      } catch (error) {
        console.log(err);
      }
    },

    async fetchComments(){
      const configuration = {
        headers: {
        'Content-type': 'application/json; charset=UTF-8',
        },
      }
      try {
        const route = `https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}/comments`
        const response = await axios.get(route, configuration);
        this.comments = response.data;
        console.log(this.comments, "2");
      } catch (error) {
        console.log(err);
      }
    }
  },
}
</script>

<style>

</style>