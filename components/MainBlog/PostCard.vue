<template>
  <nuxt-link :to="`posts/` + id" class="post-link w-25">
      <b-card class="post-card">
        <h3 class="post-title">{{ title }}</h3> 
        <b-card-text> by {{ user }} </b-card-text>
        <h6>{{ id }}</h6>
        <b-card-text class="post-post">
          {{ post }}
        </b-card-text>
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
  opacity: 75%;
  background-color: palegoldenrod;
}

.post-card{
  max-width: 30rem;
  height: 20rem;
  /* display: flex;
  flex-direction: column;
  align-content: space-between; */
}

.post-title{
  font-family: Roboto;
  font-weight: 500;
  font-style: italic;
  font-size: 2rem;
}

.post-card:hover + .post-title{
  text-shadow: 1px 1px yellow;
}

.post-user{
  font-family: Roboto;
  font-size: 20px;
}

.post-post{
  font-family: Roboto;
  font-size: 1rem;
  height: 4.5rem;
  width:25rem;
  white-space: normal;
  display: inline-block;
  overflow: hidden;
  /* text-overflow: ellipsis; */
}
</style>