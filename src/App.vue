<template>
  <div id="app">
    <HelloWorld>
      <current-user v-slot="{ user }">
        {{ user.firstName }}
      </current-user>
    </HelloWorld>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import CurrentUser from './components/CurrentUser';

export default {
  name: 'app',

  components: {
    HelloWorld,
    CurrentUser
  }
}
</script>

<style lang="scss">
@import "./assets/sass/variables.scss";

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: $primary-text-color;
  margin-top: 60px;
}
</style>
