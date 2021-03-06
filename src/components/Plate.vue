<template>
  <div class='plate' :class="[{'mercosul': mercosul, 'cinza': !mercosul, 'moto': moto}, `plate-${type}`]">
    <span class='header header-mercosul' v-if='mercosul'>
      <span class='cidade'>BRASIL</span>
      <bandeira class='bandeira'/>
    </span>
    <span v-else class='header header-cinza'>
      <span class='detalhe-circulo'></span>
      <span class='cidade'>{{uf}} - {{municipio}}</span>
      <span class='detalhe-circulo'></span>
    </span>
    <div class='plate-container' ref='plateContainer'>
      <span>{{letters}}</span>
      <span class='espacamento' v-if='!mercosul && !wrap'>-</span>
      <span class='numbers'>{{numbers}}</span>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
import Bandeira from './Bandeira'

export default {
  components: {
    Bandeira
  },
  setup() {
    const plateContainer = ref(null)
    return { plateContainer }
  },
  props: {
    plate: String,
    type: {
      type: String,
      default: 'particular'
    },
    uf: {
      type: String,
      default: 'UF'
    },
    municipio: {
      type: String,
      default: 'municipio'
    },
    moto: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    letters() {
      return this.plate.slice(0,3)
    },
    numbers() {
      return this.plate.slice(3,8)
    },
    mercosul () {
      return isNaN(parseInt(this.plate.slice(4,5)))
    },
    wrap () {
      if(!this.plateContainer) {
        return;
      }
      const tamanhoFilhos = [...this.plateContainer.children].map(e => e.offsetWidth).reduce((a,b)=> a+b,0)
      const tamanhoPai = this.plateContainer.offsetWidth
      return tamanhoPai < tamanhoFilhos
    }
  }
}
</script>
<style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Unica+One&display=swap');
  @import url('https://fonts.googleapis.com/css2?family=Russo+One&display=swap');
  @import url('https://fonts.googleapis.com/css2?family=Cute+Font&family=Russo+One&display=swap');

  .plate, .plate * {
    box-sizing: border-box;
  }

  .plate {
    width: 100%;
    border-width: 10em;
    border-style: solid;
    border-radius: 7em;
    text-align:center;
  }

  .plate.moto {
    width: fit-content;
  }

  .plate.moto .espacamento {
    display: none;
  }

  .plate.moto .numbers {
    display: block;
  }

  .mercosul.plate-particular {
    border-color: #101c36;
    color: #101c36;
  }

  .mercosul.plate-comercial {
    border-color: #e1422e;
    color: #e1422e;
  }

  .mercosul.plate-especial {
    border-color: #519d3c;
    color:#519d3c;
  }

  .mercosul.plate-oficial {
    border-color: #2d52a0;
    color: #2d52a0;
  }

  .mercosul.plate-colecionador {
    border-color:#818181;
    color:#818181;
  }

  .mercosul.plate-diplomatico {
    border-color: #d09a36;
    color:#d09a36;
  }

  .plate.cinza {
    font-weight:bolder;
  }

  .cinza.plate-particular {
    border-color: #a5a5a5;
    color: #101c36;
    background: #c2c2c2;
  }

  .plate-particular .detalhe-circulo {
    background:  #a5a5a5;
  }

  .cinza.plate-comercial {
    border-color:#b23222;
    color:white;
    background:#e1422e;
  }

  .plate-comercial .detalhe-circulo {
    background:#b23222;
  }

  .cinza.plate-especial {
    border-color:#3f7c30;
    color:white;
    background:#519d3c;
  }

  .plate-especial .detalhe-circulo {
    background:#3f7c30;
  }

  .cinza.plate-oficial {
    border-color:#244180;
    background:#2d52a0;
    color:white;
  }

  .plate-oficial .detalhe-circulo {
    background:#244180;
  }

  .cinza.plate-colecionador {
    border-color:#000000;
    background:#1b1b1b;
    color:#c2c2c2;
  }

  .plate-colecionador .detalhe-circulo {
    background:#000000;
  }

  .cinza.plate-diplomatico {
    border-color:#c2c2c2;
    color:#b23222;
  }

  .plate-diplomatico .detalhe-circulo {
    background:#c2c2c2;
  }

  .plate-container {
    padding:0.4em;
    letter-spacing: 0.2em;
    font-size: 90em;
  }

  .mercosul .plate-container {
    font-family: 'Cute Font', cursive;
    font-weight:bold;
    padding: 0.1em;
  }

  .moto.mercosul .plate-container {
    padding: 0 0.4em;
    line-height: 1em;
  }

  .cinza .plate-container {
    font-size: 60em;
    font-family: 'Russo One', sans-serif;
  }

  .plate-container > span {
    display: inline-block;
  }

  .header {
    height:40em;
    margin: 0;
    width:100%;
    position:relative;

    display:flex;
    align-items: center;
    justify-content:center;
  }

  .header-cinza {
    display:flex;
    justify-content: space-evenly;
  }

  .detalhe-circulo {
    display:inline-block;
    width:40em;
    height:10em;
    border-radius: 3em;
  }

  .moto .detalhe-circulo {
    width: 10em;
    border-radius: 100%;
  }

  .header-mercosul {
    background: #1e4ab3;
    color: white;
  }

  .bandeira {
    position: absolute;
    top:5em;
    right:5em;
  }

  .moto .bandeira {
    font-size: 0.8em;
    top: 10em;
  }

  .cidade {
    text-transform:uppercase;
    font-size:20em;
    font-family: 'Unica One', cursive;
    letter-spacing: 0.4em
  }

  .moto .cidade {
    letter-spacing: 0.1em
  }
</style>
