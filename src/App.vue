<template>
  <img alt="Vue logo" src="./assets/logo.webp" />
  <deck-dock />
  <footer>Desenvolvido por <a href="http://jorgemadson.github.io">Jorge Madson</a></footer>
</template>

<script>
import DeckDock from "./components/DeckDock.vue";

export default {
  name: "App",
  components: {
    DeckDock,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
footer{
  position: absolute;
  bottom: 10px;
  right: 10px;
}
</style>
