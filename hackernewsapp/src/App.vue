<template>
  <div id="app">
    <navbar></navbar>
    <router-view />
  </div>
</template>

<script>
  import Navbar from "@/components/Header";
  export default {
    name: "App",
    components: {
      Navbar
    }
  };
</script>

<style scoped>
</style>

