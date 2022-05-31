<template>
  <div>
    <b-form-group
      label-cols-lg="3"
      label="New Group"
      label-size="lg"
      label-class="font-weight-bold pt-0"
      class="mb-0"
      @submit.prevent="addPosts"
      method="post"
    >
      <b-form-group
        label="Title:"
        label-for="title"
        label-cols-sm="3"
        label-align-sm="right"
      >
        <b-form-input id="title" v-model="newPostData.title"></b-form-input>
      </b-form-group>
      <b-form-group
        label="Body:"
        label-for="body"
        label-cols-sm="3"
        label-align-sm="right"
      >
        <b-form-input id="body" v-model="newPostData.body"></b-form-input>
      </b-form-group>
      <b-button @click="addPosts">
        Create New Post
      </b-button>
    </b-form-group>
  </div>
</template>

<script>
import axios from "axios";

export default {
  components: {
  },
  data() {
    return {
      newPostData: {
        userId: 1,
        title:"",
        body:""
      },
      post:[],
    }
  },

  methods: {
    addPosts(){
      const newData = this.newPostData;
      const route = `https://jsonplaceholder.typicode.com/posts/`;
      axios.post(route, newData)
        .then((response) => console.log(response))
        .catch(error => console.log(error))
    },
  }
}
</script>


<style>

</style>