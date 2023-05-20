<template>
  <div id="app">
    <v-app>
      <v-main>
        <h1> {{ localWording.fr.title }} </h1>
        <CountDown :title="localWording.fr.countDownTitle" />
        <PreOrder :title="localWording.fr.preOrder.title" />
      </v-main>
    </v-app>
  </div>
</template>

<script>
import CountDown from './components/CountDown.vue'
import PreOrder from './components/PreOrder.vue'
import data  from './utils/data.json'

export default {
  name: 'App',
  components: { CountDown, PreOrder },
  data() {
    return {
      localWording: data
    }
  }
}
</script>

<style>
#app {
  font-family: "Roboto";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 30px 10px 60px;
}


h1 {
  color: #FAF5DB;
  background-color: #CC2536;
  box-shadow: 0 5px 5px 0 rgba(0,0,0,.25);
  font-size: 1.5em;
  margin: 15px 0;
  padding: 20px;
}
</style>
