<template>
  <page-home></page-home>
</template>

<script setup>
  import pageHome from './view/page-home.vue';
</script>

<style lang='less'>
@import './style/reset.less';
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

html, body {
  min-width: 1200px;
}
</style>
