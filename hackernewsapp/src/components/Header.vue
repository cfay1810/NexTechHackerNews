<template>
  <div class="pure-menu pure-menu-horizontal">
    <div class="container">
        <router-link to="/"><h2>Hacker News Web App</h2></router-link>
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
    background-color: #c00808;
  }
  .pure-menu a {
    color: white;
  }
  h2 {
    text-align: center;
    color: white;
  }

</style>