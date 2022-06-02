<template>
  <div>
    <b-row>
      <b-col cols="3"></b-col>
      <b-col cols="6">
        <h6 class="detail-post-id d-flex justify-content-end text-muted">Blog post #{{ post.id }}</h6>
        <h1 class="detail-post-title">{{ post.title }}</h1>
        <h6 class="detail-post-id text-muted">Written by {{ post.userId }}</h6>
        <div class="comment-cards-i">
          <h3 class="detail-post-body mt-4 mr-0">{{ post.body }}{{ post.body }}{{ post.body }}{{ post.body }}{{ post.body }}</h3>
        </div>
      </b-col>
      <b-col cols="3"></b-col>
    </b-row>
    
    <b-row class="blog-comments">
      <b-col cols="3"></b-col>
      <b-col  cols="6">
        <h6 class="my-4 reponses-title"> Responses:</h6>
        <div class="comment-cards-i">
          <comment-card v-for="comment in comments" v-bind:key="comment.id"
          :id="comment.id"
          :name="comment.name"
          :email="comment.email"
          :body="comment.body"
          class="mb-4 "
          ></comment-card>
        </div>
      </b-col>
      <b-col cols="3"></b-col>
    </b-row>

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
      post:[],
      comments:[],
    }
  },
  head() {
    return {
      title: "TMG " + this.post.title,
      meta: [
        {
          hid:"TMG",
          name:"TMG",
          content:"The midnight gospel stories",
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
        "Content-type": "application/json; charset=UTF-8",
        },
      }
      try {
        const route = `https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`
        const response = await axios.get(route, configuration);
        this.post = response.data;
      } catch (error) {
        console.log(err);
      }
    },

    async fetchComments(){
      const configuration = {
        headers: {
        "Content-type": "application/json; charset=UTF-8",
        },
      }
      try {
        const route = `https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}/comments`
        const response = await axios.get(route, configuration);
        this.comments = response.data;
      } catch (error) {
        console.log(err);
      }
    }
  },
}
</script>

<style>
.detail-post-id{
  font-family: Oswald;
  font-size: 1rem;
}

.blog-comments{
  background-color: rgba(220, 220, 220, 0.507);
}
.detail-post-title{
  font-family: Roboto;
  font-weight: 500;
  font-style: italic;
  font-size: 2rem;
  font-weight: bold;
  text-shadow: 1px 1px #FFC107;
}

.detail-post-body{
  min-height:15rem;
  width:40rem;
  font-family: Roboto;
  font-size: 1rem;
}

.comment-cards-i{
  display: flex;
  flex-direction: column;
  align-items: center;
}

.reponses-title{
  font-family: Oswald;
  font-size: 1rem;
}
</style>