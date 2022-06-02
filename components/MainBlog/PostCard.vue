<template>
  <nuxt-link :to="`posts/` + id" class="post-link w-25">
      <b-card class="post-card">
        <h6 class="d-flex justify-content-end text-muted">{{ id }}</h6>
        <h3 class="post-title">{{ title }}</h3> 
        <b-card-text class="post-post">
          {{ post }}
        </b-card-text>
        <div>
          <div class="user-ban">
            <h6 class="user-avatar">{{ user }}</h6>
            <h6 class=" ml-1 user-info"> Written by {{ user }} </h6>
          </div>
        </div>
      </b-card>
  </nuxt-link>
</template>

<script>
export default {
  name: "PostCard",
  props: [
    "post",
    "id",
    "title",
    "user",
  ],
}
</script>

<style>
.post-link {
  text-decoration: none;
  color: inherit;
}

.post-link:hover {
  text-decoration: none;
  color: inherit;
}

.post-card{
  max-width: 30rem;
  height: 20rem;
}

.post-card:hover{
  opacity: 0.9;
  background-color: rgb(220, 220, 220);
}

.post-title{
  font-family: Roboto;
  font-weight: 500;
  font-style: italic;
  font-size: 1.5rem;
}

.post-card:hover .post-title{
  font-weight: bold;
  text-shadow: 1px 1px #FFC107;
}

.post-user{
  font-family: Roboto;
  font-size: 20px;
}

.post-post{
  font-family: Roboto;
  font-size: .8rem;
  height: 4.5rem;
  max-width:20rem;
  white-space: normal;
  display: inline-block;
  overflow: hidden;
  /* text-overflow: ellipsis; */
}

.user-ban{
  display: flex;
  justify-content: flex-start;
  flex-direction: row;
  align-items: center;
}

.user-ban:last-of-type {
  position: absolute;
  top: 17rem;
}

.user-avatar {
  margin-right: 1;
  border-radius: 50%;
  height: 40px;
  width: 40px;
  padding: 3px;

  background-color: #FFC107;
  color:white;
  text-align: center;
  font-size: 1.5rem;
}

.user-info{
 font-size: .8rem;
}
</style>