<template>
  <div>
    <div class="my-4">
      <h1 class="header-text my-0 ml-2">The Midnight <br/>Gospel</h1>
    </div>
    <div class="my-4">
      <hr class="header-hr"/>
    </div>
  </div>
</template>
<script>
  export default{
    name: 'BlogHeader',
  };
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Oswald:wght@700&family=Roboto:ital,wght@0,400;0,900;1,700&display=swap');

.header-text{
  font-family: Oswald;
  font-size: 120px;
  text-shadow: 2px 4px #FFC107;
}

.header-subtitle{
  font-family: Roboto;
  font-size: 20px;
}

.header-hr{
  margin-right: 5rem;
  height: 4px;
  color: #FFC107;
  background-color: #FFC107;
  border: none;
}
</style>