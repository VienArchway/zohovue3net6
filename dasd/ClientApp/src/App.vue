<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <!-- <v-data-table
    :headers="headers"
    :items="desserts"
    :items-per-page="5"
    class="elevation-1"
  ></v-data-table> -->
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios'
import { reactive } from 'vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  setup() {
    const state = reactive({
      test: null,
    });
    // const getWeathers = async () => {
    //   weathers.value = await axios.get('api/weatherforecast')
    // }
    // try{
    //   state.test =  await fetch("https://api.npms.io/v2/search?q=vue")
    //   } catch (err) {
    //     console.error(err)
    // }

    return {
      state
    }
  },
  async mounted() {
    try {
      const data = await axios.get('api/weatherforecast')
      console.log({ data })
    } catch (error) {
      console.log(error.message)
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
</style>
