<template>
  <div>
    <b-row>
      <b-col cols="10"></b-col>
      <b-modal 
      id="modal-1" 
      title="Add a new Post"
      @ok="addPosts" 
      size="xl" 
      class="post-modal mt-4">
        <b-form-group
          label-cols-lg="3"
          label="New Post"
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
            <b-form-textarea id="body" class="post-body" v-model="newPostData.body"></b-form-textarea>
          </b-form-group>
        </b-form-group>
      </b-modal>
      <b-col cols="2" align="right">
        <b-button variant="light" class="mr-4" v-b-modal.modal-1>
          Add New Post
        </b-button>
      </b-col>
    </b-row>
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

.post-body{
  min-height: 30rem;
}

.modal-content{
  margin-top: 6rem;
}
</style>