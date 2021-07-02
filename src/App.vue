<template>
  <div id="app">
    <plate plate='MJL9746'/>
  </div>
</template>

<script>
import Plate from './components/Plate.vue'

export default {
  name: 'App',
  components: {
    Plate
  }
}
</script>
<style scoped>
  #app {
    padding: 10px
  }
</style>