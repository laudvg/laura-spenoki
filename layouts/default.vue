<template>
  <div>
    <BlogHeader/>
    <Nuxt />
  </div>
</template>

<script>
import BlogHeader from "../components/MainBlog/BlogHeader.vue"
export default {
layout: "blog",
components:{
  BlogHeader,
}
}
</script>

<style>
* template{
  overflow-x: hidden;
}
</style>
