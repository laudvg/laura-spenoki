<template>
  <b-card>
    <h3>{{ name }}</h3> 
    <h6>{{ email }}</h6>
    <b-card-text>
      {{ body }}
    </b-card-text>
  </b-card>
</template>

<script>
export default {
  name: "CommentCard",
  props: [
    "name",
    "email",
    "body",
  ],
}
</script>

<style>

</style>