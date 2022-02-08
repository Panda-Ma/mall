<template>
  <div id="nav">
    <router-view/>
    <main-tab-bar></main-tab-bar>
  </div>
</template>

<script>
import MainTabBar from "components/content/MainTabBar";

export default {
  name: 'App',
  components: {MainTabBar},
  data() {
    return {}
  }
}
</script>

<style>
@import "assets/css/base.css";
</style>
