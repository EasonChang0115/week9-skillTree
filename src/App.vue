<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style lang="scss">
#app {
  background-image: linear-gradient(
    to right,
    #2d1b59 0%,
    #0e0024 50%,
    #2d1b59 100%
  );
  width: 100%;
  min-width: 1024px;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
