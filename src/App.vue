<template>
<ManagedNavigation />
<router-view/>
</template>

<script setup>
import ManagedNavigation from './components/ManagedNavigation.vue';
</script>

<style lang="scss">
@import "@/scss/dark-colors.scss";

body {
  margin: 0;
  background-color: $primary-color;
}

*

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #214c77;
}
</style>
