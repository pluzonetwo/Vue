<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <Calc></Calc>
<!--    <Keyboard></Keyboard>-->
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import Calc from './components/Calc.vue';
// import Keyboard from './components/Keyboard.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
    Calc,
    // Keyboard,
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
