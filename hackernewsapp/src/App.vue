<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/news">News</router-link>
    </div>
    <router-view/>
  </div>
</template>

<script>
  import Navbar from "@/components/Navbar";
  export default {
    name: "App",
    components: {
      Navbar
    }
  };
</script>

<style></style>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
