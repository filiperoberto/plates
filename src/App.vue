<template>
  <div id="app">
    <plate v-for='placa in placas' :plate='placa.placa' :type='placa.tipo' class='placa'/>
  </div>
</template>

<script>
import Plate from './components/Plate.vue'

export default {
  name: 'App',
  components: {
    Plate
  },
  data() {
    return {
      placas: [
        { placa : 'MJL9746', tipo: 'particular'},
        { placa : 'MJL9746', tipo: 'comercial'},
        { placa : 'MJL9746', tipo: 'especial'},
        { placa : 'MJL9746', tipo: 'oficial'},
        { placa : 'MJL9746', tipo: 'colecionador'},
        { placa : 'MJL9746', tipo: 'diplomatico'},
        { placa : 'MJL9H46', tipo: 'particular'},
        { placa : 'MJL9H46', tipo: 'comercial'},
        { placa : 'MJL9H46', tipo: 'especial'},
        { placa : 'MJL9H46', tipo: 'oficial'},
        { placa : 'MJL9H46', tipo: 'colecionador'},
        { placa : 'MJL9H46', tipo: 'diplomatico'}
      ]
    }
  }
}
</script>
<style scoped>
  #app {
    padding: 10px
  }
  .placa {
    margin-bottom: 10px;
    font-size: 0.7px;
  }

</style>