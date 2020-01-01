<template>
  <div id="app">
    <div class="logos">
      <img alt="Vue logo" src="./assets/vuelogo.png">
      <img alt="Typescript logo" src="./assets/tslogo.png">
      <img alt="Rhino logo" src="./assets/rhinologo.png">
    </div>
    <HelloWorld msg="Vue.js + TypeScript + rhino3dm.js"/>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import HelloWorld from './components/HelloWorld.vue';

export default Vue.extend({
  name: 'app',
  components: {
    HelloWorld
  }
});
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.logos > img {
  height: 200px;
  margin-right: 30px;
}
</style>
