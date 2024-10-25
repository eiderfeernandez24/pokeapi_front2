<template>
  <div id="app">
    <PokemonList />
  </div>
</template>

<script>
import PokemonList from './components/PokemonList.vue';

export default {
  components: {
    PokemonList,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  /* background-color: blue; */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
