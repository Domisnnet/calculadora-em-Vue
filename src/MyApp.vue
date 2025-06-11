<template>
  <div id="myapp">
    <h1>Olá Vue!!</h1>
    <MainCalculator />
  </div>
</template>

<script>
import MainCalculator from './components/main/MainCalculator.vue'
export default {
  components: { MainCalculator },
  name: 'MyApp'
}
</script>

<style>
#myapp {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>