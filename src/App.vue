<!--
 * @file   App.vue: Entry point for the vue components
 * @author Lucas Roes.
 * Created: December 27, 2020.
 -->
<template>
  <div id="app">
    <div>
      <img width="300" height="117" alt="Bayfield Design logo" src="./assets/BD_logo.png">
      <hr>
    </div>
    <main>
      <RegForm/>
    </main>
  </div>
</template>

<script>
import RegForm from './components/RegForm.vue'

export default {
  name: 'App',
  components: {
    RegForm
  }
}
</script>

<style lang="scss">

$main-color: #225773;
$accent-color: #bf5543;
$bg-color: #eaeaea;

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: $main-color;
  margin-top: 30px;
}

img {
  height: 100%;
  aspect-ratio: attr(width) / attr(height);
}

hr {
  border: 1px solid $accent-color;
  margin-top: 30px;
  margin-bottom: 30px;
}
</style>
