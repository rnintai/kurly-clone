<template>
  <div class="App">
    <main-nav></main-nav>
    <router-view></router-view>
  </div>
</template>

<script>
  import MainNav from "./components/Common/MainNav.vue";

  export default {
    components: { MainNav },
    name: "App"
  };
</script>

<style lang="scss">
  @import "./assets/css/reset.css";
  @import "./assets/css/main.scss";
</style>
