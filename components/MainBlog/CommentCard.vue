<template>
  <b-card class="comment-card">
    <h6 class="user-name text-muted">{{ email }} says:</h6>
    <h3 class="comment-name my-3">{{ name }}</h3> 
    <b-card-text class="comment-body">
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
.comment-card{
  width:40rem;
}
.user-name{
  font-family: Roboto;
  font-size: .75rem;
}
.comment-name{
  font-family: Roboto;
  font-weight: 500;
  font-size: 1rem;
}
.comment-body{
  font-family: Roboto;
  font-size: .75rem;
}

</style>