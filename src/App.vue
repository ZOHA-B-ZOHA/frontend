<template>
  <div id="app">
    <Main v-if="isMainVisible" v-on:toggleMain="toggleMain" />
    <Pad v-else v-on:toggleMain="toggleMain"/>
  </div>
</template>

<script>
import Main from './components/Main.vue'
import Pad from './components/Pad.vue'

export default {
  name: 'App',
  components: {
    Main,
    Pad
  },
  data: function() { // 왜 함수여야 하는 거지?
    return {
      isMainVisible: true,
    }
  },
  methods: {
    toggleMain: function() {
      this.isMainVisible = !this.isMainVisible
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
