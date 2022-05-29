<template>
  <div>
    <b-jumbotron>
      <template #header>The Midnight Gospell</template>
      <template #lead>Blog</template>
    </b-jumbotron>
  </div>
</template>
<script>
  export default{
    name: 'BlogHeader',
    head(){
      return {
        title: "About the blog",
        meta: [
          {
            hid:"description", //unique identifier
            name:"description", //name
            content:"The midnight gospell stories" //
          }
        ]
      };
    }
  };
</script>
<style>

</style>