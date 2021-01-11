<template>
  <div id="app">
    <!--Add a simple header and footer to page-->
    <div class="header-container">
      <div class="header">
        <img alt="Bayfield Design logo" src="./assets/logo.png">
      </div>
    </div>
    <Registration msg="Registration"/>
    <div class="footer">
    </div>
  </div>
</template>

<script>
import Registration from './components/Registration.vue'

export default {
  name: 'App',
  components: {
    Registration
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  //margin-top: 60px;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.header {
  //width: 900px;
  //height: 300px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.header-container {
  //color: #5995DA;
  background-color: #D6E9FE;
  display: flex;
  justify-content: center;
}
.footer{
  height: 100px;
  background-color: #D6E9FE;
  display: flex;
  justify-content: center;
}

.error-message{
  color: red;
  font-size: smaller;
}
</style>
