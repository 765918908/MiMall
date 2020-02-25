<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
import store from "./storage";
export default {
  name: "App",
  components: {},
  mounted() {
    // console.log(store.getStorage());
    window.store = store;
    console.log(store.getItem("user"));
  }
};
</script>

<style lang="scss">
@import "./assets/scss/reset.scss";
@import "./assets/scss/config.scss";
</style>
