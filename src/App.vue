<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
  export default {
    name: 'App',
    mounted() {

    }
  }
</script>

<style>
#app {
  padding: 0;
  margin: 0;
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  bottom: 0;
  right: 0;
}
</style>
