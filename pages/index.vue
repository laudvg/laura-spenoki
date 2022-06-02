<template>
  <div>
    <b-row>
      <b-col cols="1"></b-col>
      <b-col cols="10" align="right">
        <b-button @click="addPost()" variant="outline-warning" class="mb-4 ">Add New Post</b-button>
      </b-col>
    </b-row>
    <b-row>
      <b-col cols="1"></b-col>
      <b-col cols="10">
        <div v-if="add === true" class="d-flex flex-wrap justify-content-center">
          <form @submit.prevent="submitPost">
            <b-form-input class="mb-2 input" type="text" v-model="newPostData.title" placeholder="Add a Title" required></b-form-input>
            <b-form-textarea class="mb-2 textarea" type="text" cols="30" rows="10"  v-model="newPostData.body" placeholder="Write your post here" required></b-form-textarea>
            <b-button type="submitPost"> Post </b-button>
          </form>
        </div>
      </b-col>
    </b-row> 

    <b-row class="mt-4 post-cards">
      <b-col cols="1"></b-col>
      <b-col cols="10" class="d-flex flex-wrap justify-content-center">
        <post-card v-for="post in merged" v-bind:key="post.id" 
        :id="post.id"
        :post="post.body"
        :title="post.title"
        :user="post.userId"
        class="post-card mx-4 my-4"
        ></post-card>
      </b-col>
    </b-row>
  </div>
</template>

<script>
import axios from "axios";
import PostCard from "../components/MainBlog/PostCard.vue"

export default {
  name: 'IndexPage',
  components: {
    PostCard,
  },
  data() {
    return {
      posts: {},
      newPostData: {
        userId: 1,
        title:"",
        body:"",
        id:""
      },
      restData: {
        userId: 1,
        title:"",
        body:"",
        id:""
      },
      newPost:{},
      add: false,
      merged:{},
    }
  },
  head() {
    return {
      title: "TMG Posts",
      meta: [
        {
          hid:"TMG",
          name:"TMG Posts",
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
        this.posts = response.data.sort((b, a) => a.id - b.id);
        console.log(this.posts);
      } catch (error) {
        console.log(error);
      }
    },

    async submitPost(){
      const newData = this.newPostData;
      const route = `https://jsonplaceholder.typicode.com/posts/`;
      try{
        const response = await axios.post(route, newData);
        this.newPost = response.data;
        this.addToPosts();
      } catch (error) {
        console.log(error);
      }
    },

    addToPosts(){
      this.merged = [ ...this.posts, this.newPost];
      this.newPostData = this.restData;
      this.add = false; 
    },

    addPost(){
      this.add = !this.add;
    }
  },

  watch:{
    posts:"addToPosts",
  },
  
}
</script>

<style>

  .post-card{
    max-width: 30rem;
    height: 20rem;
  }

  .input{
    min-width: 50rem;
  }

  .textarea{
    min-width: 50rem;
  }

</style>
