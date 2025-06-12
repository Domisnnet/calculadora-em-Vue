<template>
  <div id="myapp">
    <h1>Calculadora</h1>
    <MainCalculator />
    <AddButton />
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
@font-face {
  font-family: "RobotoMono";
  src: url(./fonts/RobotoMono-Thin.ttf) format("truetype");
}

* {
  font-family: "RobotoMono", monospace;
}

body {
  margin: 0;
}

#myapp {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  height: 100vh;
  color: #fff;
  background: linear-gradient(to right,rgb(83,105,118), rgb(41,46,73));
}
</style>