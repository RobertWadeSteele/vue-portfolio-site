<template>
<HeadShot />
<h1 id="name">Robert Steele $></h1>
</template>

<script setup>
import HeadShot from '@/components/HeadShot.vue';
</script>

<style lang="scss">
@import '@/scss/dark-colors.scss';

#home {
  padding-top: 10px;
}

#name {
  color: $primary-text-color;
}
</style>