<template>
  <ConvencionNombre titulo="Convensión de Nombres"/>
</template>

<script>
import ConvencionNombre from './components/ConvencionNombre.vue'

export default {
  name: 'App',
  components: {
    ConvencionNombre
  }
}
</script>

<style>
body {
  background-color: #F5F5F5;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
