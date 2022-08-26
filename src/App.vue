<template>
<!-- <ManagedNavigation /> -->
<NavBar />
<!-- <Terminal /> -->
<router-view/>
</template>

<script setup>
import NavBar from './components/NavBar.vue';
// import Terminal from '@/components/Terminal.vue';
// import ManagedNavigation from './components/ManagedNavigation.vue';
</script>

<style lang="scss">
// @import "@/scss/light-colors.scss";
// @media (prefers-color-scheme: dark) {
//   @import "@/scss/dark-colors.scss";
// }
@import "@/scss/dark-colors.scss";

body {
  margin: 0;
  background-color: $primary-color;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #214c77;
}
</style>
