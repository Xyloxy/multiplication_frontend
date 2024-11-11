<template>
  <MultiplyComponent />
</template>

<script>
import MultiplyComponent from './components/MultiplyComponent.vue'

export default {
  name: 'App',
  components: {
    MultiplyComponent,
  }
}
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
</style>
