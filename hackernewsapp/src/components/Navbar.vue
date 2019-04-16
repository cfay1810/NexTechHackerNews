<template>
  <div class="pure-menu pure-menu-horizontal">
    <div class="container">
<router-link class="pure-menu-link" to="/news">News</router-link>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Navbar"
  };
</script>

<style scoped>
  .pure-menu {
    background-color: #404040;
  }
  .pure-menu a {
    color: white;
  }
</style>