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
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  font-size: 1.8em;;
  margin: 25px 0;
}
</style>
