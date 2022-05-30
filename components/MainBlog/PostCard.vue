<template>
  <nuxt-link :to="`posts/` + id">
      <b-card>
        <h3>{{ title }}</h3> 
        <h6>{{ id }}</h6>
        <b-card-text>
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

</style>